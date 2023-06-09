<!--
 * @Author: mengkun822 1197235402@qq.com
 * @Date: 2023-06-08 19:45:01
 * @LastEditors: mengkun822 1197235402@qq.com
 * @LastEditTime: 2023-06-09 17:14:33
 * @FilePath: \knowledge_planet\docs\md\idea-plugin\Bug\Bug.md
 * @Description: 这是默认设置,请设置`customMade`, 打开koroFileHeader查看配置 进行设置: https://github.com/OBKoro1/koro1FileHeader/wiki/%E9%85%8D%E7%BD%AE
-->

> ### h5 端 ios 端获取日期时报错

在 H5 开发的时候，发现 new Date('2023-06-09')在安卓机运行是正常的，然后再 ios 却报错

原因： ios 不支持"2023-06-09"形式只支持"2023/06/09"

```js
new Date('2023-06-09'.replace(/-/g, '/')).getTime();
```
