---
title: Details
layout: home
nav_order: 4
---

## Training details

- Trained by communication rounds of 500 (100 for SVHN)
- 100 clients, fraction rate of 0.1 each round (i.e., 10 clients each round)
- Local batch size of 32 and local epochs of 5
- Optimizer: SGD with learning rate of 0.1 without momentum and weight decay
- Learning rate decreased by a factor of 0.1 at halfway point and 3/4 of the total communication rounds

- System heterogeneity: each client trained one of the submodels in each iteration.
  - One with five submodels (<i>N<sub>s</sub></i>=5, where γ = [γ<sub>1</sub>, γ<sub>2</sub>, γ<sub>3</sub>, γ<sub>4</sub>, γ<sub>5</sub>] = [0.2, 0.4, 0.6, 0.8, 1]).
    - The clients were evenly distributed across tiers corresponding to the number of submodels.
    - A client in tier x selects a submodel uniformly from the range [max(γ<sub>1</sub>, γ<sub>x-2</sub>), min(γ<sub>x+2</sub>, γ<sub>5</sub>)] during each iteration due to dynamically varying system availability.
- Statistical heterogeneity: label distribution skew following the Dirichlet distribution with a concentration parameter of 0.5.



## Details on architectures of submodels
### [[Example]]

Please note that the widthwise scaling (𝛾<sub>W</sub>) is uniformly applied across all blocks.

Consider Model index 1 and 2 in NeFL-D on ResNet18. The architecture is illustrated as follows:

<img src="./resources/submodel_ex.png" alt="drawing" width="600"/>

### ResNet18

Details of 𝛾 of NeFL-D on ResNet18
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="4">NeFL-D (ResNet18)</th>
    </tr>
    <tr>
      <th>Layer 1 (64)</th>
      <th>Layer 2 (128)</th>
      <th>Layer3 (256)</th>
      <th>Layer 4 (512)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.20</td><td>1</td><td>0.20</td><td>1,1</td><td>0,0</td><td>1,1</td><td>0,0</td></tr>
    <tr><td>2</td><td>0.38</td><td>1</td><td>0.38</td><td>1,0</td><td>0,0</td><td>1,0</td><td>1,0</td></tr>
    <tr><td>3</td><td>0.57</td><td>1</td><td>0.57</td><td>1,1</td><td>1,1</td><td>1,1</td><td>1,0</td></tr>
    <tr><td>4</td><td>0.81</td><td>1</td><td>0.81</td><td>1,0</td><td>1,1</td><td>0,0</td><td>1,1</td></tr>
    <tr><td>5</td><td>1</td><td>1</td><td>1</td><td>1,1</td><td>1,1</td><td>1,1</td><td>1,1</td></tr>
  </tbody>
</table>
<br>
Details of 𝛾 of NeFL-WD on ResNet18
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="4">NeFL-WD (ResNet18)</th>
    </tr>
    <tr>
      <th>Layer 1 (64)</th>
      <th>Layer 2 (128)</th>
      <th>Layer3 (256)</th>
      <th>Layer 4 (512)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.20</td><td>0.34</td><td>0.58</td><td>1,1</td><td>1,1</td><td>1,1</td><td>1,0</td></tr>
    <tr><td>2</td><td>0.4</td><td>0.4</td><td>1</td><td>1,1</td><td>1,1</td><td>1,1</td><td>1,1</td></tr>
    <tr><td>3</td><td>0.6</td><td>0.6</td><td>1</td><td>1,1</td><td>1,1</td><td>1,1</td><td>1,1</td></tr>
    <tr><td>4</td><td>0.8</td><td>0.8</td><td>1</td><td>1,1</td><td>1,1</td><td>1,1</td><td>1,1</td></tr>
    <tr><td>5</td><td>1</td><td>1</td><td>1</td><td>1,1</td><td>1,1</td><td>1,1</td><td>1,1</td></tr>
  </tbody>
</table>

### ResNet34

Details of 𝛾 of NeFL-D on ResNet34
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="4">NeFL-D (ResNet34)</th>
    </tr>
    <tr>
      <th>Layer 1 (64)</th>
      <th>Layer 2 (128)</th>
      <th>Layer 3 (256)</th>
      <th>Layer 4 (512)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.23</td><td>1</td><td>0.23</td><td>1,0,0</td><td>1,0,0,0</td><td>1,0,0,0,0,0</td><td>1,0,0</td></tr>
    <tr><td>2</td><td>0.39</td><td>1</td><td>0.39</td><td>1,1,1</td><td>1,1,1,1</td><td>1,1,0,0,0,1</td><td>1,0,0</td></tr>
    <tr><td>3</td><td>0.61</td><td>1</td><td>0.61</td><td>1,1,1</td><td>1,1,1,1</td><td>1,1,0,0,0,1</td><td>1,0,1</td></tr>
    <tr><td>4</td><td>0.81</td><td>1</td><td>0.81</td><td>1,1,1</td><td>1,0,0,1</td><td>1,1,0,0,0,1</td><td>1,1,1</td></tr>
    <tr><td>5</td><td>1</td><td>1</td><td>1</td><td>1,1,1</td><td>1,1,1,1</td><td>1,1,1,1,1,1</td><td>1,1,1</td></tr>
  </tbody>
