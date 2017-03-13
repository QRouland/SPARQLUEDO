# SPARQLUEDO

ROULAND QUENTIN
HUSSON RENAN

## Question 1

La maison du Professeur Chabalet a pour URI http://www.lamaisondumeurtre.fr/instances#LaMaisonDuMeurtre

### Combien y a-t-il de pièces dans la maison?

 **Requete:**
 
    PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
    PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
    PREFIX xml: <http://www.w3.org/XML/1998/namespace>
    PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
    PREFIX owl: <http://www.w3.org/2002/07/owl#>
    
    SELECT (COUNT(?p) AS ?nbPieces) WHERE
    {
        data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?p .
    }
    
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="nbPieces"/>
	  </head>
	  <results>
	    <result>
	      <binding name="nbPieces">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">9</literal>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 2

### Combien y a-t-il de personnes dans la maison? 

**Requete:**
 
	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT (COUNT(?personne) AS ?nbPersonnes) WHERE
	{
	data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
	?piece cluedo:pieceContientPersonne ?personne .
	}

**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="nbPersonnes"/>
	  </head>
	  <results>
	    <result>
	      <binding name="nbPersonnes">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">10</literal>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 3 

### Qui est la victime?

**Requete:**

	    PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	    PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	    PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	    PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	    PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	    PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	    PREFIX owl: <http://www.w3.org/2002/07/owl#>
	    
	    SELECT ?personne WHERE
	    {
			data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
			?piece cluedo:pieceContientPersonne ?personne . 
			?personne cluedo:estVivant false .
	    }
	    
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="personne"/>
	  </head>
	  <results>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#0c7gdr7</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 4 

Toutes les personnes encore en vie sont considérées suspectes

### Donnez la liste des suspects.

**Requete:**


	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?personne WHERE
	{
		data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
		?piece cluedo:pieceContientPersonne ?personne .
		?personne cluedo:estVivant true .
	}
	
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="personne"/>
	  </head>
	  <results>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#ArmandChabalet</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#LucieNuzyte</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#AubinGladeche</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#VanessaLami</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#GladisTileri</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#EmmaNiolia</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#GuyTarsaich</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#PaulOchon</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#SophieStulle</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 5 

### Dans quelle pièce se situe la victime?

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?piece WHERE
	{
		data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
		?piece cluedo:pieceContientPersonne ?personne .
		?personne cluedo:estVivant false .
	}
	
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="piece"/>
	  </head>
	  <results>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Chambre</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>


## Question 6 

### Y a-t-il d'autres personnes dans cette pièce? (tranformez la requête précédante; utilisez ASK)

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	ASK 
	{
		data:Chambre cluedo:pieceContientPersonne ?personne.
		?personne cluedo:estVivant true.
	}
    
 **Resultat:**
 
	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	  </head>
	  <boolean>false</boolean>
	</sparql>

## Question 7 

### Listez les personnes dans chaque pièce.

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?piece ?personne WHERE 
	{
		?piece cluedo:pieceContientPersonne ?personne .
	}

 **Resultat:**
 
	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="piece"/>
	    <variable name="personne"/>
	  </head>
	  <results>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#PieceTele</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#AldoBermann</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Salon</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#ArmandChabalet</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Bureau</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#AubinGladeche</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Toilette</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#EmmaNiolia</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#SalleDeBain</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#GladisTileri</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#SalleDeJeu</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#GustaveHarie</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#SalleAManger</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#GuyTarsaich</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Salon</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#LucieNuzyte</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#SalleAManger</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#PaulOchon</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Hall</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#SophieStulle</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Bureau</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#VanessaLami</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Chambre</uri>
	      </binding>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#0c7gdr7</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 8 

### Combien y a-t-il de personnes dans chaque pièce (contenant au moins une personne)?

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?piece COUNT(?personne) WHERE 
	{
		?piece cluedo:pieceContientPersonne ?personne .
	}
	GROUP BY ?piece

 **Resultat:**
 
	 <?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="piece"/>
	    <variable name=".1"/>
	  </head>
	  <results>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Salon</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">2</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#SalleDeJeu</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">1</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Hall</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">1</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#PieceTele</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">1</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#SalleDeBain</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">1</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Toilette</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">1</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Chambre</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">1</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#SalleAManger</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">2</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Bureau</uri>
	      </binding>
	      <binding name=".1">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">2</literal>
	      </binding>
	    </result>
	  </results>
	</sparql>
 
 

