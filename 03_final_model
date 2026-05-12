# Model 3
ap_low <- as.numeric(df$pm25 < 15)
ap_high <- 1 - ap_low

int3 <- cbt1 * ap_high
int4 <- cbt1 * ap_low

fit3_1 <- update(fit1, deaths ~ cbt1 + pm25 + int3)
fit3_2 <- update(fit1, deaths ~ cbt1 + pm25 + int4)

pred3_1 <- crosspred(cbt1, fit3_1)
pred3_2 <- crosspred(cbt1, fit3_2)

plot(pred3_1, ptype = "overall", main = "RR Temp w/ Low AP")
plot(pred3_2, ptype = "overall", main = "RR Temp w/ High AP")

# We pick model 3
attrdl(
  x = df$temp,
  basis = cbt1,
  cases = df$deaths,
  coef = coef(fit3_1)[14:25],
  vcov = vcov(fit3_1)[14:25, 14:25],
  model.link = "af",
  type = "af",
  cen = 20,
  sim = FALSE
)