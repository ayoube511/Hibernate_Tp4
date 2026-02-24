# TP Hibernate – Stratégies d'Héritage JPA

Projet démontrant les 3 stratégies d'héritage JPA/Hibernate :
- SINGLE_TABLE
- JOINED
- TABLE_PER_CLASS

## Objectifs

- Comprendre les différences entre les stratégies
- Voir les tables générées et les requêtes SQL
- Tester les opérations CRUD et les requêtes polymorphiques

## Technologies

- Java 8+
- Maven
- JPA 2.2 + Hibernate 5.6
- H2 (in-memory)
- SLF4J

## Diagramme de classe 
+-------------------+             +-------------------+             +-------------------+
|    <<abstract>>   |             |    <<abstract>>   |             |    <<abstract>>   |
|     Vehicule      |             |      Employe      |             |      Produit      |
| ----------------- |             | ----------------- |             | ----------------- |
| - id: Long        |             | - id: Long        |             | - id: Long        |
| - marque          |             | - nom             |             | - nom             |
| - modele          |             | - prenom          |             | - prix            |
| - anneeFabrication|             | - email           |             | - description     |
| - prix            |             | - dateEmbauche    |             | - dateCreation    |
| @Inheritance      |             | @Inheritance      |             | @Inheritance      |
| (SINGLE_TABLE)    |             | (JOINED)          |             | (TABLE_PER_CLASS) |
| @Discriminator... |             |                   |             |                   |
+-------------------+             +-------------------+             +-------------------+
          ▲                                 ▲                                 ▲
          │                                 │                                 │
   +-------------+                    +-------------+                   +-------------+
   |   Voiture   |                    | Developpeur |                   |   Livre     |
   | -------------|                    | -------------|                   | -------------|
   | - nbPortes  |                    | - langage    |                   | - auteur    |
   | - clim      |                    | - specialite |                   | - isbn      |
   | - carburant |                    | - anneesExp  |                   | - nbPages   |
   | @DiscValue  |                    | @Table       |                   | @Table      |
   |  ("VOITURE")|                    | ("developpeurs")                | ("livres")  |
   +-------------+                    +-------------+                   +-------------+

          ▲                                 ▲                                 ▲
          │                                 │                                 │
   +-------------+                    +-------------+                   +-------------+
   |    Moto     |                    |   Manager   |                   | Electronique|
   | -------------|                    | -------------|                   | -------------|
   | - cylindree |                    | - service    |                   | - marque    |
   | - trans     |                    | - nbSubord.  |                   | - modele    |
   | @DiscValue  |                    | - bonus      |                   | - garantie  |
   |   ("MOTO")  |                    | @Table       |                   | - carac.    |
   +-------------+                    | ("managers") |                   | @Table      |
                                      +-------------+                   | ("electroniques")|
                                                                          +-------------+
## Resultat des tests 
- Stratégie SINGLE_TABLE
  <img width="1732" height="765" alt="image" src="https://github.com/user-attachments/assets/4891cd95-c096-4cff-a057-2ef9c930283f" />
  <img width="1737" height="669" alt="image" src="https://github.com/user-attachments/assets/1c8647e8-db02-4687-a1fb-3c08ad3a4f98" />
  <img width="1733" height="614" alt="image" src="https://github.com/user-attachments/assets/5b0f5e59-29df-43ed-be3e-1ab61bc75349" />
  <img width="1725" height="563" alt="image" src="https://github.com/user-attachments/assets/f0eea2bc-3a28-4e84-aacd-5c761e7a62b0" />
  <img width="1726" height="505" alt="image" src="https://github.com/user-attachments/assets/194a239c-f865-460a-ac8c-e97e592f9b50" />

- Stratégie JOINED
  <img width="1733" height="729" alt="image" src="https://github.com/user-attachments/assets/34ad894b-ab20-45fd-b25d-24c49004d732" />
  <img width="1729" height="688" alt="image" src="https://github.com/user-attachments/assets/e3d73896-2a49-4d8f-bab8-96418836d29c" />
  <img width="1729" height="756" alt="image" src="https://github.com/user-attachments/assets/d31df64b-f1fa-4c13-b00b-44ea4f5e4b3e" />
  <img width="1733" height="715" alt="image" src="https://github.com/user-attachments/assets/a01b4509-4dbb-43a5-8c14-aee2de6b0d10" />
  <img width="1727" height="716" alt="image" src="https://github.com/user-attachments/assets/86eb9c1b-1d5d-44cb-b80a-9ffd495d07b4" />

- Stratégie TABLE_PER_CLASSE
   <img width="1735" height="667" alt="image" src="https://github.com/user-attachments/assets/b5a7ab04-2ad5-472d-8992-714df24c845b" />
   <img width="1728" height="772" alt="image" src="https://github.com/user-attachments/assets/717f8466-5b97-4e97-b271-88b69fc5b2b6" />
   <img width="1734" height="792" alt="image" src="https://github.com/user-attachments/assets/556e08a4-9ec0-4472-9481-2b634a768c94" />
   <img width="1735" height="786" alt="image" src="https://github.com/user-attachments/assets/3003e676-0846-4db1-b00e-35685d17c0c3" />
   <img width="1748" height="697" alt="image" src="https://github.com/user-attachments/assets/57dd838a-bd1f-4209-ad95-b55d0ad959af" />
   

   















    
