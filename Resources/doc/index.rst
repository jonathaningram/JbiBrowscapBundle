Provides integration for Browscap for your Symfony2 Project.

Installation
============

Bring in the vendor libraries
-----------------------------

This can be done in two different ways:

**Method #1**) Use the bin/vendor script

::

    [phpbrowscap]
        git=http://github.com/GaretJax/phpbrowscap.git

    [JbiBrowscapBundle]
        git=http://github.com/jonathaningram/JbiBrowscapBundle.git
        target=bundles/Jbi/BrowscapBundle

**Method #2**) Use git submodules

::

    git submodule add git://github.com/GaretJax/phpbrowscap.git vendor/phpbrowscap
    git submodule add git://github.com/Jbi/BrowscapBundle.git vendor/bundles/Jbi/BrowscapBundle

Register the phpbrowscap and Jbi namespaces
---------------------------------------------------

::

    // app/autoload.php
    $loader->registerNamespaces(array(
        // ...
        'phpbrowscap'  => __DIR__.'/../vendor/phpbrowscap/src',
        'Jbi'          => __DIR__.'/../vendor/bundles',
        // ...
    ));

Add JbiBrowscapBundle to your application kernel
-------------------------------------------------------

::

    // app/AppKernel.php
    public function registerBundles()
    {
        return array(
            // ...
            new Jbi\BrowscapBundle\JbiBrowscapBundle(),
            // ...
        );
    }

Configure the bundle
====================

.. note::

    This is not needed if you use the default cache directory setting.

in YAML::

    # app/config.yml
    jbi_browscap:
        cache_dir: "%kernel.cache_dir%/browscap"

Use the JbiBrowscapBundle library
==================================

All explanations about this library are available on the official blog_

As bundle uses the new annotation implementation (as all Symfony2 code)
the annotations are a bit different.

Instead of::

    $browscap = $this->container->get('jbi_browscap.browscap');

    $browserInfo = browscap->getBrowser($userAgentString);