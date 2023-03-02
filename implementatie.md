# Implementatie

## Vertaalspecificaties

Zie ook Mapping UML - SKOS begrippen.

### «Domein» Registratiegegevens

| **Productmodel Gebouw** |                     |              | **Bronregistraties** |                |                     |              |
|-------------------------|---------------------|--------------|----------------------|----------------|---------------------|--------------|
| **objecttype**          | **attribuut**       | **datatype** | **Registratie**      | **objecttype** | **attribuut**       | **datatype** |
| Registratiegegevens     | tijdstipRegistratie | Tijdstip     | BAG                  | Pand           | tijdstipRegistratie | Tijdstip     |
|                         |                     |              | BGT                  | OverigBouwwerk | tijdstipRegistratie | Tijdstip     |
|                         | eindRegistratie     | Tijdstip     | BAG                  | Pand           | eindRegistratie     | Tijdstip     |
|                         |                     |              | BGT                  | OverigBouwwerk | eindRegistratie     | Tijdstip     |

### «Domein» Gebouw

| **Productmodel Gebouw** |                         |                      | **Bronregistraties** |                                                  |                                            |                                         |
|-------------------------|-------------------------|----------------------|----------------------|--------------------------------------------------|--------------------------------------------|-----------------------------------------|
| **objecttype**          | **attribuut**           | **datatype**         | **Registratie**      | **objecttype**                                   | **attribuut**                              | **datatype**                            |
| Gebouw                  | identificatie           | CharacterString {id} |                      | Nummeraanduiding                                 | identificatie                              | Objectnummering                         |
|                         | domein                  | CharacterString {id} |                      |                                                  |                                            |                                         |
|                         | type                    | CharacterString      | BAG                  | Verblijfsobject dat onderdeel uit maakt van Pand | gebruiksdoel                               | Gebruiksdoel                            |
|                         | bouwjaar                | Integer              | BAG                  | Pand                                             | Oorspronkjelijk bouwjaar                   | Jaar                                    |
|                         | sloopjaar               | Integer              | BAG                  | Pand                                             | beginGeldigheid van status ‘Pand gesloopt’ | Datum                                   |
|                         |                         |                      | BGT                  | OverigBouwwerk                                   | bgt-type plus-type                         | TypeOverigBouwwerk TypeOverBouwwerkPlus |
|                         |                         |                      | BRT                  | Gebouw                                           | typeGebouw                                 | TypeGebouw                              |
|                         | geometrie:bovenaanzicht | Vlak                 | BAG                  | Pand                                             | geometrie                                  | Vlak                                    |
|                         | geometrie:maaiveld      | MultiVlak            | BGT                  | Pand OverigBouwwerk                              | geometrie2d geometrie2d                    | Multivlak Vlak of Multivlak             |
|                         | geometrie:3d            | LOD2                 | 3D basisbestand      |                                                  |                                            |                                         |
|                         |                         |                      |                      |                                                  |                                            |                                         |

### Mapping BAG VBO gebruiksdoel naar PM Gebouw:type

#### BAG gebruiksdoelen

| **Waarden**             | **Omschrijving**                                                                                                                                                                                        |
|-------------------------|---------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------------|
| Woonfunctie             | Gebruiksfunctie voor het wonen                                                                                                                                                                          |
| Bijeenkomstfunctie      | Gebruiksfunctie voor het samenkomen van personen voor kunst, cultuur, godsdienst, communicatie, kinderopvang, het verstrekken van consumpties voor het gebruik ter plaatse of het aanschouwen van sport |
| Celfunctie              | Gebruiksfunctie voor het dwangverblijf van personen                                                                                                                                                     |
| Gezondheidszorgfunctie  | Gebruiksfunctie voor medisch onderzoek, verpleging, verzorging of behandeling                                                                                                                           |
| Industriefunctie        | Gebruiksfunctie voor het bedrijfsmatig bewerken of opslaan van materialen en goederen, of voor agrarische doeleinden                                                                                    |
| Kantoorfunctie          | Gebruiksfunctie voor administratie                                                                                                                                                                      |
| Logiesfunctie           | Gebruiksfunctie voor het bieden van recreatief verblijf of tijdelijk onderdak aan personen                                                                                                              |
| Onderwijsfunctie        | Gebruiksfunctie voor het geven van onderwijs                                                                                                                                                            |
| Sportfunctie            | Gebruiksfunctie voor het beoefenen van sport                                                                                                                                                            |
| Winkelfunctie           | Gebruiksfunctie voor het verhandelen van materialen, goederen of diensten                                                                                                                               |
| Overige gebruiksfunctie | Niet in dit lid benoemde gebruiksfunctie voor activiteiten waarbij het verblijven van personen een ondergeschikte rol speelt                                                                            |

#### Mapping BAG gebruiksdoel op Gebouw type

| **BAG Verblijfsobject: gebruiksdoel** | **PM Gebouw: type**        |
|---------------------------------------|----------------------------|
| Woonfunctie                           | woning                     |
| Bijeenkomstfunctie                    |                            |
| Celfunctie                            | gevangeniscomplex          |
| Gezondheidszorgfunctie                | medisch centrum            |
| Industriefunctie                      |                            |
| Kantoorfunctie                        | kantoorgebouw              |
| Logiesfunctie                         |                            |
| Onderwijsfunctie                      | universiteit, schoolgebouw |
| Sportfunctie                          |                            |
| Winkelfunctie                         |                            |
| Overige gebruiksfunctie               |                            |

#### Combinaties meerdere gebruiksdoelen naar Gebouw type

Twee of meer verblijfsobjecten maken onderdeel uit van een Pand:

| BAG Verblijfsobject: gebruiksdoel  | PM Gebouw: type |
|------------------------------------|-----------------|
| Woonfunctie Kantoorfunctie         | woonkantoor     |
| Woonfunctie gezondheidszorgfunctie | woonzorgcomplex |
|                                    |                 |
|                                    |                 |

### 

### «Domein» Adres

Zie <https://geonovum.github.io/WaU-UC2>.

## Prioriteit

#### Type

1.  bgt- of plus-type van BGT OverigBouwwerk
2.  type van BRT Gebouw
3.  gebruiksdoel van Verblijfsobject dat onderdeel uit maakt van BAG Pand

#### Registratiegegevens

tijdstipRegistratie en eindRegistratie :

Optie 1) waarde van BGT of BAG object met het oudste tijdstip; uitgangspunt de actualiteit van de gegevens is zo goed/slecht als de minst actuele?

Optie 2) waarde van BGT of BAG object met het nieuwste tijdstip; uitgangspunt de actualiteit van de gegevens is zo goed/slecht als de meest actuele?
