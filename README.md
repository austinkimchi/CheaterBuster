# Cheater Beater (AWS x Inrix Hack 2025)
<div style="text-align: center;">
  <p>
    <a href="LICENSE">
      <img src="https://img.shields.io/badge/License-MIT-red.svg" alt="MIT License" />
    </a>
    <a href="https://aws.amazon.com/">
      <img src="https://custom-icon-badges.demolab.com/badge/AWS-%23FF9900.svg?logo=aws&logoColor=white" alt="AWS" />
    </a>
    <a href="https://react.dev/">
      <img src="https://img.shields.io/badge/React-18.x-blue.svg" alt="React" />
    </a>
    <a href="https://nodejs.org/">
      <img src="https://img.shields.io/badge/Node.js-22+-green.svg" alt="Node.js" />
    </a>
  </p>
</div>


## Overview
**Cheater Beater** is a cheating detection application that can be scaled in classroom spaces. <br/>
Cheater Beater uses real-time video analysis powered by **AWS Rekognition** to detect "examination-banned" electronic devices, such as phones and laptops. <br/>
It captures frames from one or multiple live video feeds, analyzes them with a trained model, and flags suspicious activity. Professors can receive visual feedback showing what device was detected and where it appeared in the frame.

[![Demonstration Video](https://img.youtube.com/vi/U3FE1XJM4Hk/0.jpg)](https://www.youtube.com/watch?v=U3FE1XJM4Hk)
[![AlertBoxes](https://github.com/eric-kimm/CheatingAppBackend/blob/main/photos/annotated_2819768fda624af986687ad2d709508e.jpg?raw=true)

## Inspiration
In today’s classrooms, technology and AI tools have made cheating easier than ever, especially during online exams or in large lecture halls where it’s impossible for professors to monitor every student. We wanted to build a solution that could proactively help educators maintain academic integrity without needing constant manual supervision.

## How we built it
We built a FastAPI backend that receives live video frames through a websocket connection. These frames are sent to AWS Rekognition, where we first experimented with general models before creating our own custom Rekognition model trained to recognize cheating-related devices. 
We used:
- **Amazon Rekognition** Custom Labels to train our model on calculators, phones, and laptops.
- **FastAPI** + **OpenCV** to process and annotate frames with bounding boxes.
- **WebSockets** for low-latency communication between the live feed and detection backend.

---

## Challenges we ran into
One of our biggest challenges was that AWS Rekognition’s default model struggled to recognize smaller or less common devices, especially calculators, which were often missed unless they were close to the camera. To overcome this, we built and trained a custom Rekognition model, which required manually labeling and balancing hundreds of images across different categories for both training and testing. Along the way, we encountered technical hurdles such as image size limitations, S3 permission errors, and bounding box rendering issues before achieving stable detection results. Our model had to be retrained multiple times to improve accuracy and confidence scores, and each iteration took 30–60 minutes to build and deploy, limiting how quickly we could test and refine our results.

---

## Accomplishments that we're proud of
Some accomplishments that we were proud of was successfully training a custom AWS Rekognition model capable of identifying multiple devices with strong accuracy, Integrated this with a live streaming pipeline, allowing real-time detection directly from a webcam or exam video feed, and having a final prototype that visually highlights detected devices and outputs detailed JSON logs for further review.

---

## What we learned
We learned how to use AWS Rekognition Custom Labels end-to-end, from dataset creation and labeling to model training and inference. We also deepened our understanding of AWS IAM policies, S3 bucket configurations, and efficient video streaming over websockets. Most importantly, we learned how to break down a large-scale idea into a working, testable prototype under time constraints. Another area where we gained a lot of experience was debugging because we were constantly having to retrain and update our custom rekognition model to actually detect the images we wanted to identify.


---

## Contributors
- [Austin Kim](https://github.com/austinkimchi)
- [Aarav Mehta]()
- [Eric Kim](https://github.com/eric-kimm/)
- [Stefan Murphy](https://github.com/StefanMerfy)


---

## License  
This project is licensed under the **MIT License** — see the [LICENSE](LICENSE) file for details.
