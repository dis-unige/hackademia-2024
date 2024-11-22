# Notes

Pour tester Llamas2 7B sans installation 😎: [https://www.llama2.space/de](https://www.llama2.space/de)

Doc pour un prompt fait pour obtenir du JSON dans la réponse : https://medium.com/@harshitdy/how-to-get-only-json-response-from-any-llm-using-langchain-ed53bc2df50f

## Tâches pour la recherche d'un concept en langage naturelle dans swisscovery


## Exemples de requêtes en langage naturel
1. J'aimerais savoir qu'est-ce le bosson de Higgs


## Exemples de prompts
    template = """
    Question: I want to transform the question "{question}" into a new booleen query that I can use in a library catalog search.
    Add several synonyms for the subjects and the translation of the terms into french and english and combine all the termes with OR.
    Give me only the query without explanations.
    
    Answer:
    """
    {'question': "Je veux savoir ce qu'est le bosson de Higgs", 'text': ' `(("physics" OR "physique") AND ("higgs boson" OR "boson de Higgs"))`'} 

    {'question': 'Can you explain me the mexican revolution conducting to the independence of the country', 'text': ' (mexican OR mexico) AND revolution* NOT independence\n    '}

    {'question': 'comment la circonference de la terre a pu être calculé en grece antique?', 'text': ' (circonference OR circumvolution* OR peripherique) AND ("Grec antic" OR "Ancient Greek")\n    '} 

    {'question': 'Qui a calculé la circonférence de la terre en premier?', 'text': ' `(subject:("Circonference" OR "Circumferences") AND (translation_fr:"calculer la circonférence de la terre" OR translation_en:"who calculated the circumference of the earth"))`'} 

## API swisscovery: convertir la requête en URL




