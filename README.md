<!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora de Derivadas Parciales</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/9.2.0/math.min.js"></script>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap">
  <style>
    body {
      background: linear-gradient(to bottom, #ff8c5b, #ff6491, #d3448e);
      color: #fff;
      font-family: 'Raleway', sans-serif;
    }

    .container {
      max-width: 500px;
      margin: 0 auto;
      background: linear-gradient(to bottom, #d3448e, #ff6491, #ff8c5b);
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
      margin-top: 30px;
      text-align: center;
    }

    h1 {
      color: #fff;
      text-shadow: 2px 2px 3px rgba(0, 0, 0, 0.5);
      font-size: 28px;
    }

    label {
      margin-top: 10px;
      color: #ffd6ba;
      font-size: 16px;
    }

    input {
      border: 1px solid #ffd6ba;
      border-radius: 8px;
      padding: 10px;
      width: 100%;
      color: #333;
      background-color: #fff;
      font-size: 16px;
    }

    button {
      width: 100%;
      margin-top: 20px;
      background: linear-gradient(to bottom, #fca636, #ff3b73, #d3448e);
      color: #fff;
      border: none;
      padding: 12px;
      border-radius: 25px;
      cursor: pointer;
      transition: background 0.3s ease;
      text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
      font-size: 16px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    }

    button:hover {
      background: linear-gradient(to bottom, #d3448e, #ff3b73, #ff8c5b);
    }

    .modal-content {
      background: linear-gradient(to bottom, #ff9e72, #ff6491, #d3448e);
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
    }

    .close {
      color: #ffd6ba;
    }

    /* Estilos adicionales para la segunda calculadora */
    hr {
      border: 1px solid #ffd6ba;
      margin-top: 30px;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Calculadora de Derivadas Parciales</h1>
    
    <label for="inputFuncion">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <button class="btn btn-primary" onclick="calcularDerivadasParciales()">Calcular Derivadas Parciales</button>

    <!-- Modal para mostrar el resultado -->
    <div class="modal" id="resultadoModal">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX"></p>
            <p id="resultadoDerivadaY"></p>
            <p id="resultadoDerivadaZ"></p>
            <p id="tipoDerivada"></p>
          </div>
        </div>
      </div>
    </div>

    <hr>

    <h1>Calculadora de Derivadas Parciales de Orden Superior</h1>
    
    <label for="inputFuncion2">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion2" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <label for="ordenDerivada">Ingresa el orden de la derivada:</label>
    <input type="number" class="form-control" id="ordenDerivada" placeholder="Orden">

    <button class="btn btn-primary" onclick="calcularDerivadaOrdenSuperior()">Calcular Derivada de Orden Superior</button>

    <!-- Modal para mostrar el resultado de la segunda calculadora -->
    <div class="modal" id="resultadoModal2">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado Derivada de Orden Superior</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX2"></p>
          </div>
        </div>
      </div>
    </div>

  </div>

  <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.1/dist/umd/popper.min.js"></script>
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

  <script>
    function calcularDerivadaOrdenSuperior() {
      var inputFuncion2 = document.getElementById("inputFuncion2").value;
      var ordenDerivada = parseInt(document.getElementById("ordenDerivada").value);

      try {
        // Utilizar math.js para evaluar la función y calcular la derivada de orden superior
        var expresion2 = math.parse(inputFuncion2);
        var derivadaOrdenSuperior = math.derivative(expresion2, 'x', { order: ordenDerivada });

        // Mostrar el resultado en el modal de la segunda calculadora
        document.getElementById("resultadoDerivadaX2").innerText = "Derivada de orden " + ordenDerivada + " respecto a x: " + derivadaOrdenSuperior.toString();
        $('#resultadoModal2').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }

    function calcularDerivadasParciales() {
      var inputFuncion = document.getElementById("inputFuncion").value;

      try {
        // Utilizar math.js para evaluar la función y calcular las derivadas parciales
        var expresion = math.parse(inputFuncion);
        var derivadaX = math.derivative(expresion, 'x');
        var derivadaY = math.derivative(expresion, 'y');
        var derivadaZ = math.derivative(expresion, 'z');

        // Mostrar los resultados en el modal
        document.getElementById("resultadoDerivadaX").innerText = "Derivada respecto a x: " + derivadaX.toString();
        document.getElementById("resultadoDerivadaY").innerText = "Derivada respecto a y: " + derivadaY.toString();
        document.getElementById("resultadoDerivadaZ").innerText = "Derivada respecto a z: " + derivadaZ.toString();
        $('#resultadoModal').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }
  </script>

</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora de Derivadas Parciales</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/9.2.0/math.min.js"></script>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap">
  <style>
    body {
      background: linear-gradient(to bottom, #ff8c5b, #ff6491, #d3448e);
      color: #fff;
      font-family: 'Raleway', sans-serif;
    }

    .container {
      max-width: 500px;
      margin: 0 auto;
      background: linear-gradient(to bottom, #d3448e, #ff6491, #ff8c5b);
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
      margin-top: 30px;
      text-align: center;
    }

    h1 {
      color: #fff;
      text-shadow: 2px 2px 3px rgba(0, 0, 0, 0.5);
      font-size: 28px;
    }

    label {
      margin-top: 10px;
      color: #ffd6ba;
      font-size: 16px;
    }

    input {
      border: 1px solid #ffd6ba;
      border-radius: 8px;
      padding: 10px;
      width: 100%;
      color: #333;
      background-color: #fff;
      font-size: 16px;
    }

    button {
      width: 100%;
      margin-top: 20px;
      background: linear-gradient(to bottom, #fca636, #ff3b73, #d3448e);
      color: #fff;
      border: none;
      padding: 12px;
      border-radius: 25px;
      cursor: pointer;
      transition: background 0.3s ease;
      text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
      font-size: 16px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    }

    button:hover {
      background: linear-gradient(to bottom, #d3448e, #ff3b73, #ff8c5b);
    }

    .modal-content {
      background: linear-gradient(to bottom, #ff9e72, #ff6491, #d3448e);
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
    }

    .close {
      color: #ffd6ba;
    }

    /* Estilos adicionales para la segunda calculadora */
    hr {
      border: 1px solid #ffd6ba;
      margin-top: 30px;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Calculadora de Derivadas Parciales</h1>
    
    <label for="inputFuncion">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <button class="btn btn-primary" onclick="calcularDerivadasParciales()">Calcular Derivadas Parciales</button>

    <!-- Modal para mostrar el resultado -->
    <div class="modal" id="resultadoModal">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX"></p>
            <p id="resultadoDerivadaY"></p>
            <p id="resultadoDerivadaZ"></p>
            <p id="tipoDerivada"></p>
          </div>
        </div>
      </div>
    </div>

    <hr>

    <h1>Calculadora de Derivadas Parciales de Orden Superior</h1>
    
    <label for="inputFuncion2">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion2" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <label for="ordenDerivada">Ingresa el orden de la derivada:</label>
    <input type="number" class="form-control" id="ordenDerivada" placeholder="Orden">

    <button class="btn btn-primary" onclick="calcularDerivadaOrdenSuperior()">Calcular Derivada de Orden Superior</button>

    <!-- Modal para mostrar el resultado de la segunda calculadora -->
    <div class="modal" id="resultadoModal2">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado Derivada de Orden Superior</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX2"></p>
          </div>
        </div>
      </div>
    </div>

  </div>

  <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.1/dist/umd/popper.min.js"></script>
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

  <script>
    function calcularDerivadaOrdenSuperior() {
      var inputFuncion2 = document.getElementById("inputFuncion2").value;
      var ordenDerivada = parseInt(document.getElementById("ordenDerivada").value);

      try {
        // Utilizar math.js para evaluar la función y calcular la derivada de orden superior
        var expresion2 = math.parse(inputFuncion2);
        var derivadaOrdenSuperior = math.derivative(expresion2, 'x', { order: ordenDerivada });

        // Mostrar el resultado en el modal de la segunda calculadora
        document.getElementById("resultadoDerivadaX2").innerText = "Derivada de orden " + ordenDerivada + " respecto a x: " + derivadaOrdenSuperior.toString();
        $('#resultadoModal2').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }

    function calcularDerivadasParciales() {
      var inputFuncion = document.getElementById("inputFuncion").value;

      try {
        // Utilizar math.js para evaluar la función y calcular las derivadas parciales
        var expresion = math.parse(inputFuncion);
        var derivadaX = math.derivative(expresion, 'x');
        var derivadaY = math.derivative(expresion, 'y');
        var derivadaZ = math.derivative(expresion, 'z');

        // Mostrar los resultados en el modal
        document.getElementById("resultadoDerivadaX").innerText = "Derivada respecto a x: " + derivadaX.toString();
        document.getElementById("resultadoDerivadaY").innerText = "Derivada respecto a y: " + derivadaY.toString();
        document.getElementById("resultadoDerivadaZ").innerText = "Derivada respecto a z: " + derivadaZ.toString();
        $('#resultadoModal').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }
  </script>

</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora de Derivadas Parciales</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/9.2.0/math.min.js"></script>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap">
  <style>
    body {
      background: linear-gradient(to bottom, #ff8c5b, #ff6491, #d3448e);
      color: #fff;
      font-family: 'Raleway', sans-serif;
    }

    .container {
      max-width: 500px;
      margin: 0 auto;
      background: linear-gradient(to bottom, #d3448e, #ff6491, #ff8c5b);
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
      margin-top: 30px;
      text-align: center;
    }

    h1 {
      color: #fff;
      text-shadow: 2px 2px 3px rgba(0, 0, 0, 0.5);
      font-size: 28px;
    }

    label {
      margin-top: 10px;
      color: #ffd6ba;
      font-size: 16px;
    }

    input {
      border: 1px solid #ffd6ba;
      border-radius: 8px;
      padding: 10px;
      width: 100%;
      color: #333;
      background-color: #fff;
      font-size: 16px;
    }

    button {
      width: 100%;
      margin-top: 20px;
      background: linear-gradient(to bottom, #fca636, #ff3b73, #d3448e);
      color: #fff;
      border: none;
      padding: 12px;
      border-radius: 25px;
      cursor: pointer;
      transition: background 0.3s ease;
      text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
      font-size: 16px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    }

    button:hover {
      background: linear-gradient(to bottom, #d3448e, #ff3b73, #ff8c5b);
    }

    .modal-content {
      background: linear-gradient(to bottom, #ff9e72, #ff6491, #d3448e);
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
    }

    .close {
      color: #ffd6ba;
    }

    /* Estilos adicionales para la segunda calculadora */
    hr {
      border: 1px solid #ffd6ba;
      margin-top: 30px;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Calculadora de Derivadas Parciales</h1>
    
    <label for="inputFuncion">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <button class="btn btn-primary" onclick="calcularDerivadasParciales()">Calcular Derivadas Parciales</button>

    <!-- Modal para mostrar el resultado -->
    <div class="modal" id="resultadoModal">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX"></p>
            <p id="resultadoDerivadaY"></p>
            <p id="resultadoDerivadaZ"></p>
            <p id="tipoDerivada"></p>
          </div>
        </div>
      </div>
    </div>

    <hr>

    <h1>Calculadora de Derivadas Parciales de Orden Superior</h1>
    
    <label for="inputFuncion2">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion2" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <label for="ordenDerivada">Ingresa el orden de la derivada:</label>
    <input type="number" class="form-control" id="ordenDerivada" placeholder="Orden">

    <button class="btn btn-primary" onclick="calcularDerivadaOrdenSuperior()">Calcular Derivada de Orden Superior</button>

    <!-- Modal para mostrar el resultado de la segunda calculadora -->
    <div class="modal" id="resultadoModal2">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado Derivada de Orden Superior</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX2"></p>
          </div>
        </div>
      </div>
    </div>

  </div>

  <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.1/dist/umd/popper.min.js"></script>
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

  <script>
    function calcularDerivadaOrdenSuperior() {
      var inputFuncion2 = document.getElementById("inputFuncion2").value;
      var ordenDerivada = parseInt(document.getElementById("ordenDerivada").value);

      try {
        // Utilizar math.js para evaluar la función y calcular la derivada de orden superior
        var expresion2 = math.parse(inputFuncion2);
        var derivadaOrdenSuperior = math.derivative(expresion2, 'x', { order: ordenDerivada });

        // Mostrar el resultado en el modal de la segunda calculadora
        document.getElementById("resultadoDerivadaX2").innerText = "Derivada de orden " + ordenDerivada + " respecto a x: " + derivadaOrdenSuperior.toString();
        $('#resultadoModal2').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }

    function calcularDerivadasParciales() {
      var inputFuncion = document.getElementById("inputFuncion").value;

      try {
        // Utilizar math.js para evaluar la función y calcular las derivadas parciales
        var expresion = math.parse(inputFuncion);
        var derivadaX = math.derivative(expresion, 'x');
        var derivadaY = math.derivative(expresion, 'y');
        var derivadaZ = math.derivative(expresion, 'z');

        // Mostrar los resultados en el modal
        document.getElementById("resultadoDerivadaX").innerText = "Derivada respecto a x: " + derivadaX.toString();
        document.getElementById("resultadoDerivadaY").innerText = "Derivada respecto a y: " + derivadaY.toString();
        document.getElementById("resultadoDerivadaZ").innerText = "Derivada respecto a z: " + derivadaZ.toString();
        $('#resultadoModal').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }
  </script>

</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora de Derivadas Parciales</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/9.2.0/math.min.js"></script>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap">
  <style>
    body {
      background: linear-gradient(to bottom, #ff8c5b, #ff6491, #d3448e);
      color: #fff;
      font-family: 'Raleway', sans-serif;
    }

    .container {
      max-width: 500px;
      margin: 0 auto;
      background: linear-gradient(to bottom, #d3448e, #ff6491, #ff8c5b);
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
      margin-top: 30px;
      text-align: center;
    }

    h1 {
      color: #fff;
      text-shadow: 2px 2px 3px rgba(0, 0, 0, 0.5);
      font-size: 28px;
    }

    label {
      margin-top: 10px;
      color: #ffd6ba;
      font-size: 16px;
    }

    input {
      border: 1px solid #ffd6ba;
      border-radius: 8px;
      padding: 10px;
      width: 100%;
      color: #333;
      background-color: #fff;
      font-size: 16px;
    }

    button {
      width: 100%;
      margin-top: 20px;
      background: linear-gradient(to bottom, #fca636, #ff3b73, #d3448e);
      color: #fff;
      border: none;
      padding: 12px;
      border-radius: 25px;
      cursor: pointer;
      transition: background 0.3s ease;
      text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
      font-size: 16px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    }

    button:hover {
      background: linear-gradient(to bottom, #d3448e, #ff3b73, #ff8c5b);
    }

    .modal-content {
      background: linear-gradient(to bottom, #ff9e72, #ff6491, #d3448e);
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
    }

    .close {
      color: #ffd6ba;
    }

    /* Estilos adicionales para la segunda calculadora */
    hr {
      border: 1px solid #ffd6ba;
      margin-top: 30px;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Calculadora de Derivadas Parciales</h1>
    
    <label for="inputFuncion">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <button class="btn btn-primary" onclick="calcularDerivadasParciales()">Calcular Derivadas Parciales</button>

    <!-- Modal para mostrar el resultado -->
    <div class="modal" id="resultadoModal">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX"></p>
            <p id="resultadoDerivadaY"></p>
            <p id="resultadoDerivadaZ"></p>
            <p id="tipoDerivada"></p>
          </div>
        </div>
      </div>
    </div>

    <hr>

    <h1>Calculadora de Derivadas Parciales de Orden Superior</h1>
    
    <label for="inputFuncion2">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion2" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <label for="ordenDerivada">Ingresa el orden de la derivada:</label>
    <input type="number" class="form-control" id="ordenDerivada" placeholder="Orden">

    <button class="btn btn-primary" onclick="calcularDerivadaOrdenSuperior()">Calcular Derivada de Orden Superior</button>

    <!-- Modal para mostrar el resultado de la segunda calculadora -->
    <div class="modal" id="resultadoModal2">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado Derivada de Orden Superior</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX2"></p>
          </div>
        </div>
      </div>
    </div>

  </div>

  <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.1/dist/umd/popper.min.js"></script>
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

  <script>
    function calcularDerivadaOrdenSuperior() {
      var inputFuncion2 = document.getElementById("inputFuncion2").value;
      var ordenDerivada = parseInt(document.getElementById("ordenDerivada").value);

      try {
        // Utilizar math.js para evaluar la función y calcular la derivada de orden superior
        var expresion2 = math.parse(inputFuncion2);
        var derivadaOrdenSuperior = math.derivative(expresion2, 'x', { order: ordenDerivada });

        // Mostrar el resultado en el modal de la segunda calculadora
        document.getElementById("resultadoDerivadaX2").innerText = "Derivada de orden " + ordenDerivada + " respecto a x: " + derivadaOrdenSuperior.toString();
        $('#resultadoModal2').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }

    function calcularDerivadasParciales() {
      var inputFuncion = document.getElementById("inputFuncion").value;

      try {
        // Utilizar math.js para evaluar la función y calcular las derivadas parciales
        var expresion = math.parse(inputFuncion);
        var derivadaX = math.derivative(expresion, 'x');
        var derivadaY = math.derivative(expresion, 'y');
        var derivadaZ = math.derivative(expresion, 'z');

        // Mostrar los resultados en el modal
        document.getElementById("resultadoDerivadaX").innerText = "Derivada respecto a x: " + derivadaX.toString();
        document.getElementById("resultadoDerivadaY").innerText = "Derivada respecto a y: " + derivadaY.toString();
        document.getElementById("resultadoDerivadaZ").innerText = "Derivada respecto a z: " + derivadaZ.toString();
        $('#resultadoModal').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }
  </script>

</body>
</html><!DOCTYPE html>
<html lang="en">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Calculadora de Derivadas Parciales</title>
  <link rel="stylesheet" href="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/css/bootstrap.min.css">
  <script src="https://cdnjs.cloudflare.com/ajax/libs/mathjs/9.2.0/math.min.js"></script>
  <link rel="stylesheet" href="https://fonts.googleapis.com/css2?family=Raleway:wght@400;700&display=swap">
  <style>
    body {
      background: linear-gradient(to bottom, #ff8c5b, #ff6491, #d3448e);
      color: #fff;
      font-family: 'Raleway', sans-serif;
    }

    .container {
      max-width: 500px;
      margin: 0 auto;
      background: linear-gradient(to bottom, #d3448e, #ff6491, #ff8c5b);
      padding: 20px;
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
      margin-top: 30px;
      text-align: center;
    }

    h1 {
      color: #fff;
      text-shadow: 2px 2px 3px rgba(0, 0, 0, 0.5);
      font-size: 28px;
    }

    label {
      margin-top: 10px;
      color: #ffd6ba;
      font-size: 16px;
    }

    input {
      border: 1px solid #ffd6ba;
      border-radius: 8px;
      padding: 10px;
      width: 100%;
      color: #333;
      background-color: #fff;
      font-size: 16px;
    }

    button {
      width: 100%;
      margin-top: 20px;
      background: linear-gradient(to bottom, #fca636, #ff3b73, #d3448e);
      color: #fff;
      border: none;
      padding: 12px;
      border-radius: 25px;
      cursor: pointer;
      transition: background 0.3s ease;
      text-shadow: 1px 1px 2px rgba(0, 0, 0, 0.3);
      font-size: 16px;
      box-shadow: 0 0 10px rgba(0, 0, 0, 0.3);
    }

    button:hover {
      background: linear-gradient(to bottom, #d3448e, #ff3b73, #ff8c5b);
    }

    .modal-content {
      background: linear-gradient(to bottom, #ff9e72, #ff6491, #d3448e);
      border-radius: 15px;
      box-shadow: 0 0 30px rgba(0, 0, 0, 0.3);
    }

    .close {
      color: #ffd6ba;
    }

    /* Estilos adicionales para la segunda calculadora */
    hr {
      border: 1px solid #ffd6ba;
      margin-top: 30px;
    }
  </style>
</head>
<body>

  <div class="container">
    <h1>Calculadora de Derivadas Parciales</h1>
    
    <label for="inputFuncion">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <button class="btn btn-primary" onclick="calcularDerivadasParciales()">Calcular Derivadas Parciales</button>

    <!-- Modal para mostrar el resultado -->
    <div class="modal" id="resultadoModal">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX"></p>
            <p id="resultadoDerivadaY"></p>
            <p id="resultadoDerivadaZ"></p>
            <p id="tipoDerivada"></p>
          </div>
        </div>
      </div>
    </div>

    <hr>

    <h1>Calculadora de Derivadas Parciales de Orden Superior</h1>
    
    <label for="inputFuncion2">Ingresa la función:</label>
    <input type="text" class="form-control" id="inputFuncion2" placeholder="Ejemplo: x^2 + y^3 + z^4">

    <label for="ordenDerivada">Ingresa el orden de la derivada:</label>
    <input type="number" class="form-control" id="ordenDerivada" placeholder="Orden">

    <button class="btn btn-primary" onclick="calcularDerivadaOrdenSuperior()">Calcular Derivada de Orden Superior</button>

    <!-- Modal para mostrar el resultado de la segunda calculadora -->
    <div class="modal" id="resultadoModal2">
      <div class="modal-dialog">
        <div class="modal-content">
          <div class="modal-header">
            <h4 class="modal-title">Resultado Derivada de Orden Superior</h4>
            <button type="button" class="close" data-dismiss="modal">&times;</button>
          </div>
          <div class="modal-body">
            <p id="resultadoDerivadaX2"></p>
          </div>
        </div>
      </div>
    </div>

  </div>

  <script src="https://code.jquery.com/jquery-3.5.1.slim.min.js"></script>
  <script src="https://cdn.jsdelivr.net/npm/@popperjs/core@2.9.1/dist/umd/popper.min.js"></script>
  <script src="https://stackpath.bootstrapcdn.com/bootstrap/4.5.2/js/bootstrap.min.js"></script>

  <script>
    function calcularDerivadaOrdenSuperior() {
      var inputFuncion2 = document.getElementById("inputFuncion2").value;
      var ordenDerivada = parseInt(document.getElementById("ordenDerivada").value);

      try {
        // Utilizar math.js para evaluar la función y calcular la derivada de orden superior
        var expresion2 = math.parse(inputFuncion2);
        var derivadaOrdenSuperior = math.derivative(expresion2, 'x', { order: ordenDerivada });

        // Mostrar el resultado en el modal de la segunda calculadora
        document.getElementById("resultadoDerivadaX2").innerText = "Derivada de orden " + ordenDerivada + " respecto a x: " + derivadaOrdenSuperior.toString();
        $('#resultadoModal2').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }

    function calcularDerivadasParciales() {
      var inputFuncion = document.getElementById("inputFuncion").value;

      try {
        // Utilizar math.js para evaluar la función y calcular las derivadas parciales
        var expresion = math.parse(inputFuncion);
        var derivadaX = math.derivative(expresion, 'x');
        var derivadaY = math.derivative(expresion, 'y');
        var derivadaZ = math.derivative(expresion, 'z');

        // Mostrar los resultados en el modal
        document.getElementById("resultadoDerivadaX").innerText = "Derivada respecto a x: " + derivadaX.toString();
        document.getElementById("resultadoDerivadaY").innerText = "Derivada respecto a y: " + derivadaY.toString();
        document.getElementById("resultadoDerivadaZ").innerText = "Derivada respecto a z: " + derivadaZ.toString();
        $('#resultadoModal').modal('show');
      } catch (error) {
        alert("Error al evaluar la función.");
      }
    }
  </script>

</body>
</html>
