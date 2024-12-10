# Bonsai Conference 2024: Machine Learning session

| Day | Time | Moderators |
| --- | ---- | ---------- |
| Tuesday December 3 | 1pm -- 4pm | [Joaquin Rapela](../../participants/jRapela/) [Nicholas Guilbeault](../../participants/nGuilbeault) |

## Abstract

Typically, neuroscientists use Bonsai for acquisition but rely on other
programming languages, such as Python and MATLAB, for offline processing with
machine learning (ML) algorithms. Recently, we started adding ML functionality
to Bonsai by developing packages that interface with powerful ML tools for
online data analysis. In this session we will discuss the basics of online
probabilistic machine learning, and introduce a new package Bonsai.ML which
aims at extending Bonsai with online machine learning techniques, such as
linear dynamical systems, hidden Markov models, online Bayesian linear
regression and neural decoding models. We will provide examples and tutorials
throughout the session and end with a discussion on the future of machine
learning in Bonsai.

## Summary

In the Introduction section Joaquin talked about the origins and motivations for the Bonsai.ML package. He mentioned that the initial focus of Bonsai.ML will be on **Bayesian models** for **Neuroscience applications** that can **process online** potentially infinite and **non-stationary** datastreams. Bonsai.ML aims to use **reactive inference methods** that allow continuous inference in scenarios where new data sources are added or removed from the environment.

Joaquin started by describing a Bonsai workflow for [online Bayesian linear regression](https://github.com/joacorapela/bonsai-oblrSimpleLinearRegressionDemo), applied to the perform simple linear regression. Then he showed that the previous workflow could be modified to address a more elaborate use case, the [estimation of visual receptive fields from responses of neurons to natural stimuli](https://github.com/joacorapela/bonsai-oblr-corticalSimpleCellEx) (Figure 1).

<figure>

  <a href="https://github.com/joacorapela/bonsai-oblr-corticalSimpleCellEx"><img src="https://github.com/joacorapela/bonsai-oblr-corticalSimpleCellEx/raw/master/figures/workflow.png" width="450" /></a>

  <figcaption>Fig.1 - Bonsai workflow for visual receptive field estimation</figcaption>

</figure>

Online Bayesian linear regression allows to process potentially infinite datastreams. However, it requires that the statistics of the data does not change with time. To perform linear regression on non-stationary datastreams Joaquin presented a [Bonsai workflow using the recursive least squares algorithm](https://github.com/joacorapela/bonsai-rlsSimpleLinearRegression) and showed how this algorithm was robust to dynamic changes in the data statistics.

A main goal for the Bonsai.ML package is to enable machine learning developers to develop in Bonsai. To this end, Nick presented the Bonsai - Python scripting package which integrates the standard CPython engine into Bonsai. Nick discussed the history of the package, the current state of the package and provided some examples for how to write simple Python programs in Bonsai. He also focused on discussing the current limitations of the package, which include the seperate installation steps, explicit thread management of the GIL, and converting data types between Python and .NET.

Following this, Nick discussed work towards integrating several Python-based packages into Bonsai for real-time analysis. The first package includes the [lds_python package](https://github.com/joacorapela/lds_python) which implements the Kalman Filter (KF) for online estimation of movement kinematics. The next package was the [ssm package](https://github.com/lindermanlab/ssm) for performing online estimation of discrete latent states using Hidden Markov Models (HMMs). He showcased a demo that used both of these packages in tandem on a freely behaving mouse video. The Kalman Filter was optimized online to infer the mouse's true velocity and acceleration. The model was able to forecast the mouse's kinematics into the future. The mouses velocity and acceleration were used to fit a HMM to infer the behavioral state of the animal and visualize it's trajectory through the behavioral state space.

Another demo showcased by Nick was using a trained point process decoder to infer a mouse's latent position from neural recordings online. In this demo, the model is trained offline to encode the joint distribution of the animal's linear position and neural activity from hippocampal tetrode recordings. The model can then be used to run inference online to decode position on the linear track from neural spikes.

Lastly, Nick demoed work integrating the TorchSharp C# package into Bonsai, showing how it can be used for linear regression, image classification and reinforcement learning.

The Bonsai.ML session concluded with an open discussion covering topics related to how to disseminate the package, potential good use cases for the package and the benefits of integrating TorchSharp into Bonsai.

## References

[Recording](https://ucl.zoom.us/rec/share/MWxQHOg_hFngvaNb_gt0kbyHWxT_wAaU1LZWToTsvLlnwksHu2Vq_CsAPSBxYQEA.JTzLG_cHFyyvg9Dw), password: t18N8=H^

Slides: [Introduction and Linear Regression](https://github.com/joacorapela/2024BonsaiConference-bonsai.ML-presentation/blob/master/presentation/bonsaiML.pdf)

Slides: [Python Scripting](https://neurogears.sharepoint.com/:b:/r/sites/BonsaiFoundation/Shared%20Documents/Conference%202024/Slides/Bonsai%20-%20Python%20Scripting%20Slides.pdf?csf=1&web=1&e=HdMUOb)