## Question 9 

### Quelle(s) pièce(s) contien-nen-t au moins deux personnes?

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?piece (COUNT(?personne) as ?nbPersonne) WHERE 
	{
		?piece cluedo:pieceContientPersonne ?personne .
	}
	GROUP BY ?piece
	HAVING(?nbPersonne >= 2)
	
 **Resultat:**
 
	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="piece"/>
	    <variable name="nbPersonne"/>
	  </head>
	  <results>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Salon</uri>
	      </binding>
	      <binding name="nbPersonne">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">2</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#SalleAManger</uri>
	      </binding>
	      <binding name="nbPersonne">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">2</literal>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Bureau</uri>
	      </binding>
	      <binding name="nbPersonne">
		<literal datatype="http://www.w3.org/2001/XMLSchema#integer">2</literal>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 10 

### Quelle(s) pièce(s) est/sont vide(s)?

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT * WHERE 
	{
		data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
		FILTER not EXISTS {?piece cluedo:pieceContientPersonne ?personne .}
	}
	
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="piece"/>
	  </head>
	  <results>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Couloir</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="piece">
		<uri>http://www.lamaisondumeurtre.fr/instances#Cuisine</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 11 

La victime a voulu écrire le nom de son assassin sur un cahier avec une plume, mais le pot d'encre s'est renversé et rend le nom du meurtrier en partie illisible.<br>
![Alt text](http://swip.univ-tlse2.fr/tpsparql/media/encrier-nom.jpg)<br>
On déchiffre cependant que son nom de famille ou son prénom finit par 'e.'

### Quels sont les suspects restants? (augmentez la requête listant les suspects)

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?personne WHERE
	{
		data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
		?piece cluedo:pieceContientPersonne ?personne .
		?personne cluedo:estVivant true .
		FILTER regex(str(?personne), "([A-Z].*e[A-Z])|(e$)", "")
	}
	
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="personne"/>
	  </head>
	  <results>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#LucieNuzyte</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#AubinGladeche</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#SophieStulle</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 12 

Le meurtrier n'est pas dans une des pièces voisines à celle où se situe la victime

### Qui est par conséquent innocent?

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?personne  WHERE
	{
	   	data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
	   	?piece cluedo:pieceContientPersonne ?personne .
		?personne cluedo:estVivant true .
		FILTER (! regex(str(?personne), "([A-Z].*e[A-Z])|(e$)", ""))
	  	FILTER(exists {
	  		?voisin cluedo:pieceContientPersonne ?mort .
			?mort cluedo:estVivant false .
	   		?piece cluedo:aPourPieceVoisine ?voisin .
	    })
	}

**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="personne"/>
	  </head>
	  <results>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#VanessaLami</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#GladisTileri</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#EmmaNiolia</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>
	
	
## Question 13 

Le meurtrier n'est pas dans une des pièces voisines à celle où se situe la victime

### Quels sont les suspects restants? (augmentez la requête listant les suspects)

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?personne  WHERE
	{
	   	data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
	   	?piece cluedo:pieceContientPersonne ?personne .
		?personne cluedo:estVivant true .
		FILTER (regex(str(?personne), "([A-Z].*e[A-Z])|(e$)", ""))
	  	FILTER(not exists {
			?voisin cluedo:pieceContientPersonne ?mort .
			?mort cluedo:estVivant false .
	  		?piece cluedo:aPourPieceVoisine ?voisin .
	    })
	}
	
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="personne"/>
	  </head>
	  <results>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#LucieNuzyte</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#SophieStulle</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 14 

Un certain nombre d'objets suspects ont été identifiés dans la maison. L'un d'entre eux est l'arme du crime.

### Combien y a-t-il d'objets dans la maison?

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT  ?objet  WHERE
	{
	 	data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
	 	?objet cluedo:objetDansPiece ?piece .
	}
	
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="objet"/>
	  </head>
	  <results>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#Chandelier</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#Marteau</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#Livre</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#Revolver</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#Oreiller</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#Poignard</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#PicAGlace</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#EauDeJavel</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#Lacet</uri>
	      </binding>
	    </result>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#Nokia3310</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 15 

L'arme du crime ne se trouve pas dans la pièce où se situe la victime

### Quels objets ne peuvent pas être l'arme du crime?

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?objet  WHERE
	{
		data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
		?objet cluedo:objetDansPiece ?piece .
	    FILTER(not exists {
			?piece cluedo:pieceContientPersonne ?personne .
			?personne cluedo:estVivant false .
			?objet cluedo:objetDansPiece ?piece .
	    }).
	}
	

**Resultat:**

<?xml version="1.0" encoding="UTF-8"?>
<sparql xmlns="http://www.w3.org/2005/sparql-results#">
  <head>
    <variable name="objet"/>
  </head>
  <results>
    <result>
      <binding name="objet">
        <uri>http://www.lamaisondumeurtre.fr/instances#Chandelier</uri>
      </binding>
    </result>
    <result>
      <binding name="objet">
        <uri>http://www.lamaisondumeurtre.fr/instances#Marteau</uri>
      </binding>
    </result>
    <result>
      <binding name="objet">
        <uri>http://www.lamaisondumeurtre.fr/instances#Livre</uri>
      </binding>
    </result>
    <result>
      <binding name="objet">
        <uri>http://www.lamaisondumeurtre.fr/instances#Revolver</uri>
      </binding>
    </result>
    <result>
      <binding name="objet">
        <uri>http://www.lamaisondumeurtre.fr/instances#PicAGlace</uri>
      </binding>
    </result>
    <result>
      <binding name="objet">
        <uri>http://www.lamaisondumeurtre.fr/instances#EauDeJavel</uri>
      </binding>
    </result>
    <result>
      <binding name="objet">
        <uri>http://www.lamaisondumeurtre.fr/instances#Lacet</uri>
      </binding>
    </result>
    <result>
      <binding name="objet">
        <uri>http://www.lamaisondumeurtre.fr/instances#Nokia3310</uri>
      </binding>
    </result>
  </results>
</sparql>
## Question 16 :

Personne ne se situe dans une pièce où a été posée l'arme du crime

### Quel objet est l'arme du crime?

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?objet  WHERE
	{
		data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
		?objet cluedo:objetDansPiece ?piece .
	    FILTER(not exists {
	    	?piece cluedo:pieceContientPersonne ?personne .
	    	?personne cluedo:estVivant false .
	    	?objet cluedo:objetDansPiece ?piece .
	    })
		FILTER(not exists {
	    	?piece cluedo:pieceContientPersonne ?personne .
	    })
	}

**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="objet"/>
	  </head>
	  <results>
	    <result>
	      <binding name="objet">
		<uri>http://www.lamaisondumeurtre.fr/instances#PicAGlace</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>

## Question 17 :

Le meurtrier se situe dans une pièce sans objet suspect

### Qui est le meurtrier? (augmentez la requête listant les suspects)

**Requete:**

	PREFIX cluedo: <http://www.lamaisondumeurtre.fr#>
	PREFIX data: <http://www.lamaisondumeurtre.fr/instances#>
	PREFIX xsd: <http://www.w3.org/2001/XMLSchema#>
	PREFIX xml: <http://www.w3.org/XML/1998/namespace>
	PREFIX rdf: <http://www.w3.org/1999/02/22-rdf-syntax-ns#>
	PREFIX rdfs: <http://www.w3.org/2000/01/rdf-schema#>
	PREFIX owl: <http://www.w3.org/2002/07/owl#>

	SELECT ?personne  WHERE
	{
	    data:LaMaisonDuMeurtre cluedo:maisonContientPiece ?piece .
	    ?piece cluedo:pieceContientPersonne ?personne .
	    ?personne cluedo:estVivant true .
	    FILTER (regex(str(?personne), "([A-Z].*e[A-Z])|(e$)", ""))
	    FILTER(not exists {
			?voisin cluedo:pieceContientPersonne ?mort .
			?mort cluedo:estVivant false .
			?piece cluedo:aPourPieceVoisine ?voisin .
	    })
	 	 FILTER(not exists {
			?objet cluedo:objetDansPiece ?piece .
	    })
	}
	
**Resultat:**

	<?xml version="1.0" encoding="UTF-8"?>
	<sparql xmlns="http://www.w3.org/2005/sparql-results#">
	  <head>
	    <variable name="personne"/>
	  </head>
	  <results>
	    <result>
	      <binding name="personne">
		<uri>http://www.lamaisondumeurtre.fr/instances#SophieStulle</uri>
	      </binding>
	    </result>
	  </results>
	</sparql>