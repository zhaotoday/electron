修复开发模式下升级无法使用的 Bug：
在根目录创建 dev-app-update.yml 文件：
```yml
provider: generic
url: https://releases.xxx.com/test/client/win/x64/
```
升级文件加一下代码：
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
