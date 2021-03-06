﻿ # Practica08-LaberintoVR


 Desarrollo de una aplicación de realidad virtual usando la herramienta Unity y desplegada en un dispositivo móvil Android.

<h2>OBJETIVO ALCANZADO:</h2>
 <ul>
  <li>Experimenta con aplicaciones de realidad virtual.</li>
  <li>Experimenta con aplicaciones de realidad aumentada.</li>
  <li>Distingue la diferencia entre tecnologías de realidad virtual y realidad aumentada.</li>
 </ul>

 

 <p>1.	El desarrollo de cada uno de los requerimientos antes descritos.
Crear la GVR Camera Rig
Durante este paso, crearemos la cámara VR incluyendo el GvrEditorEmulator en la escena y configurando la cámara. 
Se agrego a la jerarquía el objeto prefab GrvEditorEmulator a la escena, y convertir como hijo el objeto Main Camera y mover a una posición para mejor visualización.
-	Se recomienda la posición de 0, 3, 35 y Rotación: 0, 180, 0.
</p>

	<img width="45%" src="Imagenes/Foto1.png"></img>

	

 <p>-	Ingrese al modo de juego y use Alt + Mouse y Ctrl + Mouse para rotar e inclinar el ángulo de visión de la cámara.</p>

	<img width="45%" src="Imagenes/Foto2.png"></img>

<p>GvrEditorEmulator prefab.- Proporciona emulación en el editor del movimiento del cabezal y la entrada del controlador.

Preparando la escena para la interacción
Durante este paso, prepararemos la escena para la interacción configurando el puntero, el emisor de rayos y el sistema de eventos, y luego probaremos el sistema de punto de referencia incluido (waypoint).
GvrReticlePointer.- Proporciona un puntero de retícula basado en la mirada que admite la entrada de botones del visor de cartón. Debe ser hijo de la cámara principal, para que el puntero y la retícula sigan la mirada del usuario
</p>

 <p>	-	Aumentar el valor de Distancia máxima de retícula para el GvrReticlePointer del valor predeterminado de 10 a 20.</p>

	<img width="45%" src="Imagenes/Foto4.png"></img>

 <p>Hacer que los objetos del juego sean interactivos
Durante este paso haremos que la Moneda, la Llave y la Puerta sean interactivas añadiéndoles componentes de disparadores y eventos.
El componente coin debe contener un elemento Collider, luego agregar el script coin y el evento event trigger, dentro de ello asignar el evento Pointer Click y asignar el método Coin.OnCoinClicked(); 
</p>
	
	<img width="45%" src="Imagenes/Foto5.png"></img>

 <p>Los componentes Collider definen la forma de un objeto para los propósitos de colisiones físicas. Un collider, el cual es invisible, necesita no estar con la misma forma exacta que el mesh del objeto y de hecho
Hacer la interfaz de usuario interactiva
Durante este paso, haremos que el objeto SignPost sea interactivo al agregarle componentes de disparadores y eventos. El proceso es casi idéntico al que hicimos con la moneda, la llave y la puerta en el paso anterior, pero no necesitamos un colisionador para interactuar con los objetos del juego de la interfaz de usuario. En su lugar, debemos verificar que el objeto del juego Canvas tenga un componente Graphic Raycaster, y debido a que estamos usando GVR, reemplazaremos el Graphic Raycaster de Unity con el GvrPointerGraphicRaycaster de Google VR.
-	Elimine el componente Graphic Raycaster que se agrega automáticamente al crear un nuevo objeto.
-	Agregue el script GvrPointerGraphicRaycaster como componente.
-	Agregue el script SignPost proporcionado como componente. 
-	Agregue un Event Trigger como componente. 
-	Agregue el evento PointerClick al componente Event Trigger. 
-	Asigne el componente script SignPost al campo de objeto del evento Pointer Click. 
-	Asigne el método SignPost.ResetScene () como la función para el evento Pointer Click. 
-	Ingrese al modo de juego, haga clic en SignPost y verifique que el mensaje 'SignPost.ResetScene ()' esté impreso en la ventana de la consola.
</p>

	<img width="45%" src="Imagenes/Foto6.png"></img>

 <p> Programando el comportamiento de la moneda (coin)
