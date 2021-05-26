project('ut432-headers', 'cpp')
cxx = meson.get_compiler('cpp')


# == Definitions for the UT 432 public header tree ==

lib_packages = [
    "Engine",
    "Core",
    "Window"
]

src_packages = {
    "XDrv": [
        "root/XDrv/Src/XClient.cpp",
        "root/XDrv/Src/XDrv.cpp",
        "root/XDrv/Src/XViewport.cpp",
    ],
    "XMesaGLDrv": [
        "root/XMesaGLDrv/Src/XMesaGL.cpp",
        "root/XMesaGLDrv/Src/XMesaGLDrv.cpp",
    ],
    "OpenGLDrv": [
        "root/OpenGLDrv/Src/OpenGL.cpp",
        "root/OpenGLDrv/Src/OpenGlDrv.cpp",
    ],
    "D3DDrv": [
        "root/D3DDrv/Src/D3DDrv.cpp",
        "root/D3DDrv/Src/Direct3D7.cpp",
        "root/D3DDrv/Src/und3d.cpp",
    ],
    "XLaunch": [
        "root/XLaunch/Src/XLaunch.cpp",
    ],
    "Audio": [
        "root/Audio/Src/AudioCoreLinux.cpp",
        "root/Audio/Src/Audio.cpp",
        "root/Audio/Src/AudioLibrary.cpp",
        "root/Audio/Src/AudioMixer.cpp",
        "root/Audio/Src/AudioSubsystem.cpp",
        "root/Audio/Src/FormatWAV.cpp",
    ],
    "Setup": [
        "root/Setup/Src/FFileManagerArc.cpp",
        "root/Setup/Src/Setup.cpp",
        "root/Setup/Src/USetupDefinition.cpp",
        "root/Setup/Src/USetupDefinitionWindows.cpp",
    ],
    "UCC": [
        "root/UCC/Src/UCC.cpp"
    ]
}


# == Add individual package dependencies ==

deps = {}
all_deps = []

foreach libpkg : lib_packages
    inc = include_directories('root/@0@/Inc'.format(libpkg))
    lib = cxx.find_library('root/@0@/Lib/@0@.lib')

    dep = declare_dependency(include_directories: inc, link_with: lib)
    all_deps += [dep]
    deps += { libpkg: dep }
endforeach

foreach srcpkg, srcs : src_packages
    inc = include_directories('root/@0@/Inc'.format(srcpkg))
    lib = static_library('@0@'.format(srcpkg), srcs)

    dep = declare_dependency(include_directories: inc, link_with: lib)
    all_deps += [dep]
    deps += { srcpkg: dep }
endforeach


# == Add 'global dependency' ==

ut432_headers = declare_dependency(dependencies: all_deps)
