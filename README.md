Composer Plugin Mass Files Copier
========================================

this is a very simple Composer plugin working on the `post-install-cmd` and `post-update-cmd` events for copying from a source path to a distination forlder.


Installation / Usage
--------------------

1. In your composer.json project's file add the requirements

    ``` json
    {
        "require": {
            "sasedev/composer-plugin-filecopier": ">=1.0.0"
        }
    }
    ```

2. In your composer.json project's file add the config in the extra element

    ``` json
    {
        "extra": {
            "filescopier" : {
                "source" : "vendor/twbs/bootstrap/less",
                "destination" : "var/less/bootstrap"
            }
        }
    }
    ```

or

    ``` json
    {
        "extra": {
            "filescopier" : [
                {
                    "source" : "vendor/twbs/bootstrap/less",
                    "destination" : "var/less/bootstrap"
                }, {
                    "source" : "src/Sasedev/ResBundle/Resources/less/bootstrap/*.less",
                    "destination" : "var/less/bootstrap"
                }, {
                    "source" : "/home/sasedev/Documents/*.pdf",
                    "destination" : "var/test"
                }
            ]
        }
    }
    ```

    > **Note:** The destination element must be a folder. if the destination folder does not exists, it is recursively created using `mkdir($destination, 0755, true)`.
    > **Note:** If the destination folder is not an absolute path, the relative path is calculated using the vendorDir path (`$project_path = \realpath($this->composer->getConfig()->get('vendor-dir').'/../').'/'`)
    > **Note:** The source element is evaluated using the php function `glob($source, GLOB_MARK)` and a recursive copy is made for every result of this function into the destination folder

3. Run Composer: `php composer.phar update`.


Requirements
------------

PHP 5.5 or above (at least 5.5.9 recommended to avoid potential bugs)


Authors
-------

Abdelkadeur Seifeddine Salah - <seif.salah@gmail.com> - <https://sasedev.net><br />


License
-------

Composer is licensed under the MIT License - see the LICENSE file for details
