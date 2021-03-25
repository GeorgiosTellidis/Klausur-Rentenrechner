<html>
<head>
<meta http-equiv="Content-Type" content="text/html; charset=utf-8">
<title>Nachschüssige Rentenendwertrechner Klassenarbeit</title>
<script>
function fRentenrechner(){
var vZinssatz;
var vRente;
var vLaufzeit;
var vAusgabehtml;
var vStartjahr;
var vZinsfaktor;
var vZinsen
var vRentenendwert;
var vRentenendwert2;



vZinssatz = parseFloat(document.getElementById("idZinssatz").value);

vRente =  parseFloat(document.getElementById("idRente").value);

vLaufzeit = parseFloat(document.getElementById("idLaufzeit").value);

vZinsfaktor = 1 + vZinssatz / 100;

vStartjahr = 0;


vAusgabehtml = "";
vAusgabehtml = vAusgabehtml + "<table border=1>";

vAusgabehtml = vAusgabehtml + "<tr><th>Jahr</th><th>Kapital am 1.1.</th><th>Zinsen am 31.12.</th><th>Rente am 31.12.</th><th>Kapital am 31.12.</th></tr>";

while (vStartjahr <5) {
      vRentenendwert = vRente * (Math.pow(vZinsfaktor, vStartjahr) -1) / (vZinsfaktor-1);
      vZinsen = vRentenendwert * vZinssatz/100;
      vRentenendwert2 = vRentenendwert + vRente + vZinsen;

vAusgabehtml = vAusgabehtml + "<tr> <td>" + vStartjahr +  "</td> <td>" + vRentenendwert.toFixed(2) + " €" + "</td> <td>" + vZinsen.toFixed(2) + " €" + "</td> <td>" + vRente + " €"  + "</td> <td>" + vRentenendwert2.toFixed(2) + " €" + "</td> </tr>";


  vStartjahr ++;
}



vAusgabehtml = vAusgabehtml + "<tr> <td>" + vStartjahr + "</td> <td>" + vRentenendwert2.toFixed(2) +  "</td> </tr>";


document.getElementById("idAusgabe").innerHTML = vAusgabehtml;


}
</script>
</head>

<body>
    <h1>Nachschüssiger Rentenendwertrechner Klassenarbeit</h1>
    Zinssatz: <input id="idZinssatz" type="text" value="2" maxlength="10" size="10">%<br>
    Nachschüssige Rente <input id="idRente" type="text" value="100" maxlength="10" size="10">€<br>
  Laufzeit: <input id="idLaufzeit" type="text" value="5" maxlength="10" size="10">Jahre<br>

    <button onClick="fRentenrechner();">Berechnen</button><br>
<div id="idAusgabe"></div>

</body>
</html>
