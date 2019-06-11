rtmp_sources = [
  'gstrtmp.c',
  'gstrtmpsink.c',
  'gstrtmpsrc.c',
]

rtmp_lib_path = 'C:/dev/gst-build/thirdparty/librtmp/lib'
rtmp_include_path = 'C:/dev/gst-build/thirdparty/librtmp/include'

rtmp_lib = cc.find_library('rtmp', dirs: rtmp_lib_path, required: true)

rtmp_dep = declare_dependency(include_directories: include_directories(rtmp_include_path), dependencies:  rtmp_lib)

if rtmp_dep.found()
  gstrtmp = library('gstrtmp',
    rtmp_sources,
    c_args : gst_plugins_bad_args,
    include_directories : [configinc],
    dependencies : [gstbase_dep, rtmp_dep] + winsock2,
    install : true,
    install_dir : plugins_install_dir,
  )
  pkgconfig.generate(gstrtmp, install_dir : plugins_pkgconfig_install_dir)
endif
