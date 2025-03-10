# Sentis

The ML-Agents Toolkit allows you to use pre-trained neural network models inside
your Unity games. This support is possible thanks to the
[Sentis](https://docs.unity3d.com/Packages/com.unity.sentis@latest/index.html)
(codenamed Sentis). Sentis uses
[compute shaders](https://docs.unity3d.com/Manual/class-ComputeShader.html) to
run the neural network within Unity.

## Supported devices

See the Sentis documentation for a list of the
[supported platforms](https://docs.unity3d.com/Manual/PlatformSpecific.html).

Scripting Backends : Sentis is generally faster with
**IL2CPP** than with **Mono** for Standalone builds. In the Editor, It is not
possible to use Sentis with GPU device selected when Editor
Graphics Emulation is set to **OpenGL(ES) 3.0 or 2.0 emulation**. Also there
might be non-fatal build time errors when target platform includes Graphics API
that does not support **Unity Compute Shaders**.

## Using Sentis

When using a model, drag the model file into the **Model** field in the
Inspector of the Agent. Select the **Inference Device** : CPU or GPU you want to
use for Inference.

**Note:** For most of the models generated with the ML-Agents Toolkit, CPU will
be faster than GPU. You should use the GPU only if you use the ResNet visual
encoder or have a large number of agents with visual observations.

# Unsupported use cases
## Externally trained models
The ML-Agents Toolkit only supports the models created with our trainers. Model
loading expects certain conventions for constants and tensor names. While it is
possible to construct a model that follows these conventions, we don't provide
any additional help for this. More details can be found in
[TensorNames.cs](https://github.com/Unity-Technologies/ml-agents/blob/release_22_docs/com.unity.ml-agents/Runtime/Inference/TensorNames.cs)
and
[SentisModelParamLoader.cs](https://github.com/Unity-Technologies/ml-agents/blob/release_22_docs/com.unity.ml-agents/Runtime/Inference/SentisModelParamLoader.cs).

If you wish to run inference on an externally trained model, you should use
Sentis directly, instead of trying to run it through ML-Agents.

## Model inference outside of Unity
We do not provide support for inference anywhere outside of Unity. The `.onnx` files produced by training use the open format ONNX; if you wish to convert a `.onnx` file to another
format or run inference with them, refer to their documentation.
