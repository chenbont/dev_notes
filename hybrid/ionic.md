# ionic 
## 1.创建新页面
在命令行执行
```
ionic g page learn-start
```
然后在pages.modules.ts 中添加 
```
import {LearnStartPageModule} from "./learn-start/learn-start.module"
```
并将 LearnStartPageModule 添加到 imports:[] 的数组中
