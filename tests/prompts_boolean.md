# Notes

Pour tester Llamas2 7B sans installation 😎: [https://www.llama2.space/de](https://www.llama2.space/de)

## Exemples de requêtes en langage naturel

* Recherche les publications de Michel Mayor sur les transitions, datant de 2000-2010
* Je veux des documents sur l'égalité hommes femmes en Suisse dans les années 1950
* Crée-moi une bibliographie sur le nu dans la peinture du XVIIIe siècle
* Un roman de Laurent Gaudé publié en 2008
* Des documents sur le rôle de la Suisse durant la première guerre mondiale du point de vue financier

## Résultats de la i-ème requète
[p1r1](Author Michel Mayor) AND (Publication Date >= 2000-01-01) AND (Publication Date <= 2010-12-31)\n    \nExplanation:\n\n* (Author Michel Mayor) : Cette clause de requête vérifie si l'auteur des publications est Michel Mayor.\n* (Publication Date >= 2000-01-01) : Cette clause de requête vérifie si la date de publication est égale ou supérieure à 2000-01-01.\n* (Publication Date <= 2010-12-31) : Cette clause de requête vérifie si la date de publication est égale ou inférieure à 2010-12-31.\nEn résumé, cette requête booléenne va chercher toutes les publications de Michel Mayor qui ont eu lieu entre 2000 et 2010.
2.

## Exemples de prompts

De plus efficace au moins efficace

> The following natural language phrase is a search request in the university library catalogue. If applicable extract the authors (json key "author"), the start publication year (json key "start_date"), the end publication year (json key "end_date") and the subjects (json key "subject"). For "subject", create a boolean request with synomyms in French and English. If no data is identified, the variable is null. Your response is a JSON file without comments.
> 
> I'm gonna provide you two examples with the raw search query and the expected json structure.
> 
> example1.raw_search_query = "Recherche les publications de Michel Mayor sur les transitions, datant de 2000-2010"
> 
> example1.expected_json_structure = """{{ "author": "Michel Mayor", "start_date": "2000", "end_date": "2010", "subject": "(transitions OR transition) AND (sciences OR scientific OR technology OR technologie)" }}"""
> 
> example2.raw_search_query = "Je cherche un livre de Harlan Coben publié en 2009 à propos de sang"
> 
> example2.expected_json_structure = """{{ "author": "Harlan Coben", "start_date": "2009", "end_date": null, "subject": "sang OR blood" }}"""
> 
> example3.raw_search_query = "Des articles scientifiques sur le COVID-19 en bibliothèque académique publiés après 2020"
> 
> example3.expected_json_structure = """{{ "author": null, "start_date": "2020", "end_date": null, "subject": "(COVID-19 OR coronavirus OR pandémie OR pandemic) AND (bibliothèque académique OR bibliothèques universitaires OR academic library OR university libraries)" }}"""
> 
> Now apply these rules to convert the following raw search query: {search}

---

> You are the best model to map raw texts to desired Json format. You are tasked with converting a given search query into a JSON object with the specified structure.
> 
> Please follow these guidelines:
> 
> 1. If the provided text is empty or does not contain any relevant information, return the JSON structure with all values as empty strings.
> 
> 2. Extract relevant information from the provided text and map it to the corresponding keys in the JSON structure.
> 
> 3. For "subject", create a boolean request with synomyms in French and English.
> 
> 4. If a particular key's value is not found in the given text, leave the value as an empty string.
> 
> 5. Do not include any additional information or formatting beyond the requested JSON object.
> 
> I'm gonna provide you two examples with the raw search query and the expected json structure.
> 
> example1.raw_search_query = "Je cherche un livre de Harlan Coben publié en 2009 à propos de sang"
> example1.expected_json_structure = """{{
>   "author": "Harlan Coben",
>   "start_date": "2009",
>   "end_date": null,
>   "subject": "sang OR blood"
> }}"""
> 
> example2.raw_search_query = "Recherche les publications de Michel Mayor sur les transitions, datant de 2000-2010"
> example2.expected_json_structure = """{{
>   "author": "Michel Mayor",
>   "start_date": "2000",
>   "end_date": "2010",
>   "subject": "(transitions OR transition) AND (sciences OR scientific OR technology OR technologie)"
> }}"""
> 
> Now apply these rules to convert the following raw search query: {search}

---

> The following natural language phrase is a search request in the university library catalogue. If applicable extract the authors (variable AUTHOR), the start publication year (variable START_DATE), the end publication year (variable END_DATE) and the subjects (variable SUBJECT). For SUBJECT, create a boolean request with synomyms in French and English. If no data is identified, the variable is null. Your response must follow this JSON format:

---

> The following natural language phrase is a search request in the university library catalogue. If applicable extract the authors (variable AUTHOR), the start publication year (variable START_DATE), the end publication year (variable END_DATE) and the subjects (variable SUBJECT). For SUBJECT, create a boolean request with synomyms in French and English. If no data is identified, the variable is null. Your response must follow this JSON format:
> {
> "AUTHOR": "Laurent Gaudé",
> "START_DATE": "2008",
> "END_DATE": null,
> "SUBJECT": "(suisse OR switzerland OR swiss) AND (finance OR financial OR économique OR economic)"
> }

## Exemples d'input depuis l'IA pour traitement python

Mayor:

```json
{
"AUTHOR": "Michel Mayor",
"START_DATE": "2000",
"END_DATE": "2010",
"SUBJECT": "(transitions OR transition) AND (finance OR financial OR économique OR economic)"
}
```

Gaudé:

```json
{
"AUTHOR": "Laurent Gaudé",
"START_DATE": "2008",
"END_DATE": null,
"SUBJECT": "(suisse OR switzerland OR swiss) AND (egalite OR equality OR gender OR women) AND (1950 OR "ancien regime")"
}
```


## API swisscovery: doc booléen

?query=creator,contains,michel mayor,AND&query=any,contains,transition,AND&pfilter=dr_s,exact,20000101,AND&pfilter=dr_e,exact,20101231,AND&tab=41SLSP_UGE_MyInst_CI&search_scope=MyInst_and_CI&vid=41SLSP_UGE:VU1&mode=advanced&offset=0

Partout: `query=any,contains,transition,`
Auteur: `query=creator,contains,michel mayor`
Année départ: `pfilter=dr_s,exact,20000101`
Année fin: `pfilter=dr_e,exact,20101231`
