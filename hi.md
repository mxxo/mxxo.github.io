Hi

```rust
// max absolute wave speed is either
//   |u - a| or |u + a|
// where u can be negative. we can simplify this
// by finding |u| + a since the sound speed is always positive
pub fn max_stable_timestep(&self) -> f64 {
    self.cfl * self.delta_x / self.max_wave_speed()
}

pub fn max_wave_speed(&self) -> f64 {
    self.cells
        .iter()
        .map(|cell| cell.velocity().abs() + cell.sound_speed())
        .fold(0.0, |a, b| a.max(b)) // reduce to maximum
}
```
