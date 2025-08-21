```ts
import path from 'path';
import fs from 'fs';

if (process.env.NODE_ENV === 'development') {
  const devUpdateConfigPath = path.join(__dirname, 'dev-app-update.yml');
  Object.defineProperty(app, 'isPackaged', {
    get() {
      return true;
    },
  });
  if (fs.existsSync(devUpdateConfigPath)) {
    autoUpdater.updateConfigPath = devUpdateConfigPath;
  }
}
```
