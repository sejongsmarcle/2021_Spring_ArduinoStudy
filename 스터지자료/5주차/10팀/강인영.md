# 5주차 미션~~
## 인공지능의 개념과 티쳐블머신
이번 주제가 흥미로워서 한번 미션에 참여해보았다!   
지금 수강하는 과목 중에는 인공지능 관련된 것이 없지만...내년에는 접할 기회가 많을 거 같아서 기대가 된다.


### 인공지능의 개념
우선 인공지능에 대해 새롭게 알게 된 개념을 정리하자. 미션 공지에 첨부된 영상을 시청 소감: 모든 설명이 뇌에 흡수되는 느낌!  
AI와 가까워진 기분! (실제론 갈 길이 멀지만...) 영상에 의하면 딥러닝은 학습할 때 인간의 뉴런 신경망처럼 여러 계층을 만들어  
주어진 데이터를 그대로 활용할 수 있는데, 입력 신호를 가공해서 출력값을 도출하기 위해 활성화 함수가 매우 중요하다!!  
(결론: 수학 공부.. 열심히ㅠㅠ) 그리고 GAN 은 두 개의 모델이 서로 대결하며 학습하는 머신러닝이다. <--정말 흥미롭다...  



### 티쳐블머신  
이제 티쳐블 머신으로 나만의 인공지능 분류모델을 만들어보자! 나는 오디오 모델을 이용했는데 분류기준은 4가지였다.  
__Background Noise, whistle, clap, music__

1. 위의 기준에 따라 데이터를 수집하고,
2. 모델을 훈련시킨 다음,
3. 모델을 원하는 형태로 추출할 수 있다. (링크나 다운로드)

![audiomodel](https://user-images.githubusercontent.com/81199414/119164855-cbfb3c80-ba97-11eb-9512-2b25b7244918.PNG)  

#### Advanced 탭: 인공지능이 학습하는 방법 변경하기  
Training에서 advanced 탭에 epochs 라는 것이 있다. 한 번의 epoch는 인공 신경망에서 전체 데이터 셋에 대해 한 번 학습을 완료한 상태이다.  
예를 들어 epochs=60 이면 전체 데이터를 60번 학습한 것이다. epoch가 클수록 인공지능 모델이 데이터를 예측하는 정확도가 높아진다.  
* 주의:  epoch가 너무 작아도, 너무 커도 데이터 예측에 문제가 발생한다.  

그리고 batch size는 한번의 batch마다 주는 데이터 샘플의 크기라고 한다. batch는 나눠진 데이터 셋을 말한다.  
learning rate는 학습률인데 '어느 정도의 크기로, 기울기가 줄어드는 지점으로 이동하겠는가'를 나타내는 지표라고 한다.  
좀 어려운 개념이긴 한데.. 이것 역시 너무 값이 작으면 학습 속도가 매우 느려지고, 너무 크면 overshooting이 발생한다.  

실제로 epochs 값을 크게 바꿨더니 소리를 분류하는 정확도가 높아졌다! 
music 카테고리에는 요즘 빠진 노래 '어푸' 와 '서울의 잠 못 이루는 밤'을 샘플로 녹음했다. 
흥미롭게도 휘파람이 녹음된 노래를 틀면 인공지능 모델이 whistle, music 2가지를 모두 출력한다.  
참.. 신기하다! 당연한 거지만 인공지능은 참 똑똑하다.  이 모델을 개선할 수 있다면, '사람이 부는 휘파람 vs  
노래에 녹음된 휘파람 구분하기' 기능이 있으면 좋을 것 같다. 이를 위해서 데이터셋이 아주 많이 필요하겠지..?   
데이터 수집 단계에 가장 많은 돈과 시간이 소모되는 이유가 있다....

##### Audio model 코드와 링크는 아래와 같다.  
https://teachablemachine.withgoogle.com/models/xaQ7c0gRy/ 

     <div>Teachable Machine Audio Model</div>
     <button type="button" onclick="init()">Start</button>
     <div id="label-container"></div>
     <script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@1.3.1/dist/tf.min.js"></script>
     <script src="https://cdn.jsdelivr.net/npm/@tensorflow-models/speech-commands@0.4.0/dist/speech-commands.min.js"></script>

     <script type="text/javascript"
     // more documentation available at
     // https://github.com/tensorflow/tfjs-models/tree/master/speech-commands

     // the link to your model provided by Teachable Machine export panel
     const URL = "./my_model/";

     async function createModel() {
        const checkpointURL = URL + "model.json"; // model topology
        const metadataURL = URL + "metadata.json"; // model metadata

        const recognizer = speechCommands.create(
            "BROWSER_FFT", // fourier transform type, not useful to change
            undefined, // speech commands vocabulary feature, not useful for your models
            checkpointURL,
            metadataURL);

        // check that model and metadata are loaded via HTTPS requests.
        await recognizer.ensureModelLoaded();

        return recognizer;
     }
      async function init() {
        const recognizer = await createModel();
        const classLabels = recognizer.wordLabels(); // get class labels
        const labelContainer = document.getElementById("label-container");
        for (let i = 0; i < classLabels.length; i++) {
            labelContainer.appendChild(document.createElement("div"));
        }

        // listen() takes two arguments:
        // 1. A callback function that is invoked anytime a word is recognized.
        // 2. A configuration object with adjustable fields
        recognizer.listen(result => {
            const scores = result.scores; // probability of prediction for each class
            // render the probability scores per class
            for (let i = 0; i < classLabels.length; i++) {
                const classPrediction = classLabels[i] + ": " + result.scores[i].toFixed(2);
                labelContainer.childNodes[i].innerHTML = classPrediction;
            }
        }, {
            includeSpectrogram: true, // in case listen should return result.spectrogram
            probabilityThreshold: 0.75,
            invokeCallbackOnNoiseAndUnknown: true,
            overlapFactor: 0.50 // probably want between 0.5 and 0.75. More info in README
        });

        // Stop the recognition in 5 seconds.
        // setTimeout(() => recognizer.stopListening(), 5000);
       }
      </script> 


### 미션 클리어~ 인공지능과 관련된 다른 미션도 수행해보고 싶다!!
