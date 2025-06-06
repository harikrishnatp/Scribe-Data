query_profanity.sparql
======================

`View code on Github <https://github.com/scribe-org/Scribe-Data/tree/main/src/scribe_data/wikidata/query_profanity.sparql>`_

Queries all profane words from a given language to be removed from autosuggest options. Enter this query at https://query.wikidata.org/.

.. code:: sparql

    # tool: scribe-data
    # Queries all profane words from a given language to be removed from autosuggest options.
    # Enter this query at https://query.wikidata.org/.

    SELECT DISTINCT
        ?lemma

    WHERE {
        ?lexemeId dct:language wd:LANGUAGE_QID; # replace language qid here
            wikibase:lemma ?lemma;
            ontolex:sense ?sense.

        VALUES ?filter {
            wd:Q8102
            wd:Q545779
            wd:Q1521634
            wd:Q184439
        }.

        FILTER EXISTS {?sense wdt:P6191 ?filter.}.
    }

    ORDER BY
        lcase(?lemma)

..
