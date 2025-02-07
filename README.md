# ITSR
Conociendo el mundo
<html lang="es">
<head>
  <meta charset="UTF-8">
  <meta name="viewport" content="width=device-width, initial-scale=1.0">
  <title>Explorando el Mundo</title>
  <link href="https://fonts.googleapis.com/css2?family=Montserrat:wght@400;700&family=Playfair+Display:wght@700&display=swap" rel="stylesheet">
  <style>
      body {
          display: flex;
          flex-direction: column;
          align-items: center;
          justify-content: center;
          height: 100vh;
          margin: 0;
          font-family: 'Montserrat', sans-serif;
          color: #ffffff;
          background-color: #eaeaea;
          overflow: hidden;
      }

      .fondo {
          position: fixed; 
          top: 0;
          left: 0;
          width: 100%;
          height: 100%;
          z-index: 0;
          background: url('https://as2.ftcdn.net/jpg/00/92/14/59/1000_F_92145979_r5TsRD5ZlvwRq0biwHmlY9B1XrWxwfue.jpg') no-repeat center center fixed;
          background-size: cover;
          filter: blur(5px);
      }

      #mensaje {
          font-size: 3em;
          margin-bottom: 20px;
          font-family: 'Playfair Display', serif;
          text-shadow: 2px 2px 4px rgba(0, 0, 0, 0.7);
          z-index: 1;
          position: relative;
      }

      button {
          padding: 15px 30px;
          font-size: 1.2em;
          background-color: #663a07;
          color: #ffffff;
          border: none;
          border-radius: 25px;
          cursor: pointer;
          box-shadow: 0 4px 20px rgba(0, 0, 0, 0.3);
          transition: background-color 0.3s, transform 0.3s;
          font-family: 'Montserrat', sans-serif;
          font-weight: bold;
          z-index: 1;
          position: relative;
          margin: 10px;
      }

      button:hover {
          background-color: #482607;
          transform: scale(1.05);
      }

      .contenedor-imagenes {
          height: 100vh; 
          position: relative;
          z-index: 1;
          overflow-y: auto; 
          padding: 20px;
      }

      .imagenes {
          display: flex;
          flex-wrap: wrap;
          justify-content: center;
          padding-top: 20px;
      }

      .imagenes div {
          margin: 10px; 
          text-align: center; 
      }

      .imagenes img {
          width: 200px; 
          height: 150px; 
          object-fit: cover; 
          cursor: pointer;
          transition: transform 0.3s;
      }

      .imagenes img:hover {
          transform: scale(1.1);
      }

      .imagen-seleccionada {
          text-align: center;
          margin-top: 20px;
      }

      .imagen-seleccionada img {
          width: 80%; 
          margin-top: 20px;
      }

      .introduccion {
          margin-top: 20px;
          font-size: 1.2em;
          color: #ffffff;
          max-width: 600px; 
          margin-left: auto;
          margin-right: auto;
      }
  </style>
