=======
Engines
=======

Special Engine Settings
=======================

.. sidebar:: Further reading ..

   - :ref:`settings engine`
   - :ref:`engine settings` & :ref:`engine file`

.. toctree::
   :maxdepth: 1

   engines/recoll.rst


.. _engines generic:

General Engine Settings
=======================

Explanation of the :ref:`general engine configuration` shown in the table
:ref:`configured engines`.

============= =========== ==================== ============
:ref:`engine settings`    :ref:`engine file`
------------------------- ---------------------------------
Name (cfg)                Categories
------------------------- ---------------------------------
Engine        ..          Paging support       **P**
------------------------- -------------------- ------------
Shortcut      **S**       Language support     **L**
Timeout       **TO**      Time range support   **TR**
Disabled      **D**       Engine type          **ET**
------------- ----------- -------------------- ------------
Safe search   **SS**
------------- ----------- ---------------------------------
Weigth        **W**
------------- ----------- ---------------------------------
Disabled      **D**
------------- ----------- ---------------------------------
Show errors   **DE**
============= =========== =================================

.. _configured engines:

.. jinja:: webapp

   .. flat-table:: Engines configured at built time (defaults)
      :header-rows: 1
      :stub-columns: 2

      * - Name (cfg)
        - S
        - Engine
        - TO
        - Categories
        - P
        - L
        - SS
        - D
        - TR
        - ET
        - W
        - D
        - DE

      {% for name, mod in engines.items() %}

      * - {{name}}
        - !{{mod.shortcut}}
        - {{mod.__name__}}
        - {{mod.timeout}}
        - {{", ".join(mod.categories)}}
        - {{(mod.paging and "y") or ""}}
        - {{(mod.language_support and "y") or ""}}
        - {{(mod.safesearch and "y") or ""}}
        - {{(mod.disabled and "y") or ""}}
        - {{(mod.time_range_support and "y") or ""}}
        - {{mod.engine_type or ""}}
        - {{mod.weight or 1 }}
        - {{(mod.disabled and "y") or ""}}
        - {{(mod.display_error_messages and "y") or ""}}

     {% endfor %}

