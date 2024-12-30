project('super', 'c',
  version : '0.1',
  default_options : ['warning_level=3'])

dep = dependency('mydep')

dir = dep.get_variable('mydatadir')

# Generated file depending on dep's generated file.
sed = find_program('sed', native: true)
custom_target(
  command: [sed, '-e', 's,@second@,hmm,g', '@INPUT@'],
  input: dir / 'configuration_file.ini',
  output: 'configuration_file',
  capture: true,
)

executable('super',
           'main.c',
           dependencies: dep)
