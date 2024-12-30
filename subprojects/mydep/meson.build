project('mydep', 'c', default_options: ['warning_level=3'])

lib = library('lib', 'lib.c')

# A generated data file is simulated here.
sed = find_program('sed', native: true)
custom_target(
  command: [sed, '-e', 's,@first@,mydep,g', '@INPUT@'],
  input: 'configuration_file.ini.in',
  output: 'configuration_file.ini',
  install: true,
  install_dir: get_option('datadir'),
  capture: true,
)

dep = declare_dependency(link_with: lib, variables: {'mydatadir': get_option('prefix') / get_option('datadir')})

meson.override_dependency('mydep', dep)
