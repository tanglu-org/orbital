project('Laniakea', 'c',
    meson_version: '>=0.48',
    license: 'LGPL-3.0+',
    version: '0.1'
)

source_root = meson.source_root()
build_root  = meson.build_root()

pymod = import('python')
py = pymod.find_installation('python3')

#
# Dependencies
#
python_min_version = '3.9'
systemd_dep = dependency('systemd')

if not py.language_version().version_compare('>=' + python_min_version)
    error('Python version is too low. We require at least ' + python_min_version + ' to run.')
endif

# Python dependencies
pymod_check_exe = find_program(join_paths(source_root, 'pyreqcheck.py'))
pymod_check_arg = ['--check-group']
r = run_command(pymod_check_exe, [pymod_check_arg, 'base'])
if r.returncode() != 0
    error(r.stderr().strip())
endif

# maintainer target to update requirements files
run_target ('update-requirements',
    command: [pymod_check_exe, ['--write-requirements']]
)

#
# Lanikaea Modules
#
subdir('src')

#
# Data
#
subdir('data')

#
# Tests
#
subdir('tests')

#
# Documentation
#
if get_option('docs')
    subdir('docs')
endif
