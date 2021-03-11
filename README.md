[![Testing](https://github.com/InzGIBA/django-extra-settings/actions/workflows/package-test.yml/badge.svg)](https://github.com/InzGIBA/django-extra-settings/actions/workflows/package-test.yml)

# django-extra-settings
config and manage extra settings using just the django admin.

![](https://user-images.githubusercontent.com/1035294/74425761-81325400-4e54-11ea-9095-3d64e1420bfe.gif)

## Installation
-   Run `pip install django-extra-settings`
-   Add `extra_settings` to `settings.INSTALLED_APPS`
-   Run ``python manage.py migrate``
-   Run ``python manage.py collectstatic``
-   Restart your application server

## Usage

### Settings
All these settings are optional, if not defined in ``settings.py`` the default values (listed below) will be used.

```python
# if True the template tag will fallback to os environ,
# very useful to retrieve env.
EXTRA_SETTINGS_FALLBACK_TO_CONF_ENV = True
```

```python
# if True the template tag will fallback to django.conf.settings,
# very useful to retrieve conf settings such as DEBUG.
EXTRA_SETTINGS_FALLBACK_TO_CONF_SETTINGS = True
```

```python
# the upload_to path value of settings of type 'file'
EXTRA_SETTINGS_FILE_UPLOAD_TO = 'files'
```

```python
# the upload_to path value of settings of type 'image'
EXTRA_SETTINGS_IMAGE_UPLOAD_TO = 'images'
```

### Admin
Just go to the admin where you can:
-   Create a new setting
-   Update an existing setting
-   Delete an existing setting

### Python
You can retrieve settings programmatically:
```python
from extra_settings.models import Setting

value = Setting.get('SETTING_NAME', default='django-extra-settings')
```

### Templates
You can retrieve settings in templates:
```html
{% load extra_settings %}

{% get_setting 'SETTING_NAME' default='django-extra-settings' %}
```

## Testing
```bash
# create python virtual environment
virtualenv testing_django_extra_settings

# activate virtualenv
cd testing_django_extra_settings && . bin/activate

# clone repo
git clone https://github.com/fabiocaccamo/django-extra-settings.git src && cd src

# install dependencies
pip install -r requirements.txt

# run tests
tox
# or
python setup.py test
# or
python -m django test --settings "tests.settings"
```

## License
Released under [MIT License](LICENSE.txt).

---

## See also

- [`django-admin-interface`](https://github.com/fabiocaccamo/django-admin-interface) - the default admin interface made customizable by the admin itself. popup windows replaced by modals. 🧙 ⚡

- [`django-colorfield`](https://github.com/fabiocaccamo/django-colorfield) - simple color field for models with a nice color-picker in the admin. 🎨

- [`django-maintenance-mode`](https://github.com/fabiocaccamo/django-maintenance-mode) - shows a 503 error page when maintenance-mode is on. 🚧 🛠️

- [`django-redirects`](https://github.com/fabiocaccamo/django-redirects) - redirects with full control. ↪️

- [`django-treenode`](https://github.com/fabiocaccamo/django-treenode) - probably the best abstract model / admin for your tree based stuff. 🌳

- [`python-benedict`](https://github.com/fabiocaccamo/python-benedict) - dict subclass with keylist/keypath support, I/O shortcuts (base64, csv, json, pickle, plist, query-string, toml, xml, yaml) and many utilities. 📘

- [`python-codicefiscale`](https://github.com/fabiocaccamo/python-codicefiscale) - encode/decode Italian fiscal codes - codifica/decodifica del Codice Fiscale. 🇮🇹 💳

- [`python-fsutil`](https://github.com/fabiocaccamo/python-fsutil) - file-system utilities for lazy devs. 🧟‍♂️