</head>
<body>
  <div class="fondo"></div>
  <div id="mensaje">¡....BIENVENIDO.....!</div>
  <div id="mensaje">La aventura inicia aquí</div>
  <button onclick="ingresarNombre()">Da click para comenzar</button>

  <script>
      let nombreUsuario;
      let imagenes = [
          {
              url: "https://marketingsimulator.net/mhernandez/wp-content/uploads/sites/140/2016/06/Mitad-del-Mundo1-672x372.jpg",
              descripcion: "Mitad del Mundo, Ecuador",
              info: "Un lugar emblemático en Ecuador donde la línea ecuatorial divide el hemisferio norte y sur."
          },
          {
              url: "https://media.viajando.travel/p/3f600e17dd8b89dd3aa9b82f54b7b6c2/adjuntos/236/imagenes/000/662/0000662813/412x232/smart/shutterstock_786312625-espana-madridjpg.jpg",
              descripcion: "Madrid, España",
              info: "La capital de España, conocida por su rica historia y cultura."
          },
          {
              url: "https://64.media.tumblr.com/8064ae189e2a062fee5f4297a5c0b7d3/tumblr_p84886x31s1um9b75o1_1280.jpg",
              descripcion: "Lugares de Perú",
              info: "Conocido por su biodiversidad y bellezas naturales."
          },
          {
              url: "https://www.saborusa.com/wp-content/uploads/2022/12/Foto-esc%C3%A9nica-del-pueblo-pesquero-de-invierno-con-luces-del-norte-1280x1024.jpg",
              descripcion: "Luces del Norte",
              info: "Un espectáculo natural que ilumina el cielo en el invierno."
          },
          {
              url: "https://upload.wikimedia.org/wikipedia/commons/thumb/c/ca/Machu_Picchu%2C_Peru_%282018%29.jpg/640px-Machu_Picchu%2C_Peru_%282018%29.jpg",
              descripcion: "Machu Picchu, Perú",
              info: "Una de las maravillas del mundo, ubicada en los Andes peruanos."
          },
          {
              url: "https://ichef.bbci.co.uk/ace/ws/640/cpsprodpb/ef90/live/d3367b00-c22b-11ef-aff0-072ce821b6ab.jpg.webp",
              descripcion: "La Torre Eiffel, Francia",
              info: "Símbolo icónico de París, Francia, y una de las estructuras más reconocibles del mundo."
          },
          {
              url: "https://www.paises.net/wp-content/uploads/2022/11/francia-pais.jpg",
              descripcion: "Francia",
              info: "Conocida por su arte, gastronomía y paisajes hermosos."
          },
          {
              url: "https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcTZ46MdKTzgzqrT4xctyvoxbnbZXuT85IMonw&s",
              descripcion: "Playa de Cancún, México",
              info: "Famosa por sus playas de arena blanca y aguas cristalinas."
          },
          {
              url: "https://shorthand-social.imgix.net/prod/story/j2foA05UG/media/50ecb3101ebd11e59bd1bd8388cbd6e2/original.jpg?w=1500&h=1500&fit=clip&fm=jpg&q=75",
              descripcion: "Naturaleza de Costa Rica",
              info: "Famoso por su biodiversidad y paisajes impresionantes."
          },
          {
              url: "https://efeagro.com/wp-content/uploads/2022/06/48695_5.jpg",
              descripcion: "Paisajes de Italia",
              info: "Italia es famosa por su historia, arte y paisajes naturales."
          }
      ];
      let indiceImagenActual = 0;

      function ingresarNombre() {
          nombreUsuario = prompt("Por favor, ingrese su nombre:");
          nombreUsuario = nombreUsuario.charAt(0).toUpperCase() + nombreUsuario.slice(1).toLowerCase();
          mostrarImagenes();
      }

      function mostrarImagenes() {
          document.body.innerHTML = `
              <div class="fondo"></div>
              <div id="mensaje">¡Bienvenido, ${nombreUsuario}!</div>
              <div class="contenedor-imagenes">
                  <div class="imagenes">
                      ${imagenes.map((img, index) => `
                          <div>
                              <img src="${img.url}" onclick="verImagen(${index})" alt="Imagen ${index + 1}">
                              <p>${img.descripcion}</p>
                          </div>
                      `).join('')}
                  </div>
              </div>
          `;
      }

      function verImagen(indice) {
          indiceImagenActual = indice;
          const { url, descripcion, info } = imagenes[indiceImagenActual];
          document.body.innerHTML = `
              <div class="fondo"></div>
              <div class="imagen-seleccionada">
                  <img src="${url}" alt="Imagen Seleccionada">
                  <h2>${descripcion}</h2>
                  <p class="introduccion">${info}</p>
                  <button onclick="anteriorImagen()">Anterior</button>
                  <button onclick="siguienteImagen()">Siguiente</button>
                  <button onclick="mostrarImagenes()">Regresar</button>
              </div>
          `;
      }

      function anteriorImagen() {
          if (indiceImagenActual > 0) {
              indiceImagenActual--;
          } else {
              indiceImagenActual = imagenes.length - 1; // Volver al último si está en el primero
          }
          verImagen(indiceImagenActual);
      }

      function siguienteImagen() {
          if (indiceImagenActual < imagenes.length - 1) {
              indiceImagenActual++;
          } else {
              indiceImagenActual = 0; // Volver al primero si está en el último
          }
          verImagen(indiceImagenActual);
      }
  </script>
</body>
</html>
