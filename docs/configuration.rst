Configuration
=============

.. include:: configuration-prelude.rst

.. contents::
   :depth: 2
   :local:

Core
----

Extension class: ``PhpBench\Extension\CoreExtension``

.. _configuration_core_debug:

core.debug
~~~~~~~~~~

If enabled output debug messages (e.g. the commands being executed when running benchamrks). Same as ``-vvv``

Default: ``false``

Types: ``["bool"]``

.. _configuration_core_extensions:

core.extensions
~~~~~~~~~~~~~~~

List of additional extensions to enable

Default: ``[]``

Types: ``["array"]``

.. _configuration_core_working_dir:

core.working_dir
~~~~~~~~~~~~~~~~

Working directory to use

Default: ``"\/home\/daniel\/www\/phpbench\/phpbench"``

Types: ``["string"]``

.. _configuration_core_config_path:

core.config_path
~~~~~~~~~~~~~~~~

Alternative path to a PHPBench configuration file (default is ``phpbench.json``

Default: ``null``

Types: ``["string","null"]``

.. _configuration_core_profiles:

core.profiles
~~~~~~~~~~~~~

Alternative configurations::

    {
        "core.profiles": {
            "php8": {
                "runner.php_bin": "/bin/php8"
            }
        }
    }

The named configuration will be merged with the default configuration, and can be used via:

.. code-block:: bash

    $ phpbench run --profile=php8

Default: ``[]``

Types: ``["array"]``

Runner
------

Extension class: ``PhpBench\Extension\RunnerExtension``

.. _configuration_runner_annotations:

runner.annotations
~~~~~~~~~~~~~~~~~~

Read metadata from annotations

Default: ``true``

Types: ``["bool"]``

.. _configuration_runner_annotation_import_use:

runner.annotation_import_use
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Require that annotations be imported before use

Default: ``false``

Types: ``["bool"]``

.. _configuration_runner_attributes:

runner.attributes
~~~~~~~~~~~~~~~~~

Read metadata from PHP 8 attributes

Default: ``true``

Types: ``["bool"]``

.. _configuration_runner_bootstrap:

runner.bootstrap
~~~~~~~~~~~~~~~~

Path to bootstrap (e.g. ``vendor/autoload.php``)

Default: ``null``

Types: ``["string","null"]``

.. _configuration_runner_env_enabled_providers:

runner.env_enabled_providers
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Select which environment samplers to use

Default: ``["sampler","git","opcache","php","uname","unix_sysload"]``

Types: ``["array"]``

.. _configuration_runner_env_samplers:

runner.env_samplers
~~~~~~~~~~~~~~~~~~~

Environment baselines (not to be confused with baseline comparisons when running benchmarks) are small benchmarks which run to sample the speed of the system (e.g. file I/O, computation etc). This setting enables or disables these baselines

Default: ``["nothing","md5","file_rw"]``

Types: ``["array"]``

.. _configuration_runner_env_sampler_callables:

runner.env_sampler_callables
~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Map of baseline callables (adds you to register a new environemntal baseline)

Default: ``[]``

Types: ``["array"]``

.. _configuration_runner_executors:

runner.executors
~~~~~~~~~~~~~~~~

Add new executor configurations

Default: ``[]``

Types: ``["array"]``

.. _configuration_runner_path:

runner.path
~~~~~~~~~~~

Path or paths to the benchmarks

Default: ``null``

Types: ``["string","array","null"]``

.. _configuration_runner_php_binary:

runner.php_binary
~~~~~~~~~~~~~~~~~

Specify a PHP binary to use when executing out-of-band benchmarks, e.g. ``/usr/bin/php6``, defaults to the version of PHP used to invoke PHPBench

Default: ``null``

Types: ``["string","null"]``

.. _configuration_runner_php_config:

runner.php_config
~~~~~~~~~~~~~~~~~

Map of PHP ini settings to use when executing out-of-band benchmarks

Default: ``[]``

Types: ``["array"]``

.. _configuration_runner_php_disable_ini:

runner.php_disable_ini
~~~~~~~~~~~~~~~~~~~~~~

Disable reading the default PHP configuration

Default: ``false``

Types: ``["bool"]``

.. _configuration_runner_php_wrapper:

runner.php_wrapper
~~~~~~~~~~~~~~~~~~

Wrap the PHP binary with this command (e.g. ``blackfire run``)

Default: ``null``

Types: ``["string","null"]``

.. _configuration_runner_progress:

runner.progress
~~~~~~~~~~~~~~~

Default progress logger to use

Default: ``"verbose"``

Types: ``["string"]``

.. _configuration_runner_progress_summary_variant_format:

runner.progress_summary_variant_format
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Expression used to render the summary text default progress loggers

Default: ``"\"Mo\" ~ display_as_time(mode(variant.time.avg), coalesce(subject.time_unit,\"time\"), subject.time_precision, subject.time_mode) ~ \n\" (\" ~ rstdev(variant.time.avg) ~ \")\""``

Types: ``["string"]``

.. _configuration_runner_progress_summary_baseline_format:

runner.progress_summary_baseline_format
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

When the a comparison benchmark is referenced, alternative expression used to render the summary text default progress loggers

Default: ``"\"[\" ~ \n\"Mo\" ~ display_as_time(mode(variant.time.avg), coalesce(subject.time_unit,\"time\"), subject.time_precision, subject.time_mode) ~\n\" vs \" ~ \n\"Mo\" ~ display_as_time(mode(baseline.time.avg), coalesce(subject.time_unit,\"time\"), subject.time_precision, subject.time_mode) ~ \"] \" ~ \npercent_diff(mode(baseline.time.avg), mode(variant.time.avg), (rstdev(variant.time.avg) * 2)) ~\n\" (\" ~ rstdev(variant.time.avg) ~ \")\""``

Types: ``["string"]``

.. _configuration_runner_remote_script_path:

runner.remote_script_path
~~~~~~~~~~~~~~~~~~~~~~~~~

PHPBench generates a PHP file for out-of-band benchmarks which is executed, this setting specifies the path to this file. When NULL a file in the systems temporary directory will be used

Default: ``null``

Types: ``["string","null"]``

.. _configuration_runner_remote_script_remove:

runner.remote_script_remove
~~~~~~~~~~~~~~~~~~~~~~~~~~~

If the generated file should be removed after it has been executed (useful for debugging)

Default: ``true``

Types: ``["bool"]``

.. _configuration_runner_assert:

runner.assert
~~~~~~~~~~~~~

Default :ref:`metadata_assertions`

Default: ``null``

Types: ``["null","string","array"]``

.. _configuration_runner_executor:

runner.executor
~~~~~~~~~~~~~~~

Default executor

Default: ``null``

Types: ``["null","string"]``

.. _configuration_runner_format:

runner.format
~~~~~~~~~~~~~

Default :ref:`metadata_format`

Default: ``null``

Types: ``["null","string"]``

.. _configuration_runner_iterations:

runner.iterations
~~~~~~~~~~~~~~~~~

Default :ref:`metadata_iterations`

Default: ``null``

Types: ``["null","int","array"]``

.. _configuration_runner_output_mode:

runner.output_mode
~~~~~~~~~~~~~~~~~~

Default :ref:`output mode <metadata_mode>`

Default: ``null``

Types: ``["null","string"]``

.. _configuration_runner_time_unit:

runner.time_unit
~~~~~~~~~~~~~~~~

Default :ref:`time unit <metadata_time_unit>`

Default: ``null``

Types: ``["null","string"]``

.. _configuration_runner_retry_threshold:

runner.retry_threshold
~~~~~~~~~~~~~~~~~~~~~~

Default :ref:`metadata_retry_threshold`

Default: ``null``

Types: ``["null","int","float"]``

.. _configuration_runner_revs:

runner.revs
~~~~~~~~~~~

Default number of :ref:`metadata_revolutions`

Default: ``null``

Types: ``["null","int","array"]``

.. _configuration_runner_timeout:

runner.timeout
~~~~~~~~~~~~~~

Default :ref:`metadata_timeout`

Default: ``null``

Types: ``["null","float","int"]``

.. _configuration_runner_warmup:

runner.warmup
~~~~~~~~~~~~~

Default :ref:`metadata_warmup`

Default: ``null``

Types: ``["null","int","array"]``

.. _configuration_runner_subject_pattern:

runner.subject_pattern
~~~~~~~~~~~~~~~~~~~~~~

Subject prefix to use when finding benchmarks

Default: ``"^bench"``

Types: ``["string"]``

Report
------

Extension class: ``PhpBench\Extension\ReportExtension``

.. _configuration_report_generators:

report.generators
~~~~~~~~~~~~~~~~~

Report generator configurations, see :doc:`report-generators`

Default: ``[]``

Types: ``["array"]``

.. _configuration_report_outputs:

report.outputs
~~~~~~~~~~~~~~

Report renderer configurations, see :doc:`report-renderers`

Default: ``[]``

Types: ``["array"]``

Expression
----------

Extension class: ``PhpBench\Extension\ExpressionExtension``

.. _configuration_expression_syntax_highlighting:

expression.syntax_highlighting
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Enable syntax highlighting

Default: ``true``

Types: ``["bool"]``

.. _configuration_expression_theme:

expression.theme
~~~~~~~~~~~~~~~~

Select a theme to use

Default: ``"solarized"``

Types: ``["string"]``

Storage
-------

Extension class: ``PhpBench\Extension\StorageExtension``

.. _configuration_storage_driver:

storage.driver
~~~~~~~~~~~~~~

Storage driver to use

Default: ``"xml"``

Types: ``["string"]``

.. _configuration_storage_xml_storage_path:

storage.xml_storage_path
~~~~~~~~~~~~~~~~~~~~~~~~

Path to store benchmark runs when they are stored with ``--store`` or ``--tag=foo``

Default: ``".phpbench\/storage"``

Types: ``["string"]``

XDebug
------

Extension class: ``PhpBench\Extensions\XDebug\XDebugExtension``

.. _configuration_xdebug_command_handler_output_dir:

xdebug.command_handler_output_dir
~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~~

Output directory for generated XDebug profiles

Default: ``".phpbench\/xdebug-profile"``

Types: ``["string"]``

Console
-------

Extension class: ``PhpBench\Extension\ConsoleExtension``

.. _configuration_console_ansi:

console.ansi
~~~~~~~~~~~~

Enable or disable ANSI control characters (e.g. console colors)

Default: ``true``

Types: ``["bool"]``

.. _configuration_console_disable_output:

console.disable_output
~~~~~~~~~~~~~~~~~~~~~~

Disable output from both STDOUT and STDERR

Default: ``false``

Types: ``["bool"]``

.. _configuration_console_output_stream:

console.output_stream
~~~~~~~~~~~~~~~~~~~~~

Change the normal output stream - the output stream used for reports

Default: ``"php:\/\/stdout"``

Types: ``["string"]``

.. _configuration_console_error_stream:

console.error_stream
~~~~~~~~~~~~~~~~~~~~

Change the error output stream - the output stream used for diagnostics (e.g. progress loggers use this stream)

Default: ``"php:\/\/stderr"``

Types: ``["string"]``

