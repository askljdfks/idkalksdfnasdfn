Age Predictor Model

This model is used to find out what finger you are pointing. It is trained on an imagenet Resnet-18 model using transfer learning. 


## The Algorithm
The algorithim is used by taking a picture and using that file to upload it to the code. It uses a 2GB Jetson Nano, and so it uses it a preflashed SD card flashed from the NVIDIA webpage. It uses a facenet to find a person's hand and finger in the image, then it crops the image to just hold the finger. It then sends the picture of the finger to the transfer learning model. The transfer model then predicts what finger you are pointing. It will try to guess what finger it is to the best of its abilities. Then it will print out what finger you are pointing is it is confident. It is up to the user to interepret the information.
Note: I ran this model on a realivly low epoch with information that was askew. The pretrained model is quite inacurrate.
## Running this project

1. Connect to your Jetson Nano via VSCODE. 
2. Find your image file of your finger pointing something
3. Ensure that you have the proper things installed. The Renet18.onnx and all others like that - the ones that say resnet18.onnx and the final_project2.py. Also, esure that you have the labels.txt file.
4. Since using teh preflashed SD card, there sould be a docker container. This is accesable by implementing this code. Change directories into jetson-inference/build/aarch64/bin. - use this code if your in the home.$ cd jetson-inference/build/aarch64/bin
5. Then run this code -$ ./docker/run.sh --volume /home/(username)/final-projects:/final-projects        - the code moves the final-projects folder into the docker container so that the line from PIL import Image runs without an error.
6a. Run this command but fill in the blanks according to what was filled before hand: 
imagenet.py --model=$NET/resnet18.onnx --input_blob=input_0 --output_blob=output_0 --labels=$DATASET/labels.txt $DATASET/test/Folder/File_In_Folder.jpg New_Image_Name.jpg

6b. Enter your password to the jetson nano then let it load.

7. Now go to the files section of the VSCODE and find what you named each image

[View a video explanation here]((https://youtu.be/i4QWmjPIluw)https://youtu.be/i4QWmjPIluw)
Some files were impossible to upload to github so here is the link to the ones I couldn't upload: https://drive.google.com/drive/folders/1d37EMquOH7gCN_P7kG_TTXOZS-dmuiKm?usp=sharing

