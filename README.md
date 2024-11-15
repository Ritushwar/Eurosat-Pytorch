<h1>EuroSat Land Cover Classification Using PyTorch</h1>
  <br>
<p style="font-size:20px">This   project leverage PyTorch to classify satellite images from the EuroSat dataset. It is the dataset and deep learning benchmark for land use and land cover classification. The dataset is based on Sentinel-2 satellite images covering 13 spectral bands and consisting out of 10 classes with in total 27,000 labeled and geo-referenced images. </p>

<h2>Dataset Information <h2>
<ul style="font-size:20px">
   <li>Source: <a href="https://pytorch.org/vision/main/generated/torchvision.datasets.EuroSAT.html#torchvision.datasets.EuroSAT">EuroSat Dataset</a></li>
   <li>Classes: 10 land cover categories(eg:Forests, Residental, Industrial etc)</li>
   <li>Input: 64x64 RGB satellite image</li>
</ul>

<h2>Model Architecture</h2>
<ul style="font-size:20px">
  <li>FrameWork: PtTorch</li>
  <li>Model Description: I made two version of a simple fully connected neural network.
       <ul style="font-size:18px">
          <li>EuroSatV0
              <p style="font-size:16px">This architecture is lightweight and ideal for smaller datsets or as a baseline model for quick experiment. It does not involve convolutional layers, focusing insted on direct connection</p>
              <ul>
                  <li>Input Layer
                     <ul>
                       <li>Input Shape:<p>Flattened input vector from the image(64x64x3=12288)</p></li>
                     </ul>
                  </li>
                  <li>Hidden Layer
                      <ul>
                         <li>A single fully connected layer with hidden_units neurons</li>
                         <li>Activation function: ReLU</li>
                      </ul>
                    </li>
                    <li> Output Layer
                        <ul>
                            <li>A fully connected layer mapping the hidden units to output shape(for 10 classes)</li>
                        </ul>
                    </li>
                    <li>Model Flow
                        <ul>
                            <li>Flatten: Convert the input image into 1D vector.</li>
                            <li>Dense Layer: Learns intermediate representations.
                            </li>
                            <li>Activations: Applies non-linearity using ReLu.
                            </li>
                            <li>Output Layer: Produce logits for each class</li>
                            </ul>
                    </li>
       </ul>
  </li>
  <li>EuroSatV1
  <p style="font-size:16px">It is an enhanced version of fully connected neural network design for multi-class classification task.</p>
    <ul>
        <li>Input Layer
            <ul>
                <li>Input Shape: Flatten input vector from the image(64x64x3=12288)
            </ul>
        </li>
        <li>Hidden Layers
            <ul>
                <li>First Hidden Layer: Contains 32 neurons with ReLU activation.</li>
                <li>Second Hidden layer: Contains 16 neurons with ReLU activations</li>
            </ul>
        </li>
        <li> Output Layer
            <ul>
                <li>Maps 16 to the output shape(10 classes)
                </li>
                <li>Output probabilities for each class using a softmax activation function applied to logits</li>
            </ul>
        </li>
        <li>Model Flow
            <ul>
                <li>Flatten: Converts the input image into a 1D vector</li>
                <li>Dense Layers: Learn intermediate representation through two fully connected layers with non-linearity</li>
                <li>Softmax: Converts logits to probabilities fro multi-class classifications</li>
            </ul>
        </li>
    </ul>
  </li>
</ul>
<h2>Training Details</h2>
<ul>
    <li>Hardware Used: I trained the model on Colab using GPU.</li>
    <li>Training Epochs: 150</li>
    <li>Optimizer: SGD(Stochastic Gradient Descent)</li>
    <li>Evaluation:
        <ul>
            <li>EuroSatV0: This model achieve 45.27 training accuracy and 37.28 testing accuracy.
            </li>
            <li>EuroSatV1: This model achieve 51.07 training accuracy and 46.40 testing accuracy.</li>
        </ul>
    </li>
</ul>
<h2>Acknowledgements</h2>
<p>This project uses the EuroSat datsets and draws inspiration from the official PyTorch tutorials. 

<h2>License</h2>
<p>This project is licensed under the MIT License. See the file for more details</p>