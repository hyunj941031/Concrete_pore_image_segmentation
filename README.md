# Concrete_pore_image_segmentation
본 레퍼지토리에는 '콘크리트의 표면이미지'를 통해 공극을 segmentation하고 측정하기 어려운 공극률을 이미지를 활용하여 계측하는 연구를 바탕으로 한 알고리즘을 구현하였습니다.

# Data
- 표면이미지를 측정하기 위해 공극률을 다르게(콘크리트 배합비를 다르게) 한 콘크리트 큐브(50mmX50mmX50mm)를 제작하고 임의의 위치에서 표면 이미지를 촬영
- 표면이미지에서 공극에 해당하는 부분 masking
  - 표면이미지
    - ![image](https://user-images.githubusercontent.com/69951894/227112155-cc38b1f2-8a20-454c-b9a0-fd86a29fc376.png)
  - Masking 이미지
    - ![image](https://user-images.githubusercontent.com/69951894/227112227-a2071b26-0957-4800-b5f1-033d94a936a6.png)
  - 실제 공극률 측정은 XRM(X-Ray Microscope)을 통해 3차원으로 가시화하였고 공극에 해당하는 부피를 정확하게 측정함
    
# Model
- Unet
  - 공극과 그 위치를 찾는 segmentation 모델
  - ![image](https://user-images.githubusercontent.com/69951894/227115646-b6879d34-c630-4fd7-a3ea-1d4a5f1a4d0c.png)

# Evaluation
  - Mean of Porosity (Measured & Predicted)
    - <img src = "https://user-images.githubusercontent.com/69951894/227414980-4ce41d7f-e27c-44ab-b968-1530f3c784fd.png" width="50%" height="30%">
  - Accuracy
    - <img src = "https://user-images.githubusercontent.com/69951894/227416370-c3746afe-e9f3-4a39-9929-c0ac71577202.png" width="80%" height="60%">
  - Loss
    - <img src = "https://user-images.githubusercontent.com/69951894/227417234-ed7269b9-6e52-4775-9dcf-a2570e51592f.png" width="80%" height="60%">
  - Prediction Sample
    - ![image](https://user-images.githubusercontent.com/69951894/227418506-6071ae74-4b8f-45c8-9562-16e1fd0eba11.png)
  - Sample size
    - ![image](https://user-images.githubusercontent.com/69951894/227418967-4e9f07ee-61e3-4c81-8a7e-5d7d7acdd11b.png)


  ### - 고찰
        - 공극률 평균값이 차이가 나는 이유는 콘크리트의 부위마다 공극률이 다르기 때문에 측정된 부분의 공극률이 전체를 대표하지 못해서 발생하는 차이로 보임
        - 측정값을 늘려서 비교하면 차이가 더 안정적으로 나타날 것으로 보이나 금전적인 문제로 현재로썬 상당히 어려움
        - Image Segmentation의 성능은 validation accuracy가 98%정도로 매우 우수한 성능을 보임
        - 예측한 이미지를 확인해보면 공극인 부분의 위치를 잘 예측하는 모습을 보임
        - 공극률이 콘크리트 위치마다 다르다는 특징은 필요표본크기 추정식을 통해 보완하여 콘크리트의 전체 평균적인 공극률을 알기 위한 필요 표본 이미지 수를 구할 수 있음.
# - Conclusion
  - 이미지만으로 콘크리트에서 공극을 구분하는 segmentation model을 개발하였다.
  - Segmentation 성능은 우수하지만 다양한 빛 환경에서의 이미지나 다양한 종류의 콘크리트 이미지를 추가적으로 학습하면 다양한 상황에서 안정적인 모델이 될 수 있을 것으로 보인다.
  - 콘크리트 균열 탐지 모델과 접목시켜서 같이 학습을 시키면 균열과 공극률 모두 알 수 있고 압축강도도 추정할 수 있는 모델을 만들 수 있을 것으로 보인다.
