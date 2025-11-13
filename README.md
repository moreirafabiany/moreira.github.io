# moreira.github.io
<!DOCTYPE html>
<html lang="it">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Anagrafica 2.0</title>
  <style>
    body {
      font-family: Arial, sans-serif;
      margin: 30px;
    }
    input, select {
      margin: 5px;
      padding: 5px;
    }
    table {
      border-collapse: collapse;
      margin-top: 20px;
      width: 80%;
    }
    th, td {
      border: 1px solid #333;
      padding: 8px;
      text-align: left;
    }
    th {
      background-color: #f0f0f0;
    }
    button {
      margin-top: 10px;
      padding: 6px 12px;
    }
  </style>
</head>
<body>

  <h2>Modulo Anagrafico 2.0</h2>


  <label>Nome:</label>
  <input type="text" id="nome" placeholder="Inserisci il nome"><br>

  <label>Cognome:</label>
  <input type="text" id="cognome" placeholder="Inserisci il cognome"><br>

  <label>Indirizzo:</label>
  <input type="text" id="indirizzo" placeholder="Inserisci l'indirizzo"><br>

  <label>Città:</label>
  <input type="text" id="citta" placeholder="Inserisci la città"><br>


  <label>Sesso:</label><br>
  <input type="radio" name="sesso" value="Maschio" id="maschio"> <label for="maschio">Maschio</label>
  <input type="radio" name="sesso" value="Femmina" id="femmina"> <label for="femmina">Femmina</label>
  <input type="radio" name="sesso" value="Altro" id="altro"> <label for="altro">Altro</label><br>

  <label>Diplomi posseduti:</label><br>
  <input type="checkbox" name="diploma" value="Licenza media"> Licenza media
  <input type="checkbox" name="diploma" value="Diploma superiore"> Diploma superiore
  <input type="checkbox" name="diploma" value="Laurea"> Laurea
  <input type="checkbox" name="diploma" value="Master"> Master<br>

  <label>Provincia:</label>
  <select id="provincia">
    <option value="">-- Seleziona provincia --</option>
    <option value="MI">Milano (MI)</option>
    <option value="RM">Roma (RM)</option>
    <option value="NA">Napoli (NA)</option>
    <option value="TO">Torino (TO)</option>
    <option value="FI">Firenze (FI)</option>
  </select><br>

  <label>Sport praticati (Ctrl + click per selezioni multiple):</label><br>
  <select id="sport" multiple size="5">
    <option value="Calcio">Calcio</option>
    <option value="Basket">Basket</option>
    <option value="Nuoto">Nuoto</option>
    <option value="Tennis">Tennis</option>
    <option value="Ciclismo">Ciclismo</option>
    <option value="Palestra">Palestra</option>
  </select><br>

  <button onclick="mostraDati()">Mostra in tabella</button>

  <div id="risultato"></div>

  <script>
    function mostraDati() {
      // Campi base
      const nome = document.getElementById("nome").value;
      const cognome = document.getElementById("cognome").value;
      const indirizzo = document.getElementById("indirizzo").value;
      const citta = document.getElementById("citta").value;
      const sesso = document.querySelector('input[name="sesso"]:checked')?.value || "Non specificato";

      const diplomi = Array.from(document.querySelectorAll('input[name="diploma"]:checked'))
        .map(el => el.value)
        .join(", ") || "Nessuno";

     
      const provincia = document.getElementById("provincia").value || "Non selezionata";

     
      const sportSelezionati = Array.from(document.getElementById("sport").selectedOptions)
        .map(opt => opt.value)
        .join(", ") || "Nessuno";

    
      const tabella = `
        <table>
          <tr>
            <th>Nome</th>
            <th>Cognome</th>
            <th>Indirizzo</th>
            <th>Città</th>
            <th>Sesso</th>
            <th>Diplomi</th>
            <th>Provincia</th>
            <th>Sport</th>
          </tr>
          <tr>
            <td>${nome}</td>
            <td>${cognome}</td>
            <td>${indirizzo}</td>
            <td>${citta}</td>
            <td>${sesso}</td>
            <td>${diplomi}</td>
            <td>${provincia}</td>
            <td>${sportSelezionati}</td>
          </tr>
        </table>
      `;

      document.getElementById("risultato").innerHTML = tabella;
    }
  </script>

</body>
</html>
