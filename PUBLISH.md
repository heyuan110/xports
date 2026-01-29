# npm 发布备忘

## 账号信息

- npm 用户名：`hebruce110`
- npm 组织：`heyuan110`
- 包名：`@heyuan110/xports`
- 2FA 方式：Security Key（macOS 密码管理器）

## 发布步骤

```bash
cd ~/projects/xports

# 1. 确认已登录
npm whoami
# 如果没登录：npm login

# 2. 修改 package.json 中的 version（如果需要升版本）
# npm version patch   # 1.0.0 → 1.0.1
# npm version minor   # 1.0.0 → 1.1.0
# npm version major   # 1.0.0 → 2.0.0

# 3. 发布（scoped 包需要 --access public）
npm publish --access public
# 浏览器会弹出 Security Key 验证，按指纹/输入密码确认
```

## 踩坑记录

1. **npm 强制要求 2FA** — 不开 2FA 发不了包，报 `E403 Two-factor authentication required`
2. **Security Key 没有 OTP** — Security Key 方式不产生 6 位验证码，无法用 `--otp=xxx`
3. **Classic Token 已废弃** — npm 已废弃 Classic Token，只能用 Granular Access Token
4. **Granular Token bypass 2FA** — 创建时必须勾选 "Bypass two-factor authentication"，否则还是会被拦
5. **unscoped 包名权限** — 新账号可能无法发布 unscoped 包（如 `xports`），改用 scoped 包名 `@heyuan110/xports`
6. **必须 `--access public`** — scoped 包默认 private，需要加 `--access public` 才能公开
7. **最稳做法** — 直接在终端跑 `npm publish --access public`，浏览器弹出 Security Key 验证即可
