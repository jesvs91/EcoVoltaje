<!DOCTYPE html>
<html lang="es">
<cabeza>
  <meta conjunto de caracteres="UTF-8">
  <meta name="viewport" content="ancho=ancho-del-dispositivo, escala-inicial=1.0">
  <title>EcoVoltaje - Calculadora de Consumo de Energía</title>
  <estilo>
    cuerpo {
      color de fondo: #f0f0f0;
      color: #333;
      familia de fuentes: Arial, sans-serif;
    }

    .contenedor-calculadora {
      relleno: 20px;
      borde: 1px sólido #ccc;
      radio del borde: 5px;
      color de fondo: #fff;
      ancho máximo: 600px;
      margen: 20px automático;
      caja-sombra: 0 0 10px rgba(0, 0, 0, 0.1);
    }

    .título {
      peso de fuente: negrita;
      alinear texto: centro;
      tamaño de fuente: 24px;
      margen inferior: 20px;
    }

    .campo de entrada {
      peso de fuente: negrita;
      color de fondo: #f0f0f0;
      borde: ninguno;
      relleno: 8px 12px;
      radio del borde: 5px;
      margen: 5px 0;
      ancho: calc(100% - 24px);
    }

    .dos columnas {
      pantalla: cuadrícula;
      columnas de plantilla de cuadrícula: 1fr 1fr;
      espacio: 10px;
    }

    .calcular-btn, .copiar-btn {
      peso de fuente: negrita;
      color: #fff;
      color de fondo: #0077b6;
      borde: ninguno;
      relleno: 12px 24px;
      radio del borde: 5px;
      cursor: puntero;
      tamaño de fuente: 16px;
      margen superior: 10px;
      ancho: 100%;
    }

    .sección de resultados {
      margen superior: 20px;
      relleno: 15px;
      color de fondo: #0077b6;
      radio del borde: 5px;
      color: #fff;
    }

    .logotipo {
      pantalla: bloque;
      margen: 0 auto 20px;
      ancho máximo: 150px;
    }
  </estilo>
</cabeza>
<cuerpo>
  <div class="contenedor-calculadora">
    <img src="URL_DEL_LOGO" alt="EcoVoltaje" class="logo">
    <h2 class="title">EcoVoltaje - Calculadora de Consumo de Energía</h2>

    <form id="formulario-calculadora">
      <div class="dos-columnas">
        <input type="number" id="bimestre1" placeholder="Bimestre 1" class="input-field">
        <tipo de entrada="número" id="bimestre2" marcador de posición="Bimestre 2" clase="campo de entrada">
        <tipo de entrada="número" id="bimestre3" marcador de posición="Bimestre 3" clase="campo de entrada">
        <tipo de entrada="número" id="bimestre4" marcador de posición="Bimestre 4" clase="campo de entrada">
        <input type="número" id="bimestre5" placeholder="Bimestre 5" class="campo-de-entrada">
        <tipo de entrada="número" id="bimestre6" marcador de posición="Bimestre 6" clase="campo de entrada">
      </div>

      <label for="opcion">Seleccione la opción para dividir:</label>
      <select id="opcion" clase="campo-de-entrada">
        <opción valor="585">585</opción>
        <opción valor="605">605</opción>
      </seleccionar>

      <button type="button" class="calculate-btn" onclick="calculateResults()">Calculadora</button>
      <button type="button" class="copy-btn" onclick="copyResults()">Copiar resultado</button>
    </formulario>

    <div id="resultados" class="sección-de-resultados">
      <h3 class="subtitle">Resultados</h3>
      <p id="texto-resultado"></p>
    </div>
  </div>

  <guión>
    función calcularResultados() {
      const bimestres = [
        parseFloat(documento.getElementById('bimestre1').valor),
        parseFloat(document.getElementById('bimestre2').valor),
        parseFloat(documento.getElementById('bimestre3').valor),
        parseFloat(documento.getElementById('bimestre4').valor),
        parseFloat(document.getElementById('bimestre5').valor),
        parseFloat(documento.getElementById('bimestre6').valor)
      ];

      const opcion = parseFloat(document.getElementById('opcion').valor);

      const sumaTotal = bimestres.reduce((acc, val) => acc + val, 0);
      constante promedio = sumaTotal / 12;
      const resultado = (promedio/41) * 330/opcion;

      const resultadoTexto = `Total de energía consumida en 6 bimestres: ${sumaTotal} kWh
Promedio bimestral: ${promedio.toFixed(2)} kWh
Paneles necesarios: ${resultado.toFixed(2)}`;

      const bimestreStats = `Bimestre 1: ${bimestre[0]} kWh
Bimestre 2: ${bimestres[1]} kWh
Bimestre 3: ${bimestres[2]} kWh
Bimestre 4: ${bimestres[3]} kWh
Bimestre 5: ${bimestres[4]} kWh
Bimestre 6: ${bimestres[5]} kWh`;

      document.getElementById('texto-resultado').innerText = resultadoTexto + '\n\n' + bimestreStats;
    }

    función copyResults() {
      const textoResultado = document.getElementById('texto-resultado').innerText;
      navigator.clipboard.writeText(textoResultado).then(() => {
        alert('Resultado copiado al portapapeles');
      });
    }
  </script>
</cuerpo>
</html>
