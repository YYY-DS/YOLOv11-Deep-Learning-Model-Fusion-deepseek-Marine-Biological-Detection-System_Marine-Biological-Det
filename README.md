# YOLOv11深度学习模型融合deepseek海洋生物检测系统  | 海洋生物检测 YOLOv11 目标检测 深度学习 计算机视觉 Vue3 SpringBoot Flask9164期

## 系统概述

本系统基于**YOLOv11深度学习模型**，融合 **Pytorch、Flask、SpringBoot、Vue、MySQL** 等技术，构建了一套支持**图片、视频、摄像头**三种检测方式的海洋生物识别平台。系统适配海洋生物识别、科研教育及智能应用等场景。
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/ee1ef1887f494a59bce8614bc8ff3f20.png)

## 系统核心信息

| 项目 | 详细说明 |
| :--- | :--- |
| **检测类别** | 涵盖海豚、企鹅、海星、鲨鱼、海龟等多种海洋生物 |
| **核心技术** | YOLOv11 + Pytorch + Flask + SpringBoot + Vue3 |
| **检测模式** | 图片检测、视频检测、摄像头实时检测 |
| **系统架构** | 前后端分离（Vue3 + SpringBoot + Flask + MySQL） |
| **应用价值** | 1. **海洋生物识别**：支撑海洋生物种类的自动识别与分类。<br>2. **科研教育**：为海洋生物学研究、教学演示提供视觉工具。<br>3. **智能应用**：可迁移至其他检测场景，支持自定义训练模型。 |


![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7f18614d99c64b0d859aeae22cf36afe.png)

## 技术栈

| 层次 | 技术选型 |
| :--- | :--- |
| **前端** | Vue3、Element-Plus、TypeScript |
| **后端** | SpringBoot、MyBatis-Plus、Flask |
| **深度学习** | YOLOv11、Pytorch |
| **数据库** | MySQL |
| **视频处理** | FFmpeg |


![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7cb9c468597b409f88bd65982317ca27.png)

## 系统功能

**1. 多模态检测支持**
- 图片检测：上传图片，返回检测结果
- 视频检测：上传视频，逐帧分析，输出标注视频
- 摄像头实时检测：连接摄像头，实时输出检测结果

**2. 海洋生物识别**
- 支持多种海洋生物识别（海豚、企鹅、海星、鲨鱼、海龟等）
- 检测精度高，速度快

**3. 模型定制**
- 支持自定义训练模型，生成权重文件
- 可更换其他检测场景，价格私聊

**4. 用户管理**
- 管理员可查看所有检测记录
- 普通用户仅查看自己的记录

**5. 界面个性化**
- 界面简洁美观
- 支持主题色、布局、组件大小个性化


![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/7bb20eff6253427c8ae1872cf12c5eaa.png)
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/d9925251e5df477b8e3ffa17ef953475.png)

## 交付内容

- **完整系统代码**：前端、后端、YOLO算法
- **数据集与训练文件**
- **安装部署文档**
- **数据库文件**
![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/edeee74a23194130a90ae6410a6307d2.png)

## 快速开始（代码示例）

**1. 数据集配置文件 (`data.yaml`)**
```yaml
train: ./dataset/images/train
val: ./dataset/images/val
nc: 5
names: ['dolphin', 'penguin', 'starfish', 'shark', 'turtle']
```

**2. YOLOv11 训练代码**
```python
from ultralytics import YOLO

model = YOLO('yolo11n.pt')
model.train(
    data='data.yaml',
    epochs=100,
    imgsz=640,
    batch=16,
    device=0
)
```

**3. Flask 推理服务**
```python
from flask import Flask, request, jsonify
from ultralytics import YOLO
import cv2

app = Flask(__name__)
model = YOLO('runs/detect/train/weights/best.pt')

@app.route('/detect', methods=['POST'])
def detect():
    file = request.files['image']
    img = cv2.imdecode(np.frombuffer(file.read(), np.uint8), cv2.IMREAD_COLOR)
    results = model(img)
    detections = []
    for box in results[0].boxes:
        detections.append({
            'class': model.names[int(box.cls[0])],
            'confidence': float(box.conf[0]),
            'bbox': box.xyxy[0].tolist()
        })
    return jsonify(detections)

if __name__ == '__main__':
    app.run(host='0.0.0.0', port=5000)
```


![在这里插入图片描述](https://i-blog.csdnimg.cn/direct/2ca8de82cd2e4669a710867ca9879d8b.png)

## 标签
`海洋生物检测` `YOLOv11` `目标检测` `深度学习` `计算机视觉` `Vue3` `SpringBoot` `Flask`
