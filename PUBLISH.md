# Publishing to npm

1. Pick a package name nobody has taken. Check with `npm view <name>`; a 404 means it is free. A scoped name such as
   `@your-npm-username/baileys` is always free for you.
2. Edit `package.json`: `name`, `version`, `author`, `homepage`, `repository`.
3. Install and build (Node 20+ and Yarn 4 through Corepack):

   ```bash
   corepack enable
   yarn install
   yarn lint
   yarn test
   yarn build
   ```

   `npm install` also works if you do not want Yarn, it just ignores `yarn.lock` and the `resolutions` block.
4. Log in and publish:

   ```bash
   npm login
   npm publish --access public
   ```

   `prepack` runs the build for you, so `lib/` does not need to be committed.
5. Use it in a bot:

   ```bash
   npm i glitch-baileys
   ```

   To keep existing imports working without touching bot code, alias it in the bot's `package.json`:

   ```json
   "dependencies": {
   	"@whiskeysockets/baileys": "npm:glitch-baileys@1.0.0"
   }
   ```

   Or install straight from GitHub without publishing: `"glitch-baileys": "github:YOUR_GITHUB_USERNAME/glitch-baileys"`.

Keep the `LICENSE` file as it is. Baileys is MIT licensed and the copyright notice has to stay with copies of the code.
