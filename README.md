# Concrete_pore_image_segmentation
본 레퍼지토리에는 '콘크리트의 표면이미지'를 통해 공극을 segmentation하고 측정하기 어려운 공극률을 이미지를 활용하여 계측하는 알고리즘을 구현하였습니다.

# Data
- 표면이미지를 측정하기 위해 공극률을 다르게(콘크리트 배합비를 다르게) 한 콘크리트 큐브(50mmX50mmX50mm)를 제작하고 임의의 위치에서 표면 이미지를 촬영
- 표면이미지에서 공극에 해당하는 부분 masking
  - 표면이미지
    \![image](https://user-images.githubusercontent.com/69951894/227112155-cc38b1f2-8a20-454c-b9a0-fd86a29fc376.png)
  - Masking 이미지
    \![image](https://user-images.githubusercontent.com/69951894/227112227-a2071b26-0957-4800-b5f1-033d94a936a6.png)
    
# Model
- Unet
  - 공극과 그 위치를 찾는 segmentation 모델
  - ![image](https://user-images.githubusercontent.com/69951894/227115646-b6879d34-c630-4fd7-a3ea-1d4a5f1a4d0c.png)

# Evaluation
