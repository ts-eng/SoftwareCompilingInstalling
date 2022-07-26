
# Build ColossalAI in windows 10 with VS2019

## ERROR 1

  D:/Program Files (x86)/Microsoft Visual Studio/2019/BuildTools/VC/Tools/MSVC/14.28.29333/include\type_traits(1065): error: static assertion failed with "You've instantiated std::aligned_storage<Len, Align> with an extended alignment (in other words, Align > alignof(max_align_t)). Before VS 2017 15.8, the member "type" would non-conformingly have an alignment of only alignof(max_align_t). VS 2017 15.8 was fixed to handle this correctly, but the fix inherently changes layout and breaks binary compatibility (*only* for uses of aligned_storage with extended alignments). Please define either (1) _ENABLE_EXTENDED_ALIGNED_STORAGE to acknowledge that you understand this message and that you actually want a type with an extended alignment, or (2) _DISABLE_EXTENDED_ALIGNED_STORAGE to silence this message and get the old non-conforming behavior."

打开ColossalAI\setup.py, 将'-D_ENABLE_EXTENDED_ALIGNED_STORAGE'追加到extra_cuda_flags和extra_cxx_flags列表中.

## ERROR 2


  C:/Users/ZHIWEI~1.ZEN/AppData/Local/Temp/pip-req-build-qoj_tn76/colossalai/kernel/cuda_native/csrc/multi_tensor_scale_kernel.cu(68): error: calling a __host__ function("isfinite< ::c10::Half> ") from a __device__ function("ScaleFunctor< ::c10::Half, float> ::operator ()") is not allowed

  C:/Users/ZHIWEI~1.ZEN/AppData/Local/Temp/pip-req-build-qoj_tn76/colossalai/kernel/cuda_native/csrc/multi_tensor_scale_kernel.cu(68): error: identifier "isfinite< ::c10::Half> " is undefined in device code
`

打开ColossalAI\colossalai\kernel\cuda_native\csrc\multi_tensor_scale_kernel.cu, 将两处isfinite(r_in[ii])替换为isfinite(static_cast<float>(r_in[ii])).


## ERROR 3

C:/Users/ZHIWEI~1.ZEN/AppData/Local/Temp/pip-req-build-rkgk6nkq/colossalai/kernel/cuda_native/csrc/kernels/normalize_kernels.cu(86): error: identifier "uint" is undefined

打开ColossalAI\colossalai\kernel\cuda_native\csrc\kernels\normalize_kernels.cu, 将uint替换为unsigned int.

## ERROR 4

C:/Users/ZHIWEI~1.ZEN/AppData/Local/Temp/pip-req-build-qi8d3cad/colossalai/kernel/cuda_native/csrc/kernels/normalize_kernels.cu(10): error: identifier "LN_EPSILON" is undefined in device code

参考: https://stackoverflow.com/questions/39771489/nvcc-compiler-recognizes-static-constexpr-as-undefined-in-device-code
打开ColossalAI\colossalai\kernel\cuda_native\csrc\kernels\normalize_kernels.cu, 将const float LN_EPSILON = 1e-8f改为__constant__ float LN_EPSILON = 1e-8f

  C:/Users/ZHIWEI~1.ZEN/AppData/Local/Temp/pip-req-build-9v8ymakc/colossalai/kernel/cuda_native/csrc/kernels/include\block_reduce.h(246): error: identifier "REDUCE_FLOAT_INF_NEG" is undefined in device code

打开ColossalAI\colossalai\kernel\cuda_native\csrc\kernels\include\block_reduce.h, 将const float REDUCE_FLOAT_INF_NEG = -100000000.f改为__constant__ float REDUCE_FLOAT_INF_NEG = -100000000.f

  C:/Users/ZHIWEI~1.ZEN/AppData/Local/Temp/pip-req-build-9v8ymakc/colossalai/kernel/cuda_native/csrc/kernels/softmax_kernels.cu(193): error: identifier "EPSILON" is undefined in device code

打开ColossalAI\colossalai\kernel\cuda_native\csrc\kernels\softmax_kernels.cu, 将const float EPSILON = 1e-8f改为__constant__ float EPSILON = 1e-8f
