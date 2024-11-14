# display
<!DOCTYPE html>
<html>
<head>
    <title>Control de Display de 32 Dígitos</title>
</head>
<body>
    <h2>Enviar Número al Display</h2>
    <form id="numberForm">
        <label for="number">Número (hasta 32 dígitos):</label>
        <input type="text" id="number" name="number" maxlength="32">
        <button type="button" onclick="sendNumber()">Enviar</button>
    </form>
    <p id="response"></p>

    <script>
        function sendNumber() {
            const number = document.getElementById("number").value;
            fetch(/setNumber?number=${number})
                .then(response => response.text())
                .then(data => {
                    document.getElementById("response").innerHTML = data;
                })
                .catch(error => {
                    document.getElementById("response").innerHTML = "Error enviando el número.";
                    console.error("Error:", error);
                });
        }
    </script>
</body>
</html>
