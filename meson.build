

CXX = meson.get_compiler('cpp')



# subdir('subprojects/libtorch')
torch_path = meson.current_source_dir()
message('libtorch path is : ' + torch_path)

torch_libs = []
foreach lib : ['torch', 'torch_cpu', 'c10' ]
  torch_libs += CXX.find_library(lib, dirs : join_paths(torch_path, 'lib'))
endforeach

torch_dep = declare_dependency(
  include_directories : include_directories(
      'include',
      'include/torch/csrc/api/include'
  ),
  dependencies : torch_libs,
  compile_args : ['-D_GLIBCXX_USE_CXX11_ABI=0'],
  link_args : ['-Wl,-R@0@/lib'.format(torch_path)]
)
