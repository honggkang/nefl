---
title: Results
layout: home
nav_order: 3
---


Results of NeFL with five submodels and SOTA baselines on five datasets under IID settings. We report test performance including Top-1 classification accuracies (%) for the worst-case submodel and the average performance over five submodels.

<table>
<tbody>
<tr><th rowspan=3>Model</th>
<th rowspan=3>Method</th>
<th colspan=2>CIFAR-10</th>
<th colspan=2>CIFAR-100</th>
<th colspan=2>CINIC-10</th>
<th colspan=2>SVHN</th></tr>
<tr><th>Worst</th><th>Avg</th><th>Worst</th><th>Avg</th><th>Worst</th><th>Avg</th><th>Worst</th><th>Avg</th></tr>
<tr></tr>
<tr><td rowspan=5>ResNet18</td>
<td>HeteroFL</td><td>80.62</td><td>84.26</td><td>41.33</td><td>47.09</td><td>67.55</td><td>70.40</td><td>91.82</td><td>93.46</td></tr>
<tr><td>FjORD</td><td>85.12</td><td>87.32</td><td>49.29</td><td>52.67</td><td>71.95</td><td>74.98</td><td>94.31</td><td>93.97</td></tr>
<tr><td>DepthFL</td><td>64.80</td><td>82.44</td><td>31.68</td><td>49.56</td><td>54.51</td><td>71.42</td><td>91.54</td><td>93.97</td></tr>
<tr><td>ScaleFL</td><td>79.47</td><td>85.18</td><td>41.00</td><td>49.76</td><td>70.55</td><td>73.85</td><td>93.15</td><td>94.53</td></tr>
<tr><td><strong>NeFL(ours)</strong></td><td><strong>87.71</strong></td><td><strong>89.02</strong></td><td><strong>55.22</strong></td><td><strong>56.26</strong></td><td><strong>75.02</strong></td><td><strong>76.68</strong></td><td><strong>94.72</strong></td><td><strong>95.22</strong></td></tr>
<tr><td rowspan=5>ResNet34</td>
<td>HeteroFL</td><td>79.51</td><td>83.16</td><td>34.96</td><td>39.75</td><td>67.39</td><td>69.62</td><td>89.86</td><td>92.39</td></tr>
<tr><td>FjORD</td><td>85.12</td><td>87.36</td><td>47.59</td><td>50.7</td><td>71.58</td><td>74.19</td><td>93.83</td><td>94.63</td></tr>
<tr><td>DepthFL</td><td>25.73</td><td>75.30</td><td>14.51</td><td>46.79</td><td>32.05</td><td>67.04</td><td>74.33</td><td>89.96</td></tr>
<tr><td>ScaleFL</td><td>54.72</td><td>81.05</td><td>22.62</td><td>46.41</td><td>49.69</td><td>69.43</td><td>86.46</td><td>93.21</td></tr>
<tr><td><strong>NeFL(ours)</strong></td><td><strong>87.71</strong></td><td><strong>89.02</strong></td><td><strong>55.22</strong></td><td><strong>56.26</strong></td><td><strong>75.02</strong></td><td><strong>76.68</strong></td><td><strong>94.72</strong></td><td><strong>95.22</strong></td></tr>
</tbody>
</table>



