project(
  'SDL3_mixer',
  'c',
  version: '3.2.2',
  license: 'Zlib',
  meson_version: '>= 1.0.0',
  default_options: [
    'c_std=c99',
    'warning_level=1',
    'default_library=static',
  ],
)

sdl3_dep = dependency('sdl3')
flac_dep = dependency('flac')
opusfile_dep = dependency('opusfile')

sdl3_mixer_sources = files(
  'src/SDL_mixer.c',
  'src/SDL_mixer_metadata_tags.c',
  'src/SDL_mixer_spatialization.c',
  'src/decoder_flac.c',
  'src/decoder_opus.c',
  'src/decoder_raw.c',
  'src/decoder_sinewave.c',
)

sdl3_mixer_c_args = [
  '-DDECODER_FLAC_LIBFLAC',
  '-DDECODER_OPUS',
]

sdl3_mixer_internal_inc = include_directories('src', 'include')
sdl3_mixer_public_inc = include_directories('include', is_system: true)

sdl3_mixer_lib = static_library(
  'SDL3_mixer',
  sdl3_mixer_sources,
  c_args: sdl3_mixer_c_args,
  include_directories: sdl3_mixer_internal_inc,
  dependencies: [sdl3_dep, flac_dep, opusfile_dep],
)

sdl3_mixer_dep = declare_dependency(
  link_with: sdl3_mixer_lib,
  include_directories: sdl3_mixer_public_inc,
  dependencies: [sdl3_dep, flac_dep, opusfile_dep],
)

meson.override_dependency('SDL3_mixer', sdl3_mixer_dep)
meson.override_dependency('sdl3-mixer', sdl3_mixer_dep)
