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

* Transforme la phrase suivante en requête booléenne: "requête en langage naturel 1."
* The following natural language phrase is a search request in the university library catalogue. If applicable extract the authors (variable AUTHOR), the start publication year (variable START_DATE), the end publication year (variable END_DATE) and the subjects (variable SUBJECT). If no data is identified, the variable must be empty. Output only a JSON file as result.

`The following natural language phrase is a search request in the university library catalogue. If applicable extract the authors (variable AUTHOR), the start publication year (variable START_DATE), the end publication year (variable END_DATE) and the subjects (variable SUBJECT). For SUBJECT, create a boolean request with synomyms in French and English. If no data is identified, the variable must be an empty string. Output only a JSON file as result. An exemple of the output is given below:
{
"AUTHOR": "Laurent Gaudé",
"START_DATE": "2008",
"END_DATE": null,
"SUBJECT": "(suisse OR switzerland OR swiss) AND (finance OR financial OR économique OR economic)"
}
`


## API swisscovery: doc booléen

?query=creator,contains,michel mayor,AND&query=any,contains,transition,AND&pfilter=dr_s,exact,20000101,AND&pfilter=dr_e,exact,20101231,AND&tab=41SLSP_UGE_MyInst_CI&search_scope=MyInst_and_CI&vid=41SLSP_UGE:VU1&mode=advanced&offset=0

Partout: `query=any,contains,transition,`
Auteur: `query=creator,contains,michel mayor`
Année départ: `pfilter=dr_s,exact,20000101`
Année fin: `pfilter=dr_e,exact,20101231`
