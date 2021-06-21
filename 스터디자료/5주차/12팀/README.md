### 5주차 미션!!
이번 주차는 직접 티처블 머신을 작동시키는 것이다!

#### 나만의 티처블 머신!
나는 내가 정말 좋아하고 사랑하지만 나만 없는 고양이 종류를 분류해볼 것이다!

내가 제일 좋아하는 종 세개..

페르시안,시암,브리티시 숏헤어 이 세개의 종류를 학습시켜 분류 해볼 것이다!

![persian3](https://user-images.githubusercontent.com/81364249/122805855-951d7e00-d304-11eb-95ac-3f252d7f7da3.jpg)

![시암 셈플](https://user-images.githubusercontent.com/81364249/122805987-bc744b00-d304-11eb-9e29-f7b80b72f43c.jpg)

![브리티쉬 5](https://user-images.githubusercontent.com/81364249/122806043-d0b84800-d304-11eb-9861-219b09774f72.jpg)

너무 귀엽지 않나요..고양이 나만 없숴..

그렇게 만든 나만의 티처블 머신

![5주차 미션 1](https://user-images.githubusercontent.com/81364249/122806226-0a894e80-d305-11eb-9c32-a8932e5ad1ed.png)

#### 코드

<div>Teachable Machine Image Model</div>
<button type="button" onclick="init()">Start</button>
<div id="webcam-container"></div>
<div id="label-container"></div>
<script src="https://cdn.jsdelivr.net/npm/@tensorflow/tfjs@1.3.1/dist/tf.min.js"></script>
<script src="https://cdn.jsdelivr.net/npm/@teachablemachine/image@0.8/dist/teachablemachine-image.min.js"></script>
<script type="text/javascript">
    // More API functions here:
    // https://github.com/googlecreativelab/teachablemachine-community/tree/master/libraries/image

    // the link to your model provided by Teachable Machine export panel
    const URL = "./my_model/";

    let model, webcam, labelContainer, maxPredictions;

    // Load the image model and setup the webcam
    async function init() {
        const modelURL = URL + "model.json";
        const metadataURL = URL + "metadata.json";

        // load the model and metadata
        // Refer to tmImage.loadFromFiles() in the API to support files from a file picker
        // or files from your local hard drive
        // Note: the pose library adds "tmImage" object to your window (window.tmImage)
        model = await tmImage.load(modelURL, metadataURL);
        maxPredictions = model.getTotalClasses();

        // Convenience function to setup a webcam
        const flip = true; // whether to flip the webcam
        webcam = new tmImage.Webcam(200, 200, flip); // width, height, flip
        await webcam.setup(); // request access to the webcam
        await webcam.play();
        window.requestAnimationFrame(loop);

        // append elements to the DOM
        document.getElementById("webcam-container").appendChild(webcam.canvas);
        labelContainer = document.getElementById("label-container");
        for (let i = 0; i < maxPredictions; i++) { // and class labels
            labelContainer.appendChild(document.createElement("div"));
        }
    }

    async function loop() {
        webcam.update(); // update the webcam frame
        await predict();
        window.requestAnimationFrame(loop);
    }

    // run the webcam image through the image model
    async function predict() {
        // predict can take in an image, video or canvas html element
        const prediction = await model.predict(webcam.canvas);
        for (let i = 0; i < maxPredictions; i++) {
            const classPrediction =
                prediction[i].className + ": " + prediction[i].probability.toFixed(2);
            labelContainer.childNodes[i].innerHTML = classPrediction;
        }
    }
</script>

#### 모델 링크!

https://teachablemachine.withgoogle.com/models/ejLugv5sc/

### Epochs
Epochs는 트레이닝 시키는 횟수를 의미하고 Epochs가 크면 클수록 더 좋은 결과를 얻을 수 있다고 한다

### 5주차 미션 끝!
드디어 5주차까지 끝냈다..!

이제 잠을..
