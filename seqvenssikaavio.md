```mermaid
sequenceDiagram
  
  note left of Asiakas: asiakas lataa sivun
  Asiakas->>Palvelin: Http GET request url...
  activate Palvelin
  Palvelin-->>Asiakas: Http response header (HTML document)
  deactivate Palvelin
  Asiakas->>Palvelin: GET pyyntö css tyylitiedosto url...
  activate Palvelin
  Palvelin-->>Asiakas: CSS tiedosto
  deactivate Palvelin
  Asiakas->>Palvelin: GET pyyntö javascript tiedosto url...
  activate Palvelin
  Palvelin-->>Asiakas: javascript tiedosto
  deactivate Palvelin
  Asiakas->>Palvelin: Javascript suorittaa GET pyynnön muistiinpanotiedostolle
  activate Palvelin
  Palvelin-->>Asiakas: Palauttaa JSON objektin
  deactivate Palvelin
  note right of Asiakas: selain suorittaa javascript funktion ja renderöi tiedot sivulle
  activate Asiakas
  note right of Asiakas: asiakas kirjoittaa lomakekenttään ja lähettää lomakkeen "save" nappia painamalla
  Asiakas->>Palvelin: Lähettää POST metodilla pyynnön ja syötetyn datan palvelimelle
  deactivate Asiakas
  activate Palvelin
  loop redirect and save new note
    Palvelin->>Palvelin: suorittaa tallennusmetodin ja uudelleen ohjauksen
  end
  Palvelin-->>Asiakas: Http response header
  deactivate Palvelin
  Asiakas->>Palvelin: GET pyyntö css tyylitiedosto url...
  activate Palvelin
  Palvelin-->>Asiakas: CSS tiedosto
  deactivate Palvelin
  Asiakas->>Palvelin: GET pyyntö javascript tiedosto url...
  activate Palvelin
  Palvelin-->>Asiakas: javascript tiedosto
  deactivate Palvelin
  Asiakas->>Palvelin: Javascript suorittaa GET pyynnön muistiinpanotiedostolle
  activate Palvelin
  Palvelin-->>Asiakas: Palauttaa JSON objektin
  deactivate Palvelin
  note left of Asiakas: sivu uudelleen latautuu ja json objekti sisältää käyttäjän tallentaman tiedon
  ```
