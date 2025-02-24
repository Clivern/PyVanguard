.. image:: https://image.api.playstation.com/vulcan/img/rnd/202108/2318/laMdtTUhSHB2neSymEjIt5oF.jpg
  :width: 700
  :alt: Alternative text

.. image:: https://github.com/Clivern/PyVanguard/actions/workflows/ci.yml/badge.svg?branch=main
    :alt: Build Status
    :target: https://github.com/Clivern/PyVanguard/actions/workflows/ci.yml

|

===========
PyVanguard
===========

OnCall AI Assistant, Your Intelligent Incident Resolution Partner!

Meet OnCall AI Assistant, your friendly helper for tackling incidents quickly and efficiently. This smart tool makes resolving issues a breeze by tapping into your team's documents and learning from past incidents.


Features:
---------

* Smart Insights: It uses your team's knowledge base to provide solutions that fit your unique workflows and practices.
* Learn from the Past: By looking at how previous incidents were handled, it suggests tried-and-true methods to solve current problems.
* Easy Recommendations: OnCall AI combines real-time data with historical context to give you straightforward advice tailored to your situation.
* Keeps Getting Better: With every incident it helps resolve, it learns and improves, so it's always ready to assist your team more effectively.
* Works with Your Tools: It integrates smoothly with what you already use, enhancing your team's skills without replacing them.


Usage:
------

* First you need to load the following environment variables.

.. code-block::

      export OPENAI_API_KEY=....
      export QDRANT_DB_URL=....
      export QDRANT_DB_API_KEY=....
      export PAGERDUTY_INTEGRATION_KEY=....
      export SQLITE_DB_PATH=/root/pyvanguard.db


* Load The team documents.

.. code-block::

      $ pyvanguard load --dir_path /root/pyvanguard/testdocs --team_name clivern


* Trigger a Pagerduty Alert.

.. code-block::

      $ pyvanguard alert --summary "Host clivern.ams01 is down" --severity critical --team clivern

* Query the RAG

.. code-block::

      $ pyvanguard query --text "Host clivern.ams01 is Down" --kind "" --team clivern --limit 2
      $ pyvanguard query --text "Host clivern.ams01 is Down" --kind "team_document" --team clivern --limit 2
      $ pyvanguard query --text "Host clivern.ams01 is Down" --kind "pagerduty_alert" --team clivern --limit 2
