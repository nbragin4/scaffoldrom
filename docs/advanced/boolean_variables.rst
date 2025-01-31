Boolean Variables
-----------------

.. versionadded:: 2.2.0

Boolean variables are used for answering True/False questions.

Basic Usage
~~~~~~~~~~~

Boolean variables are regular key / value pairs, but with the value being
``True``/``False``.

For example, if you provide the following boolean variable in your
``scaffoldrom.yaml``::

   {
       "run_as_docker": true
   }

you will get the following user input when running Scaffoldrom::

  run_as_docker [True]:

User input will be parsed by :func:`~scaffoldrom.prompt.read_user_yes_no`. The
following values are considered as valid user input:

    - ``True`` values: "1", "true", "t", "yes", "y", "on"
    - ``False`` values: "0", "false", "f", "no", "n", "off"

The above ``run_as_docker`` boolean variable creates ``scaffoldrom.run_as_docker``,
which can be used like this::

  {%- if scaffoldrom.run_as_docker -%}
  # In case of True add your content here

  {%- else -%}
  # In case of False add your content here

  {% endif %}

Scaffoldrom is using `Jinja2's if conditional expression <https://jinja.palletsprojects
.com/en/latest/templates/#if>`_ to determine the correct ``run_as_docker``.

Input Validation
~~~~~~~~~~~~~~~~
If a non valid value is inserted to a boolean field, the following error will be printed:

.. code-block:: bash

   run_as_docker [True]: docker
   Error: docker is not a valid boolean
