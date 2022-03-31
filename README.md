# 22.01.23
- [22.01.23](#220123)
  * [[MsEmoTTS: Multi-scale emotion transfer, prediction, and control for emotional speech synthesis]
 
## [MsEmoTTS: Multi-scale emotion transfer, prediction, and control for emotional speech synthesis](https://arxiv.org/pdf/2201.06460.pdf) <a name="220123"></a>
![https://github.com/ghlee0304/Technical_Reposit/blob/master/MsEmoTTSMulti-scale%20emotion%20transfer1.PNG?raw=true](https://github.com/ghlee0304/Technical_Reposit/blob/master/MsEmoTTSMulti-scale%20emotion%20transfer1.PNG?raw=true)
    - Sample URL : [https://leiyi420.github.io/MsEmoTTS/](https://leiyi420.github.io/MsEmoTTS/)
    1. Goal : expressive emotion speech synthesis 를 위한 TTS 모델을 제안
    2. Problem : 기존의 emotion TTS 들은 explicit label 혹은 reference audio로부터 고정된 길이의 style embedding을 사용하였는데 이는 각 감정 카테고리 내의 샘플들의 평균 스타일만 학습하게 되어 표현력이 제한됨
    3. Method : Tacotron encoder와 Tacotron2 decoder를 사용하고 3개의 모듈을 제안
        1. Global-level emotion presenting module (GM)
            - 학습 시에는 label을 이용하여 감정에 대한 global embedding을 넣음
            - 합성 시에는 text를 입력으로 하는 Emotion classifier를 사용
            - Emotion classifier는 BERT 기반 모델에 softmax를 추가하였음
            - text로 emotion을 예측하는데는 한계가 있어서 softmax output을 이용한 weighted emotional embedding을 사용
        2. Utterance-level emotion presenting module (UM)
            - UM이 Table V, Fig. 5의 결과를 통해 억양의 경향을 학습할 수 있는 것으 보여줌
        3. Local-level emotion presenting module (LM)
            - 감정의 강도를 배우기 위한 모듈로 unsupervised 방식으로 학습
            - ranking function을 이용하여 syllable 단위의 감정 강도를 학습
            - 이 부분이 전체 논문에서 가장 특이한 부분이라고 생각
    4. DataSet
        1. 여자 전문 성우 한 명의 목소리로 neutral, 6가지 감정(happiness, anger, sadness, surprise, fear, disgust)로 이루어져 있음
        2. 총 10,000 발화 (약 10시간 분량)의 neutral voice와 각 2,000발화(약 2시간) 분량의 emotion 데이터가 있음
        3. BERT 기반의 classifier는 추가적으로 3,500(happy), 2,600(angry), 3300(sad), 1100(surprise), 400(fear), 4,100(disgust), 38,000(neutral)을 사용하였음
    5. Results
![https://github.com/ghlee0304/Technical_Reposit/blob/master/MsEmoTTSMulti-scale%20emotion%20transfer2.PNG?raw=true](https://github.com/ghlee0304/Technical_Reposit/blob/master/MsEmoTTSMulti-scale%20emotion%20transfer2.PNG?raw=true)
![https://github.com/ghlee0304/Technical_Reposit/blob/master/MsEmoTTSMulti-scale%20emotion%20transfer4.PNG?raw=true](https://github.com/ghlee0304/Technical_Reposit/blob/master/MsEmoTTSMulti-scale%20emotion%20transfer4.PNG?raw=true)
