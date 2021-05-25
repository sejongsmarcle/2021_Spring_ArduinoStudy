5주차 미션
===============
c프로그래밍 인증 시험 드디어 끝났다.    
진짜 c프로그래밍 2차 인증이 너무 어려워서 재수강 신청이 언젠지 보고있었는데     
오늘 인증시험 통과했다는 공지가 떳다!!!   
**********************  

이제 스마클 미션하러..!!   
이번 미션은 인공지능이라 굉장히 재밌을 것 같다.


-----------------------------------
인공지능은 푸들이랑 치킨이랑 구분을 못한다고 들어본 기억이 있다.   
그래서 오늘 인공지능을 헷갈리게 해보겠다!!   
----------

![개개개](https://user-images.githubusercontent.com/81511939/119467492-859c2b00-bd80-11eb-9d5c-25651fa28864.PNG)   
아쉽...   

------------

![ㅋㅋㅋㅋㅋㅋㅋ이건 개](https://user-images.githubusercontent.com/81511939/119467560-95b40a80-bd80-11eb-99c2-07a54703afb3.PNG)   
...??   

----------------

![개같은 치킨 2](https://user-images.githubusercontent.com/81511939/119467673-b2504280-bd80-11eb-9080-cc5704405424.PNG)   
???ㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋㅋ

---------

내가 쓴 코드
---   
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

