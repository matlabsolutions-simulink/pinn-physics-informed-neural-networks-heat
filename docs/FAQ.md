# Pinn Physics Informed Neural Networks Heat — Engineering FAQ & Troubleshooting

> Verified solutions to real student and researcher laboratory inquiries.

### Q: How to compute automatic differentiation gradients with dlgradient for PDE residual loss in MATLAB PINNs?

**Verified Technical Solution:**

In Physics-Informed Neural Networks (PINNs) in MATLAB, the loss function evaluates both data loss and the underlying differential equation residual using automatic differentiation (`dlgradient`):

1. **Transient 1D Heat Equation:**
   $$\frac{\partial u}{\partial t} - \alpha \frac{\partial^2 u}{\partial x^2} = 0$$
   where $u(x, t)$ is temperature and $\alpha$ is thermal diffusivity.

2. **Gradient Evaluation Function:**
   Define the loss evaluation inside a custom function supporting `dlarray`:
   ```matlab
   function [loss, gradients] = modelLoss(parameters, X_colloc, T_colloc, alpha)
       % Forward pass
       U = model(parameters, X_colloc, T_colloc);
       
       % First derivatives via automatic differentiation
       u_t = dlgradient(sum(U, 'all'), T_colloc, 'EnableHigherDerivatives', true);
       u_x = dlgradient(sum(U, 'all'), X_colloc, 'EnableHigherDerivatives', true);
       
       % Second spatial derivative
       u_xx = dlgradient(sum(u_x, 'all'), X_colloc);
       
       % Physics residual
       f_pde = u_t - alpha * u_xx;
       loss_pde = mean(f_pde.^2, 'all');
       
       loss = loss_pde;
       gradients = dlgradient(loss, parameters);
   end
   ```

3. **Optimization Setup:**
   Train the network using the `adamupdate` solver for the first 2,000 epochs, then fine-tune using L-BFGS to drive PDE residuals below $10^{-5}$.

Explore MATLAB scientific deep learning and PINN consulting at https://www.matlabsolutions.com/projects/deep-learning-matlab.php.

---

