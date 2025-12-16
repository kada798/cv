// 优化拼图场景中的切片显示比例，使其更符合原图比例，提升视觉效果；增加横轴拖动查看完整拼图的功能。
// 优化元数据场景的交互反馈，增加正确与错误选择的颜色区分。

/// 问题：点击拼图碎片，不是选中的拼图碎片，用户无法得知自己点击了哪个碎片；添加边框后，只显示点击的第一个碎片的边框，第二个与之交换的碎片没有边框显示。
/// （解决方案：为每个拼图碎片添加边框属性，并在交换碎片时更新边框位置。？）
/// 

2025.11.1
BUG1: 图片无法加载,图片完全黑色条状显示，无法正常打开;Failed to load resource ... CORS policy
RAISON : 浏览器不能直接从 file:// 加载本地文件到 Phaser，这会导致：
Failed to load resource ... CORS policy
这是因为 Chrome / Firefox 默认禁止本地跨域读取资源。
SOLUTION：VSCode + Live Server

BUG2: img.setStrokeStyle is not a function
SOLUTION： CHATGPT：
// 创建边框（透明）
const border = this.add.rectangle(
    img.x, img.y,
    displaySliceW, displaySliceH
).setStrokeStyle(0, 0xffffff).setOrigin(0.5);

img.border = border;


![alt text](<屏幕截图 2025-11-16 224403.png>)
raison：图片过大（29,9 MB），分辨率过高-32699*1500，超过网页可以承受的范围（浏览器（特别是 WebGL）有一个最大纹理尺寸（取决于显卡，常见：4096～16384）；
solution：1.压缩图片到10MB，仍然黑条状无法显示，转而调整分辨率到21384宽*1000高 png，仍然过高，Chat gpt 提供的解决方法为切片（tiles）。然后变成了细条状。![alt text](<屏幕截图 2025-11-25 050850.png>)