Results of NeFL utilizing <strong>pre-trained</strong> models as initial weights for CIFAR-10 dataset under <strong>IID</strong> (left) and <strong>non-IID</strong> (right) settings. Numbers in parentheses denote the performance difference compared to scratch, with <span style="color:blue">blue</span> indicating improvement from pretraining, and <span style="color:red">red</span> indicating degradation.
<table>
<tbody>
<tr><th rowspan=3>Model</th>
<th rowspan=3>Method</th>
<th colspan=2>IID</th>
<th colspan=2>non-IID</th></tr>
<tr><th>Worst</th><th>Avg</th><th>Worst</th><th>Avg</th></tr>
<tr></tr>
<tr><td rowspan=5>Pre-trained<br>ResNet18</td>
<td>HeteroFL</td><td>78.26<span style="color:red">(&downarrow;2.36)</span></td><td>84.48<span style="color:blue">(&uparrow;0.22)</span></td><td>71.95<span style="color:red">(&downarrow;4.30)</span></td><td>76.17<span style="color:red">(&downarrow;3.94)</span></td></tr>
<tr><td>FjORD</td><td>86.37<span style="color:blue">(&uparrow;1.25)</span></td><td>88.91<span style="color:blue">(&uparrow;1.59)</span></td><td>81.81<span style="color:blue">(&uparrow;6.00)</span></td><td>81.96<span style="color:blue">(&uparrow;3.97)</span></td></tr>
<tr><td>DepthFL</td><td>47.76<span style="color:red">(&downarrow;17.04)</span></td><td>82.86<span style="color:blue">(&uparrow;0.42)</span></td><td>39.78<span style="color:red">(&downarrow;19.83)</span></td><td>67.71<span style="color:red">(&downarrow;9.18)</span></td></tr>
<tr><td>ScaleFL</td><td>79.34<span style="color:red">(&downarrow;0.13)</span></td><td>86.16<span style="color:blue">(&uparrow;0.98)</span></td><td>69.47<span style="color:blue">(&uparrow;6.00)</span></td><td>78.01<span style="color:red">(&downarrow;0.48)</span></td></tr>
<tr><td><strong>NeFL(ours)</strong></td><td><strong>88.61</strong><span style="color:blue">(&uparrow;1.75)</span></td><td><strong>89.60</strong><span style="color:blue">(&uparrow;1.72)</span></td><td><strong>82.91</strong><span style="color:blue">(&uparrow;1.65)</span></td><td><strong>85.85</strong><span style="color:blue">(&uparrow;4.14)</span></td></tr>
<tr><td rowspan=5>Pre-trained<br>ResNet34</td>
<td>HeteroFL</td><td>79.97<span style="color:blue">(&uparrow;0.46)</span></td><td>84.34<span style="color:blue">(&uparrow;1.18)</span></td><td>72.33<span style="color:red">(&downarrow;3.70)</span></td><td>78.20<span style="color:red">(&downarrow;1.43)</span></td></tr>
<tr><td>FjORD</td><td>87.08<span style="color:blue">(&uparrow;1.96)</span></td><td>89.37<span style="color:blue">(&uparrow;2.01)</span></td><td>78.20<span style="color:blue">(&uparrow;3.50)</span></td><td>78.90<span style="color:blue">(&uparrow;2.89)</span></td></tr>
<tr><td>DepthFL</td><td>52.08<span style="color:blue">(&uparrow;26.35)</span></td><td>83.63<span style="color:blue">(&uparrow;8.33)</span></td><td>42.09<span style="color:blue">(&uparrow;11.67)</span></td><td>79.86<span style="color:blue">(&uparrow;9.10)</span></td></tr>
<tr><td>ScaleFL</td><td>67.66<span style="color:blue">(&uparrow;12.94)</span></td><td>85.77<span style="color:blue">(&uparrow;4.72)</span></td><td>52.59<span style="color:blue">(&uparrow;20.25)</span></td><td>78.29<span style="color:blue">(&uparrow;5.89)</span></td></tr>
<tr><td><strong>NeFL(ours)</strong></td><td><strong>88.36</strong><span style="color:blue">(&uparrow;0.65)</span></td><td><strong>91.14</strong><span style="color:blue">(&uparrow;2.12)</span></td><td><strong>83.62</strong><span style="color:blue">(&uparrow;2.86)</span></td><td><strong>86.48</strong><span style="color:blue">(&uparrow;3.18)</span></td></tr>
</tbody>
</table>
<!-- <table align="center" width=800px border="1" style="border-collapse: collapse; border: 0.5px solid black; margin: auto; text-align: center">
    <caption>Results of NeFL for CIFAR-10 dataset under <b>IID</b> (left) and <b>non-IID</b> (right) settings are presented: Top-1 classification accuracies (%) for the worst-case submodel and the average of the performance of five submodels.</caption>
    <tr>
        <th rowspan="3"><b>Model</b></th>
        <th rowspan="3"><b>Method</b></th>
        <th colspan="2"><b>IID</b></th>
        <th colspan="2"><b>non-IID</b></th>
    </tr>
    <tr>
        <th><b>Worst</b></th>
        <th><b>Avg</b></th>
        <th><b>Worst</b></th>
        <th><b>Avg</b></th>
    </tr>
    <tr>
    </tr>
    <tr>
        <th rowspan="4">ResNet18</th>
        <td>HeteroFL</td>
        <td>80.62 (&plusmn; 0.24)</td>
        <td>84.26 (&plusmn; 1.95)</td>
        <td>76.25 (&plusmn; 1.05)</td>
        <td>80.11 (&plusmn; 2.03)</td>
    </tr>
    <tr>
        <td>FjORD</td>
        <td>85.12 (&plusmn; 0.22)</td>
        <td>87.32 (&plusmn; 1.21)</td>
        <td>75.81 (&plusmn; 5.65)</td>
        <td>77.99 (&plusmn; 6.50)</td>
    </tr>
    <tr>
        <td>DepthFL</td>
        <td>64.80 (&plusmn; 10.49)</td>
        <td>82.44 (&plusmn; 10.17)</td>
        <td>59.61 (&plusmn; 5.16)</td>
        <td>76.89 (&plusmn; 9.60)</td>
    </tr>
    <tr>
        <td><b>NeFL (ours)</b></td>
        <td><b>86.86 (&plusmn; 0.22)</b></td>
        <td><b>87.88 (&plusmn; 0.68)</b></td>
        <td><b>81.26 (&plusmn; 2.44)</b></td>
        <td><b>81.71 (&plusmn; 3.14)</b></td>
    </tr>
    <tr>
        <th rowspan="4">ResNet34</th>
        <td>HeteroFL</td>
        <td>79.51 (&plusmn; 0.44)</td>
        <td>83.16 (&plusmn; 1.96)</td>
        <td>76.03 (&plusmn; 1.34)</td>
        <td>79.63 (&plusmn; 5.24)</td>
    </tr>
    <tr>
        <td>FjORD</td>
        <td>85.12 (&plusmn; 0.25)</td>
        <td>87.36 (&plusmn; 1.19)</td>
        <td>74.70 (&plusmn; 3.66)</td>
        <td>76.01 (&plusmn; 5.24)</td>
    </tr>
    <tr>
        <td>DepthFL</td>
        <td>25.73 (&plusmn; 4.25)</td>
        <td>75.30 (&plusmn; 24.88)</td>
        <td>30.42 (&plusmn; 9.34)</td>
        <td>70.76 (&plusmn; 21.04)</td>
    </tr>
    <tr>
        <td><b>NeFL (ours)</b></td>
        <td><b>87.71 (&plusmn; 0.37)</b></td>
        <td><b>89.02 (&plusmn; 0.80)</b></td>
        <td><b>80.76 (&plusmn; 2.82)</b></td>
        <td><b>83.31 (&plusmn; 2.94)</b></td>
    </tr>
</table> -->