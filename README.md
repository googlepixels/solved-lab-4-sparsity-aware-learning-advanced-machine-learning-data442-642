Download Link: https://assignmentchef.com/product/solved-lab-4-sparsity-aware-learning-advanced-machine-learning-data442-642
<br>
<h1>Exercise 1</h1>

Consider an unknown 2-sparse vector <em>θ</em><sub>0</sub>, which when measured with the sensing matrix

<strong>X </strong>

that is, of <strong>y </strong>= <strong>X</strong><em>θ</em><sub>0</sub>, gives <strong>y </strong>= [1<em>.</em>253<em>.</em>75]<sup>&gt;</sup>. Perform the following tasks in Python.

<ul>

 <li>Based on the pseudoinverse of <strong>X</strong>, compute <em>θ</em><sup>ˆ</sup><sub>2</sub>, which is the <em>`</em><sub>2 </sub>norm minimized solution. Next, check that this solution <em>θ</em><sup>ˆ</sup><sub>2 </sub>leads to zero estimation error (up to machine precision). Is <em>θ</em><sup>ˆ</sup><sub>2 </sub>a 2-space vector such as the true unknown vector <em>θ</em><sub>0</sub>?</li>

 <li>Solve the <em>`</em><sub>0 </sub>minimization task based on an exhaustive search for all possible 1- and 2sparse solutions and get the best one, <em>θ</em><sup>ˆ</sup><sub>0</sub>. Does <em>θ</em><sup>ˆ</sup><sub>0 </sub>lead to zero estimation error (up to machine precision)?</li>

 <li>Compute and compare the <em>`</em><sub>2 </sub>norms of <em>θ</em><sup>ˆ</sup><sub>2 </sub>and <em>θ</em><sup>ˆ</sup><sub>0</sub>. Which is the smaller one? Was this result expected?</li>

</ul>

<h1>Exercise 2: Image Denoising</h1>

A typical example in sparsity aware learning is the denoising problem. The problem in signal denoising is that instead of the actual signal samples, <strong>y</strong>˜, a noisy version of the corresponding observations, <strong>y</strong>, is available; that is, <strong>y </strong>= <strong>y</strong>˜ + <em>η</em>, where <em>η </em>is the vector of noise samples. Under the sparse modeling framework, the unknown signal <strong>y</strong>˜ is modeled as a sparse representation in terms of a specific known dictionary <strong>Ψ</strong>, that is, <strong>y</strong>˜ = <strong>Ψ</strong><em>θ</em>. Moreover, the dictionary is allowed to be redundant (overcomplete). Then the denoising procedure is realized in two steps. First, an estimate of the sparse representation vector, <em>θ</em>, is obtained via any LASSO formulation, and second, the estimate of the true signal is computed as <strong>y</strong>ˆ = <strong>Ψ</strong><em>θ</em><sup>ˆ</sup>.

For Exercise 2, you have to reproduce the the denoising results of the case study in Section 9.10. First, extract from the image all the possible sliding patches of size 12 × 12. Confirm that (256 − 12 + 1)<sup>2 </sup>= 60<em>,</em>025 patches in total are obtained. Next, a dictionary in which all the patches are sparsely represented needs to be designed. Specifically, the dictionary atoms are going to be those corresponding to the two-dimensional redundant DCT transform, and are obtained as follows

<ul>

 <li>Consider vectors <strong>d</strong><em><sub>i </sub></em>= [<em>d<sub>i,</sub></em><sub>1</sub><em>,d<sub>i,</sub></em><sub>2</sub><em>,…,d<sub>i,</sub></em><sub>12</sub>]<sup>&gt;</sup>, <em>i </em>= 0<em>,…,</em>13, being the sampled sinusoids of the form</li>

</ul>

<em>.</em>

Then make (12×14) matrix <strong>D</strong><sup>¯</sup>, having as columns the vectors <strong>d</strong><em><sub>i </sub></em>normalized to unit norm; <strong>D </strong>resembles a redundant DCT matrix.

<ul>

 <li>Construct the (12<sup>2 </sup>× 14<sup>2</sup>) dictionary <strong>Ψ </strong>according to <strong>Ψ </strong>= <strong>D </strong>⊗ <strong>D</strong>, where ⊗ denoted Kronecker product. Built in this way, the resulting atoms correspond to atoms related to the overcomplete 2D-DCT transform.</li>

</ul>

As a next step, denoise each image patch separately. In particular, assuming that <strong>y</strong><em><sub>i </sub></em>is the <em>i</em>th patch reshaped in column vector, estimate a sparse vector <em>θ<sub>i </sub></em>∈R<sup>196 </sup>and obtain the corresponding denoised vector as <strong>y</strong>ˆ<em><sub>i </sub></em>= <strong>Ψ</strong><em>θ</em><sup>ˆ</sup><em><sub>i</sub></em>. Finally, average the values of the overlapping patches in order to form the full denoised image.