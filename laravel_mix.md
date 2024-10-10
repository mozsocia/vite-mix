
Here's a setup using Vite.js that mimics Laravel Mix functionality for compiling and watching JS and CSS files:

```javascript
// vite.config.js
import { defineConfig } from 'vite';
import { resolve } from 'path';

export default defineConfig({
  build: {
    outDir: 'dist',
    rollupOptions: {
      input: {
        main: resolve(__dirname, 'src/js/main.js'),
        styles: resolve(__dirname, 'src/css/styles.css'),
      },
      output: {
        entryFileNames: 'js/[name].js',
        assetFileNames: 'css/[name].[ext]',
      },
    },
  },
  plugins: [
    {
      name: 'watch-external',
      buildStart() {
        this.addWatchFile(resolve(__dirname, 'src/js/**/*.js'));
        this.addWatchFile(resolve(__dirname, 'src/css/**/*.css'));
      },
    },
  ],
});
```

This configuration will:

1. Compile JS files from `src/js/main.js`
2. Compile CSS files from `src/css/styles.css`
3. Output compiled files to a `dist` folder
4. Watch for changes in all JS and CSS files in their respective directories

To use this setup:

1. Install Vite: `npm install vite --save-dev`
2. Create the `vite.config.js` file with the above content
3. Add these scripts to your `package.json`:

```json
"scripts": {
  "dev": "vite",
  "build": "vite build",
  "watch": "vite build --watch"
}
```

4. Run `npm run dev` for development or `npm run watch` to watch for changes

Would you like me to explain or break down any part of this setup?