Este paso, programaremos el comportamiento de la moneda para que, cuando se haga clic en una moneda (coin), se reproduzca un sonido, muestre un efecto de "poof" y desaparezca
-	Hay un mínimo de cinco monedas en el laberinto. Cuando se hace clic en una moneda, se reproduce un efecto de sonido en la ubicación de esa moneda. Cuando se hace clic en una moneda, esa moneda se elimina de la jerarquía de la escena.

 </p>

	<img width="45%" src="Imagenes/Foto7.png"></img>
 
 <p>Programando el comportamiento de la llave (key) 
Durante este paso, programaremos el comportamiento de la llave (key) para que, cuando se haga clic en la llave, reproduzca un sonido, muestre un efecto de "poof" y desaparezca.
-	Hay un mínimo de una llave en el laberinto. Cuando se hace clic en la llave, se reproduce un efecto de sonido en la ubicación de la llave. Cuando se hace clic en la llave, la llave se elimina de la jerarquía de la escena. Cuando se hace clic en la llave, la puerta se desbloquea
 </p>

	<img width="45%" src="Imagenes/Foto8.png"></img>

 	<img width="45%" src="Imagenes/Foto9.png"></img>

 <p>8.	Programando el comportamiento de la puerta (door)
Durante este paso, programaremos el comportamiento de la puerta (door) para que cuando se haga clic en la llave (key), la Puerta se desbloquee y cuando se haga clic en la Puerta, se escuche un sonido y comience a girar a una posición de apertura. 
</p>
 
	<img width="45%" src="Imagenes/Foto10.png"></img>

 
 <p>La puerta evita que el usuario navegue al objeto SignPost hasta que se haya abierto. Cuando comienza el juego, la puerta está bloqueada y cerrada. La puerta no se puede abrir cuando está bloqueada. La puerta solo puede desbloquearse haciendo clic en la llave. Cuando se hace clic y se desbloquea la puerta, la puerta comienza a abrirse. Cuando la puerta comienza a abrirse, se reproduce un efecto de sonido en la ubicación de la puerta. La puerta se anima a una posición de abierta solo por código, es decir, no mediante el uso de animación y controlador de animador</p>

	<img width="45%" src="Imagenes/Foto11.png"></img>

<p>Programando el comportamiento del SignPost 
Durante este paso, programaremos el comportamiento de SignPost para que cuando se haga clic en SignPost se reinicie el juego. 
El SignPost no se puede ver ni interactuar antes de que se abra la puerta. Cuando se hace clic en SignPost, la escena se restablece a su estado inicial para que el juego se pueda volver a jugar.</p>


<p>Crear la funcionalidad del juego
Durante este paso, armaremos todo y convertiremos nuestro proyecto en un juego real. 
Laberinto
.</p>

	<img width="45%" src="Imagenes/Foto12.png"></img>


	<img width="45%" src="Imagenes/Foto13.png"></img>

 <p>RESULTADO(S) OBTENIDO(S): </p>
  <ul>
  <li>RESULTADO(S) OBTENIDO(S):
-	Al Ganar el Juego se abre la puerta y se visualiza un mensaje “YOU WIN”, al darle clic se cambia de escena, simulando el cambiar de nivel en este caso se reinicia nuevamente el juego. En caso de no adquirir la llave no podrá abrir la puerta.

	
	<img width="45%" src="Imagenes/Foto14.png"></img>


-	Cuando se obtiene las monedas hace el siguiente efecto y desaparece de la escena ¨Juego¨.
   

	<img width="45%" src="Imagenes/Foto15.png"></img>


</li>
  
 </ul>
 <p>CONCLUSIONES:</p>
  <ul>
  <li>Es importante saber sobre la documentación que existe del Software Unity para la creación de los scripts e implementación de Collider para realizar animaciones dentro de un juego o para el desarrollo interactivo, principalmente unity esta considerado como un motor de videojuegos que no permite a desarrollar el entorno de juegos multiplaforma es decir poder ejecutar el juego en dispositivos como Android.
Es necesario saber tomar en cuenta le jerarquía ya que esta se cataloga los elementos según la importancia de igual manera el inspector que nos permite ver las propiedades de los elementos desarrollados en unity, la escena aquí es donde se realiza el diseño y por así decirlo el prototipado de un videojuego como en este caso el de un Laberinto, en donde pues puede haber divisiones de escenas que se simule el subir de nivel.</li>
 </ul>
 <p>RECOMENDACIONES:</p>
  <ul>
  <li>Se recomienda asistir a las secciones de clases virtuales.</li>
  <li>Ante cualquier duda consultar al docente.</li>
  <li>Revisar documentación del unity para realizar la práctica.</li>
 <li>Se recomienda usar cámara del Google VR para la realidad virtual.</li>
 </ul>
 