</table>
<br>
Details of 𝛾 of NeFL-WD on ResNet34
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="4">NeFL-WD (ResNet34)</th>
    </tr>
    <tr>
      <th>Layer 1 (64)</th>
      <th>Layer 2 (128)</th>
      <th>Layer 3 (256)</th>
      <th>Layer 4 (512)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.20</td><td>0.38</td><td>0.53</td><td>1,1,1</td><td>1,0,0,1</td><td>1,0,0,0,0,1</td><td>1,0,1</td></tr>
    <tr><td>2</td><td>0.40</td><td>0.63</td><td>0.64</td><td>1,1,1</td><td>1,0,0,1</td><td>1,1,1,0,0,1</td><td>1,0,1</td></tr>
    <tr><td>3</td><td>0.60</td><td>0.77</td><td>0.78</td><td>1,1,1</td><td>1,1,1,1</td><td>1,1,1,1,0,1</td><td>1,0,1</td></tr>
    <tr><td>4</td><td>0.80</td><td>0.90</td><td>0.89</td><td>1,1,1</td><td>1,1,1,1</td><td>1,1,1,0,0,1</td><td>1,1,1</td></tr>
    <tr><td>5</td><td>1</td><td>1</td><td>1</td><td>1,1,1</td><td>1,1,1,1</td><td>1,1,1,1,1,1</td><td>1,1,1</td></tr>
  </tbody>
</table>

### ResNet56

Details of 𝛾 of NeFL-D on ResNet56
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="3">NeFL-D (ResNet56)</th>
    </tr>
    <tr>
      <th>Layer 1 (16)</th>
      <th>Layer 2 (32)</th>
      <th>Layer 3 (64)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.2</td><td>1</td><td>0.2</td><td>1, 1, 0, 0, 0, 0, 0, 0, 0</td><td>1, 1, 0, 0, 0, 0, 0, 0, 0</td><td>1, 1, 0, 0, 0, 0, 0, 0, 0</td></tr>
    <tr><td>2</td><td>0.4</td><td>1</td><td>0.4</td><td>1, 1, 1, 0, 0, 0, 0, 0, 0</td><td>1, 1, 1, 0, 0, 0, 0, 0, 0</td><td>1, 1, 1, 1, 0, 0, 0, 0, 0</td></tr>
    <tr><td>3</td><td>0.6</td><td>1</td><td>0.6</td><td>1, 1, 1, 1, 0, 0, 0, 0, 0</td><td>1, 1, 1, 1, 0, 0, 0, 0, 0</td><td>1, 1, 1, 1, 1, 1, 0, 0, 0</td></tr>
    <tr><td>4</td><td>0.8</td><td>1</td><td>0.8</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 0</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0</td></tr>
    <tr><td>5</td><td>1</td><td>1</td><td>1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1</td></tr>    
  </tbody>
</table>

Details of 𝛾 of NeFL-WD on ResNet56
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="3">NeFL-WD (ResNet56)</th>
    </tr>
    <tr>
      <th>Layer 1 (16)</th>
      <th>Layer 2 (32)</th>
      <th>Layer 3 (64)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.2</td><td>0.46</td><td>0.43</td><td>1, 1, 1, 1, 0, 0, 0, 0, 0</td><td>1, 1, 1, 1, 0, 0, 0, 0, 0</td><td>1, 1, 1, 1, 0, 0, 0, 0, 0</td></tr>
    <tr><td>2</td><td>0.4</td><td>0.61</td><td>0.66</td><td>1, 1, 1, 1, 1, 1, 0, 0, 0</td><td>1, 1, 1, 1, 1, 1, 0, 0, 0</td><td>1, 1, 1, 1, 1, 1, 0, 0, 0</td></tr>
    <tr><td>3</td><td>0.6</td><td>0.77</td><td>0.77</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0</td></tr>
    <tr><td>4</td><td>0.8</td><td>0.90</td><td>89</td><td>1, 1, 1, 1, 1, 1, 1, 1, 0</td><td>1, 1, 1, 1, 1, 1, 1, 1, 0</td><td>1, 1, 1, 1, 1, 1, 1, 1, 0</td></tr>
    <tr><td>5</td><td>1</td><td>1</td><td>1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1</td></tr>
  </tbody>
</table>

### ReNet110

