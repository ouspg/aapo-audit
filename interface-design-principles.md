# Design

* Salasanoja (ja käyttäjätunnuksia) ei talleteta järjestelmään
* Ulos näkyvällä osalla ei ole yhteyttä tuotannon järjestelmiin ja niiden kantoihin
* Oman tilatietokannan käyttötunnusten oikeudet eroteltu tarpeen mukaan (select, insert, update)
* Taustajärjestelmän tietokantakysely tunnuksella vain rajoitettu (select) oikeus
* Aapo-rajapinnassa ei voi vaihtaa käyttäjän identiteettiä. Käyttäjä voi olla vain 'minä', joka määräytyy kirjautumisen yhteydessä.
* Toiminnot vaativat parametrina kerta-avaimen (dev_id, stu_id, tra_id)
* Kaikki järjestelmään kohdistuvat pyynnöt talletetaan lokiin.
* Ulkoa tulevat pyynnöt koostetaan uudelleen ennen kuin ne välitetään taustajärjestelmälle (arvojen tarkastus)
* Rajapintapalvelimilla (1 ja 2) ei ole hakemistoja, joihin olisi kirjoitusoikeuksia.
* Yliopiston palomuurista näkyy ainoastaan edustapalvelin (portti 443).
* Taustapalvelimen (2) portti 443 kuuntelee pelkästään edustapalvelinta (1).
