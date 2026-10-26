<h2>TensorFlow-FlexUNet-Image-Segmentation-CVC-ClinicDB (2026/10/27)</h2>
Sarah T. Arai<br>
Software Laboratory antillia.com<br><br>

This is the first experiment of Image Segmentation for <b>CVC-ClinicDB </b>
 based on
our <a href="https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Model">TensorFlowFlexUNet Model</a>
 (<b>TensorFlow Flexible UNet Image Segmentation Model for Multiclass</b>) and a 512x512-pixel upscaled PNG
 <a href="https://drive.google.com/file/d/1JNVdeHh36avltLnWCsuu4PoTwGYK5Dot/view?usp=sharing">
Augmented-CVC-ClinicDB-ImageMask-Dataset.zip</a> 
which was derived by us from the Kaggle  
<br><br>
<a href="https://github.com/openmedlab/Awesome-Medical-Dataset/blob/main/resources/CVC-ClinicDB.md">
<b>CVC-ClinicDB</b>
</a>
<br><br>
<hr>
<b>Actual Image Segmentation for CVC-ClinicDB Images of 512x512 pixels</b><br>
As shown below, the inferred masks resemble the ground-truth masks. <br>
<br>
<table>
<tr>
<th width="320" height="auto">Input: image</th>
<th width="320" height="auto">Mask (ground_truth)</th>
<th width="320" height="auto">Prediction: inferred_mask</th>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/10055.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/10055.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/10055.png" width="320" height="auto"></td>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/rotated_90_10180.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/rotated_90_10180.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/rotated_90_10180.png" width="320" height="auto"></td>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/vflipped_10497.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/vflipped_10497.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/vflipped_10497.png" width="320" height="auto"></td>
</tr>
</table>
<hr>
<br>
<h3>1. Dataset Citation</h3>
The dataset used here was derived from the following Kaggle:<br><br>
<a href="https://github.com/openmedlab/Awesome-Medical-Dataset/blob/main/resources/CVC-ClinicDB.md">
<b>CVC-ClinicDB</b>
</a>
<br><br>
The following explanation was taken the website above.
<br><br>
<b>Dataset Information</b><br>
CVC-ClinicDB is the official dataset for the training phase of the MICCAI 2015 Endoscopic Video 
Automatic Polyp Detection sub-challenge. The database consists of 612 static images extracted 
from colonoscopy examination videos, originating from 29 different sequences. <br>
Each frame image is accompanied by a ground truth mask, which is used to identify the area covered by polyps in the image. Polyp segmentation is of significant importance when it comes to colonoscopy examinations and gastrointestinal tumor screening. By separating polyps from the surrounding normal tissues in medical imaging, a clearer visual reference is provided, helping doctors to accurately determine the location, shape, and size of the polyps. This is crucial for preliminary assessment 
of the nature of the polyps (benign or malignant) and for formulating corresponding treatment plans.
<br><br>
<b>Citation</b><br>
<pre>
@article{bernal2015wm,
  title={WM-DOVA maps for accurate polyp highlighting in colonoscopy: Validation vs. saliency maps from physicians},
  author={Bernal, Jorge and S{\'a}nchez, F Javier and Fern{\'a}ndez-Esparrach, Gloria and Gil, Debora and Rodr{\'\i}guez, Cristina and Vilari{\~n}o, Fernando},
  journal={Computerized medical imaging and graphics},
  volume={43},
  pages={99--111},
  year={2015},
  publisher={Elsevier}
}
</pre>
<br>
For more information, please refer to <a href="https://gts.ai/dataset-download/cvc-clinicdb/">
CVC-ClinicDB 
</a><br>
<br>
<b>License</b><br>
Unknown
<br>
<br>
<h3>
2. CVC-ClinicDB ImageMask Dataset
</h3>
<h3>2.1 Download ImageMask Dataset</h3>
 If you would like to train this CVC-ClinicDB Segmentation model,
 please download the dataset from Google Drive  
 <a href="https://drive.google.com/file/d/1JNVdeHh36avltLnWCsuu4PoTwGYK5Dot/view?usp=sharing">
Augmented-CVC-ClinicDB-ImageMask-Dataset.zip</a>. 
Expand the downloaded ImageMaskDataset and put it under the <b>./dataset</b> folder.
<br>
<pre>
./dataset
└─CVC-ClinicDB
    ├─test
    │   ├─images
    │   └─masks
    ├─train
    │   ├─images
    │   └─masks
    └─valid
         ├─images
         └─masks
</pre>
<br>
<b>CVC-ClinicDB Statistics</b><br>
<img src ="./projects/TensorFlowFlexUNet/CVC-ClinicDB/CVC-ClinicDB_Statistics.png" width="512" height="auto"><br>
<br>
As shown above, the number of images in the training and valid datasets is large enough to use for the
 training set of our segmentation model.
<br>
<h3>2.2 Derivation of ImageMask Dataset</h3>
The folder structure of the original dataset  
</a> is as follows.
<pre>
./CVC-ClinicDB
  ├─image
  │   ├─1.tif
...
  │   └─612.tif
  │
  └─masks
      ├─1.tif
...
      └─612.tif
</pre>
In this experiment, we geneated a 512x512-pixel upscaled PNG augmented ImageMask dataset  
from the original TIF images and masks by using some image flipping and rotation tools.
<br><br>
<h3>2.3 Train Sample Images and Masks</h3>
<b>Train_sample_images</b><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/train_images_sample.png" width="1024" height="auto">
<br>
<b>Train_sample_masks</b><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/train_masks_sample.png" width="1024" height="auto">
<br>
<h3>
3. Train TensorFlowFlexUNet Model
</h3>
 We trained the CVC-ClinicDB TensorFlowFlexUNet model using the following
<a href="./projects/TensorFlowFlexUNet/CVC-ClinicDB/train_eval_infer.config"> <b>train_eval_infer.config</b></a> file. <br>
Please move to ./projects/TensorFlowFlexUNet/CVC-ClinicDB and run the following bat file.<br>
<pre>
>1.train.bat
</pre>
This runs the following command.<br>
<pre>
>python ../../../src/TensorFlowFlexUNetTrainer.py ./train_eval_infer.config
</pre>
<hr>

<b>Model parameters</b><br>
Defined a small <b>base_filters=16 </b> and large <b>base_kernels=(11,11)</b> for the first Conv Layer of Encoder Block of 
<a href="./src/TensorFlowFlexUNet.py">TensorFlowFlexUNet.py</a> 
and a large <b>num_layers=8</b> (including a bridge between Encoder and Decoder Blocks).
<pre>
[model]
; You may specify your own UNet class derived from our TensorFlowFlexModel
model         = "TensorFlowFlexUNet"
generator     =  False
image_width    = 512
image_height   = 512
image_channels = 3
num_classes    = 2
base_filters   = 16
base_kernels   = (11,11)
num_layers     = 8
dropout_rate   = 0.05
; Specified a large dilation.
dilation       = (1,1)
</pre>
<b>Learning rate</b><br>
Defined a small learning rate.  
<pre>
[model]
learning_rate  = 0.00007
</pre>
<b>Loss and metrics functions</b><br>
Specified "categorical_focal_dice_loss" and <a href="./src/dice_coef_multiclass.py">"dice_coef_hybrid"</a>.<br>
<pre>
[model]
loss           = "categorical_focal_dice_loss"
metrics        = ["dice_coef_hybrid"]
hybrid_alpha   = 1.6
hybrid_beta    = 0.4
</pre>
<b>Dataset class</b><br>
Specifed <a href="./src/ImageCategorizedMaskDataset.py">ImageCategorizedMaskDataset</a> class.<br>
<pre>
[dataset]
class_name    = "ImageCategorizedMaskDataset"
</pre>
<br>
<b>Learning rate reducer callback</b><br>
Enabled the learning_rate_reducer callback and a small reducer_patience.
<pre> 
[train]
learning_rate_reducer = True
reducer_factor     = 0.4
reducer_patience   = 4
</pre>
<b>Early stopping callback</b><br>
Enabled early stopping callback with the patience parameter.
<pre>
[train]
patience      = 10
</pre>

<b>RGB Color map</b><br>
Specified RGB color map dict for CVC-ClinicDB 2 classes.<br>
<pre>
[mask]
mask_datatype= "categorized"
mask_file_format = ".png"
; CVC-ClinicDB RGB color map dict for 1+1 classes.
;      Background: black, Polyp: white 
rgb_map = {(0,0,0):0,(255,255,255):1,}
</pre>

<b>Epoch change inference callback</b><br>
Enabled <a href="./src/EpochChangeInferencer.py">epoch_change_infer callback</a></b>.<br>
<pre>
[train]
epoch_change_infer       = True
epoch_change_infer_dir   =  "./epoch_change_infer"
num_infer_images         = 6
</pre>

By using this callback, on every epoch change, the inference procedure can be called
 for 6 images in the <b>mini_test</b> folder. This will help you confirm how the predicted mask changes 
 at each epoch during your training process.<br> 
<br> 
<!--
As shown below, early in the model training, the predicted masks from our FlexUNet segmentation model showed 
discouraging results.
 However, as training progressed through the epochs, the predictions gradually improved. 
 <br> 
<br>
-->
<b>Epoch_change_inference output at starting (epoch 1,2,3)</b><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/epoch_change_infer_at_start.png" width="1024" height="auto"><br>
<br>
<b>Epoch_change_inference output at middlepoint (epoch 21,22,23)</b><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/epoch_change_infer_at_middle.png" width="1024" height="auto"><br>
<br>
<b>Epoch_change_inference output at ending (epoch 43,44,45)</b><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/epoch_change_infer_at_end.png" width="1024" height="auto"><br>
<br>
In this experiment, the training process was terminated at epoch 45.<br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/train_console_output_at_epoch45.png" width="1024" height="auto"><br>
<br>
<a href="./projects/TensorFlowFlexUNet/CVC-ClinicDB/eval/train_metrics.csv">train_metrics.csv</a><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/eval/train_metrics.png" width="520" height="auto"><br>
<br>
<a href="./projects/TensorFlowFlexUNet/CVC-ClinicDB/eval/train_losses.csv">train_losses.csv</a><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/eval/train_losses.png" width="520" height="auto"><br>
<br>
<h3>
4. Evaluation
</h3>
Please move to <b>./projects/TensorFlowFlexUNet/CVC-ClinicDB</b> folder,<br>
and run the following bat file to evaluate the TensorFlowUNet model for CVC-ClinicDB.<br>
<pre>
./2.evaluate.bat
</pre>
This runs the following command.
<pre>
python ../../../src/TensorFlowFlexUNetEvaluator.py ./train_eval_infer.config
</pre>

Evaluation console output:<br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/evaluate_console_output_at_epoch45.png" width="1024" height="auto">
<br><br>Image-Segmentation-CVC-ClinicDB

<a href="./projects/TensorFlowFlexUNet/CVC-ClinicDB/evaluation.csv">evaluation.csv</a><br>
The loss (categorical_focal_dice_loss) on this CVC-ClinicDB/test was not low, but dice_coef_hybrid was high, as shown below.
<br>
<pre>
categorical_focal_dice_loss,0.0828
dice_coef_hybrid,0.96
</pre>
<br>

<h3>
5. Inference
</h3>
Please move to <b>./projects/TensorFlowFlexUNet/CVC-ClinicDB</b> folder
and run the following bat file to infer segmentation regions for images using the trained TensorFlowUNet model for CVC-ClinicDB.<br>
<pre>
./3.infer.bat
</pre>
This runs the following command.
<pre>
python ../../../src/TensorFlowFlexUNetInferencer.py ./train_eval_infer.config
</pre>
<hr>
<b>mini_test_images</b><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/mini_test_images.png" width="1024" height="auto"><br>
<b>mini_test_mask(ground_truth)</b><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/mini_test_masks.png" width="1024" height="auto"><br>

<hr>
<b>Inferred test masks</b><br>
<img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/asset/mini_test_output.png" width="1024" height="auto"><br>
<br>
<hr>
<b>Enlarged images and masks for CVC-ClinicDB Images of 256x256 pixels</b><br>
As shown below, the inferred masks look similar to the ground truth masks except for the first and ixth cases.<br>
<br>
<table>
<tr>
<th width="320" height="auto">Image</th>
<th width="320" height="auto">Mask (ground_truth)</th>
<th width="320" height="auto">Inferred-mask</th>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/10013.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/10013.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/10013.png" width="320" height="auto"></td>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/10408.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/10408.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/10408.png" width="320" height="auto"></td>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/rotated_270_10383.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/rotated_270_10383.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/rotated_270_10383.png" width="320" height="auto"></td>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/rotated_270_10410.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/rotated_270_10410.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/rotated_270_10410.png" width="320" height="auto"></td>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/rotated_270_10554.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/rotated_270_10554.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/rotated_270_10554.png" width="320" height="auto"></td>
</tr>
<tr>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/images/rotated_270_10584.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test/masks/rotated_270_10584.png" width="320" height="auto"></td>
<td><img src="./projects/TensorFlowFlexUNet/CVC-ClinicDB/mini_test_output/rotated_270_10584.png" width="320" height="auto"></td>
</tr>
</table>
<hr>
<br>
<h3>
References
</h3>
<b>1. TensorFlow-FlexUNet-Image-Segmentation-CVC-ColonDB</b><br>
Toshiyuki Arai<br>
<a href="https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-CVC-ColonDB">
https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-CVC-ColonDB
</a>
<br><br>
<b>2. TensorFlow-FlexUNet-Image-Segmentation-Colonoscopy-Child-Polyp</b><br>
Toshiyuki Arai<br>
<a href="https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Colonoscopy-Child-Polyp">
https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Colonoscopy-Child-Polyp
</a>
<br><br>
<b>3. TensorFlow-FlexUNet-Image-Segmentation-Sessile-Polyp </b><br>
Toshiyuki Arai<br>
<a href="https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Sessile-Polyp">
https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Sessile-Polyp
</a>
<br><br>
<b>4. TensorFlow-FlexUNet-Image-Segmentation-Multiclass-Gastrointestinal-Disease </b><br>
Toshiyuki Arai<br>
<a href="https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Multiclass-Gastrointestinal-Disease">
https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Multiclass-Gastrointestinal-Disease
</a>
<br><br>
<b>5. TensorFlow-FlexUNet-Image-Segmentation-Model</b><br>
Toshiyuki Arai<br>
<a href="https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Model">
https://github.com/sarah-antillia/TensorFlow-FlexUNet-Image-Segmentation-Model
</a>
<br><br>