Details of 𝛾 of NeFL-D on ResNet110
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="3">NeFL-D (ResNet110)</th>
    </tr>
    <tr>
      <th>Layer 1 (16)</th>
      <th>Layer 2 (32)</th>
      <th>Layer 3 (64)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.2</td><td>1</td><td>0.20</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0</td><td>1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0</td><td>1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0</td></tr>
    <tr><td>2</td><td>0.4</td><td>1</td><td>0.40</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0</td></tr>
    <tr><td>3</td><td>0.6</td><td>1</td><td>0.60</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0</td></tr>
    <tr><td>4</td><td>0.8</td><td>1</td><td>0.80</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0</td></tr>
    <tr><td>5</td><td>1</td><td>1</td><td>1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1</td></tr>
  </tbody>
</table>

Details of 𝛾 of NeFL-WD on ResNet110
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>    
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="3">NeFL-WD (ResNet110)</th>
    </tr>
    <tr>
      <th>Layer 1 (16)</th>
      <th>Layer 2 (32)</th>
      <th>Layer 3 (64)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.2</td><td>0.46</td><td>0.44</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1</td><td>1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 1</td></tr>
    <tr><td>2</td><td>0.4</td><td>0.60</td><td>0.66</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 1</td></tr>
    <tr><td>3</td><td>0.6</td><td>0.77</td><td>0.77</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 1</td></tr>
    <tr><td>4</td><td>0.8</td><td>0.90</td><td>0.89</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 1</td></tr>
    <tr><td>5</td><td>1</td><td>1</td><td>1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1</td></tr>
  </tbody>
</table>

### Wide ResNet

Details of 𝛾 of NeFL on Wide ResNet101_2
<table>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th colspan="4">NeFL-D (Wide ResNet101_2)</th>
    </tr>
    <tr>
      <th>Layer 1 (128)</th>
      <th>Layer 2 (256)</th>
      <th>Layer 3 (512)</th>
      <th>Layer 4 (1024)</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.5</td><td>1</td><td>0.51</td><td>1, 1, 1</td><td>1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0, 0</td><td>1, 1, 0</td></tr>
    <tr><td>2</td><td>0.75</td><td>1</td><td>0.75</td><td>1, 1, 1</td><td>1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0, 0, 0, 0</td><td>1, 1, 1</td></tr>
    <tr><td>3</td><td>1</td><td>1</td><td>1</td><td>1, 1, 1</td><td>1, 1, 1, 1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1</td><td>1, 1, 1</td></tr>
  </tbody>
</table>

### ViT-B/16

<table>
  <caption>Details of $\bm{\gamma}$ of NeFL-D and NeFL-W on ViT-B/16</caption>
  <thead>
    <tr>
      <th rowspan="2">Model<br>index</th>
      <th rowspan="2">Model size<br>𝛾</th>
      <th rowspan="2">𝛾<sub>W</sub></th>
      <th rowspan="2">𝛾<sub>D</sub></th>
      <th>NeFL-D (ViT-B/16)</th>
    </tr>
    <tr>
      <th>Block</th>
    </tr>
  </thead>
  <tbody>
    <tr><td>1</td><td>0.5</td><td>1</td><td>0.50</td><td>1, 1, 1, 1, 1, 1, 0, 0, 0, 0, 0, 0</td></tr>
    <tr><td>2</td><td>0.75</td><td>1</td><td>0.75</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 0, 0, 0</td></tr>
    <tr><td>3</td><td>1</td><td>1</td><td>1</td><td>1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1, 1</td></tr>
  </tbody>
</table>


## Pre-trained models (trained on ImageNet-1k)

### ResNet18/34
- Trained by epochs of 90, batch size of 32
- Optimizer: SGD with learning rate of 0.1, momentum of 0.9, and weight decay of 0.0001
- Learning rate decreased by a factor of 0.1 every 30 epochs

### Wide ResNet101_2
- Trained by epochs of 90, batch size of 32
- Optimizer: SGD with learning rate of 0.1, momentum of 0.9, and weight decay of 0.0001
- Learning scheduler: Cosine learning rate with warming up restarts for 256 epochs

### ViT-B/16
- Trained by epochs of 300, batch size of 512
- Optimizer: AdamW with learning rate of 0.003 and weight decay of 0.3
- Learning scheduler: Cosine annealing after linear warmup method with decay of 0.033 for 30 epochs
- Augmentation:
  - Random augmentation
  - Random mixup with alpha=0.2
  - Cutmix with alpha=1
  - Repeated augmentation
  - Label smoothing of 0.11
  - Gradient norm clipping to 1
  - Model exponential moving average (EMA)

## Comparing Wide ResNet101_2 & ViT-B/16
### Training details
- Trained by communication rounds of 100
- 10 clients, fraction rate of 1 each round (i.e., 10 clients each round)
- Local batch size of 32 and local epochs of 1
- Optimizer: SGD with learning rate of 0.1 without momentum and weight decay
- Cosine annealing learning rate scheduling with 500 steps of warmup and an initial learning rate of 0.03
- Input images are resized to a size of 256x256 and randomly cropped to a size of 224x224 with a padding size of 28 28

----
[Example]: https://github.com/honggkang/nested-federated-learning/blob/master/submodel_param_flop.xlsx