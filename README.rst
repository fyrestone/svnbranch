svnbranch
==============

A lightweight svn branch tool with externals support. 

features
--------------

- Cross-platform (Windows/Linux/MacOSX)

- Create branch through svn URLs directly, no need to clone entire repository

- Auto scans externals from one or more URLs or local repository

- Support all kinds of externals forms

- Support peg revision and operative revision

- Support non-ascii svn paths or externals


Installation
--------------

Just perform

 `$ pip install svnbranch`

which will install this command line tool on your system.


Usage
--------------

1. It auto scans externals from one or more URLs or local copy, and create a config template contains externals information. 

    `$ svnbranch create_config D:\\Tmp\\sample\\trunk\\src`

    will get a config_template.json in the working directory, for example:

    .. code-block:: json

        {
            "branch_map": {
                "https://hqc-pc:12000/svn/sample/": {
                    "trunk/README.md/": "",
                    "trunk/src/": "",
                    "trunk/third_party/": ""
                }
            },
            "external_cache": {
                "...": "..."
            },
            "url_list": [
                "..."
            ],
            "version": 1
        }


2. Customize your config.

    Define branch_map, and the result config file looks like this:

    .. code-block:: json

        {
            "branch_map": {
                "https://hqc-pc:12000/svn/sample/": {
                    "trunk/README.md/": "branches/bak_{uuid}/README.md",
                    "trunk/src/": "/branches/bak_{uuid}/src",
                    "trunk/third_party/": "branches/bak_{uuid}/3rdparty"
                }
            },
            "...": "..."
        }

    - The {uuid} is will be replaced by -uid, --uuid argument of create_branch sub command.


3. Create branches or delete branches with your config, add -t to simulate the operation.

    `$ svnbranch create_branch conf/my_branch.json -t`

    `$ svnbranch delete_branch conf/my_branch.json 20180121T1557 -t`


Repository
--------------

The project is hosted on GitHub. You can look at the source here:

 https://github.com/fyrestone/svnbranch
 
