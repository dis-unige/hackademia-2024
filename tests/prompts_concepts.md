# Notes

Pour tester Llamas2 7B sans installation 😎: [https://www.llama2.space/de](https://www.llama2.space/de)

Doc pour un prompt fait pour obtenir du JSON dans la réponse : https://medium.com/@harshitdy/how-to-get-only-json-response-from-any-llm-using-langchain-ed53bc2df50f

## Tâches pour la recherche d'un concept en langage naturelle dans swisscovery


## Exemples de requêtes en langage naturel
1. J'aimerais savoir ce qu'est le bosson de Higgs


## Exemples de prompts
    Question: I want an concise explanation about the question "{question}" and also to transform the question into a booleen search strategy that can be used in a library catalog.
    The search query can be constructed using several synonyms of the subject in french and english. All the terms of the query can be combined with OR.
    Put the string '[explanation]' before your explanation about the question.
    Put the string '[query]' before que search query.
    Don't add comments inside the query, give only the serach strategy the we can use in our library database.
    Please respect this structure on the answer: '[explanation] the subject explanation. [query] the search strategy' and don't add explanations after the query
    
    Answer:
    """

--------------------------------------

    template = """
    Question: I want to transform the question "{question}" into a new booleen query that I can use in a library catalog search.
    Add several synonyms for the subjects and the translation of the terms into french and english and combine all the termes with OR.
    Give me only the query without explanations.
    
    Answer:
    """

---------------------------------------
    {'question': "Je veux savoir ce qu'est le bosson de Higgs", 'text': '\n    [explanation] Le bosson de Higgs est une particule hypothétique qui est considérée comme être à l\'origine des masses des particules subatomiques. Elle a été décrite mathématiquement par le physicien britannique Peter Higgs et son équipe en 1964. Le boson de Higgs est un des fondamentaux du modèle standards de la physique des particules, qui explique comment les particule acquissent leurs masses.\n    [query] (("bosson de Higgs" OR "Higgs boson") OR ("particule hypothetique" OR "masse subatomique") OR ("modèle standard" OF physique des particules) OR ("physicien britannique" OR "Peter Higgs"))\n    This search query uses the terms "bosson de Higgs", "Higgs boson", "particule hypothetique", "masse subatomique", and "modèle standard de la physique des particules" to find books, articles, or other resources related to the subject. The OR operator is used to combine these terms and retrieve resources that contain at least one of them. This allows users to search for information on different aspects of the boson de Higgs, such as its discovery, properties, or implications in physics.'}


    {'question': "Je veux savoir ce qu'est le bosson de Higgs", 'text': ' `(("physics" OR "physique") AND ("higgs boson" OR "boson de Higgs"))`'} 

    {'question': 'Can you explain me the mexican revolution conducting to the independence of the country', 'text': ' (mexican OR mexico) AND revolution* NOT independence\n    '}

    {'question': 'comment la circonference de la terre a pu être calculé en grece antique?', 'text': ' (circonference OR circumvolution* OR peripherique) AND ("Grec antic" OR "Ancient Greek")\n    '} 

    {'question': 'Qui a calculé la circonférence de la terre en premier?', 'text': ' `(subject:("Circonference" OR "Circumferences") AND (translation_fr:"calculer la circonférence de la terre" OR translation_en:"who calculated the circumference of the earth"))`'} 

## API swisscovery: convertir la requête en URL




