# tensorflow-compiled-from-source
Contains Tensorflow 1.3.0 package compiled from source to use AVX, SSE4.1 and SSE4.2 instructions available on CPU

Follow below steps to compile from source root directory:

1) Configure giving no to all questions.
  $./configure                                                        
  
2) Choose python path (e.g. /usr/bin/python3) in configuration 

3) Run below command to build with AVX, SSE4.1/4.2 instruction
  
  $bazel build -c opt --copt=-mavx --copt=-mfpmath=both --copt=-msse4.2 -k  //tensorflow/tools/pip_package:build_pip_package

4) This will build a script in bazel-bin/tensorflow/tools/pip_package/build_pip_package

5) Run this to make wheel package

  $bazel-bin/tensorflow/tools/pip_package/build_pip_package /tmp/tensorflow

6) Install wheel using pip install wheel_name
  
  $pip install /tmp/tensorflow/tensorflow-1.3.0-cp35-cp35m-linux_x86_64.whl 

  


