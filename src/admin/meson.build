# Meson definition for Laniakea - Admin CLI

install_subdir('.', install_dir: 'lib/laniakea/admin/',
    exclude_directories: ['__pycache__', 'lkadmin/__pycache__'],
    exclude_files: ['meson.build', 'lk-admin.py'],
)
install_data('lk-admin.py', install_dir: 'bin', rename: 'lk-admin')
