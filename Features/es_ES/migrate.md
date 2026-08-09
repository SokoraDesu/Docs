# Guía de Migración
<small>Última actualización: 20/6/26</small>

<!-- START START -->
<b>Esta guía cubre la migración de datos de nivel, la cual aún no está disponible.</b> Será lanzada junto a Sokora 0.4, que está aún bajo desarrollo activo.
<!-- END START -->

<!-- START(Introduction) -->
## Introducción
Una parte complicada de pasarse a un bot nuevo y mejor (como Sokora) con un sistema de niveles es que probablemente ya estaba usando otro bot con este propósito. Esto normalmente le deja con tres opciones:
- Mantener ambos bots, haciendo con uno lo que podría hacer con otro. Lo más fácil, pero subóptimo.
- Eliminar el bot anterior. Óptimo, pero los niveles y tabla de clasificación previos se pierden, cosa que no hará gracia a sus miembros.
- No usar Sokora. Sus datos se mantienen, pero se pierde el mejor bot de Discord. ¡No compensa!
<!-- $$ -->
Sin embargo, <b>si usa MEE6, Tatsu, Lurkr o Amari para niveles, ¡está de suerte!</b>
<!-- $$ -->
Podemos portar su tabla de clasificación a Sokora.
<!-- END(Introduction) -->

<!-- START(Setup) -->
## Preparando su bot anterior para importar

Este proceso depende del bot del que esté migrando.
<!-- $$ -->
<!-- $$ -->
### MEE6
Solo necesita habilitar la visibilidad de la tabla de clasificación. Abra los ajustes del sistema de niveles en el panel de MEE6 y habilite `Make my server's leaderboard public`. De otra manera no se podrá importar nada.
<!-- $$ -->
<!-- $$ -->
### Tatsu
Necesita una clave API. Obténgala ejecutando `t!apikey` en el servidor a migrar.
<!-- $$ -->
<!-- $$ -->
### Lurkr
Necesita una clave API. Obténgala siguiendo los pasos mencionados en <https://lurkr.gg/docs/api#authentication>.
<!-- $$ -->
Además, deberá dotar al servidor a migrar de permisos especificos. El mismo enlace explica como hacer esto inmediatamente después de explicar cómo obtener su clave API.
<!-- $$ -->
Por último, deberá cambiar manualmente `Choose the visibility for the web leaderboard` en el panel de Lurkr a `Public`.
<!-- $$ -->
<!-- $$ -->
### Amari
Necesita una clave API. Obténgala manualmente mediante una solicitud en el servidor oficial de Amari en Discord, <https://amaribot.com/support>.
<!-- $$ -->
Cabe recalcar que nosotros mismos fuimos a pedirla para hacer pruebas y se nos dijo que en aquel momento no se estaban emitiendo claves nuevas porque se está rehaciendo el sistema o algo por el estilo.
<!-- END(Setup) -->

<!-- START(Importing your data) -->
## Cómo importar sus datos

En su servidor, ejecute el comando `/import` de Sokora desde cualquier canal. Se le presentará una lista con cada bot soportado, seguido de un botón para importar que o bien le pedirá una clave API o bien pasará directamente al siguiente paso, según el bot seleccionado.
<!-- $$ -->
<!-- $$ -->
En el siguiente paso, verá una pequeña vista previa de qué se importará. Tendrá tres botones: «<b>Merge data</b>», «<b>Overwrite data</b>» y «<b>Check JSON first</b>». El contenedor explica por sí mismo qué hace cada botón, pero para que se haga a la idea:

- <b>Merge data</b> AÑADE la experiencia que cada usuario tenía con el bot anterior a la que tiene con Sokora.
- <b>Overwrite data</b> REEMPLAZA la experiencia que cada usuario tenía con Sokora con la que tenía con el bot anterior.
<!-- $$ -->
Ambos botones son equivalentes si acaba de añadir Sokora (de modo que no tiene datos previos).

- <b>Check JSON first</B> presenta una vista previa algo más detallada de los datos que Sokora ha leído del bot del que importar, ordenando a sus usuarios de mayor a menor experiencia (solo mostrará lo que quepa en el mensaje). Dicha vista previa estará, efectivamente, en formato JSON; un formato fácil de leer, sepa o no lo que es. Seguirá teniendo los botones Merge y Overwrite a su disposición.

En cuanto presione Merge u Overwrite, Sokora empezará de inmediato. Dele algo de tiempo. Le avisará cuando termine.
<!-- $$ -->
Y, en cuanto acabe, ¡ya está! Podrá eliminar el bot anterior con seguridad, preservando su tabla de clasificación.
<!-- END(Importing your data) -->

<!-- START(FAQ) -->
## P+F
<CLOSABLE (¿Qué hay de las recompensas por nivel como canales y roles? ¿Se migran?)>
Depende del bot. Por ahora solo podemos migrarlas desde MEE6; con Amari aún en proceso. Si un bot soporta recompensas por nivel pero no podemos migrarlas, Sokora avisará de esto.
</CLOSABLE (¿Qué hay de las recompensas por nivel como canales y roles? ¿Se migran?)>
<!-- $$ -->

<CLOSABLE (¿De qué depende el soporte para bots? ¿Por qué el bot *x* no está soportado?)>
Sokora obtiene los datos tratando de manejarse con las APIs que proveen los bots. El caso es que no todos los bots proveen APIs y algunos prefieren retener sus datos de manera que solo estos puedan accederlos. No podemos hacer mucho al respecto.
</CLOSABLE (¿De qué depende el soporte para bots? ¿Por qué el bot *x* no está soportado?)>
<!-- $$ -->

<CLOSABLE (He importado mis datos, pero ahora el ritmo al que crece la experiencia parece diferente, ¿por qué?)>
Porque lo es. Sencillamente no podemos importar los ajustes de obtención de experiencia de ningún bot (porque cada bot utiliza su propia fórmula y parámetros para computar la experiencia a obtener).
</CLOSABLE (He importado mis datos, pero ahora el ritmo al que crece la experiencia parece diferente, ¿por qué?)>
<!-- $$ -->

<CLOSABLE (¿Esta capacidad es exclusiva de Sokora?)>
De hecho no. La pusimos a disposición de casi cualquier bot de Discord.
<!-- $$ -->
Véase más al respecto en <https://github.com/hokkiai/djs-level-importer>.
<!-- $$ -->
<small>(Nota: somos nosotros los creadores y principales mantenedores del sistema, pero por un pequeño acuerdo no es Sokora quien publica el código fuente, por eso la URL de GitHub no apunta a nuestra organización habitual).</small>
</CLOSABLE (¿Esta capacidad es exclusiva de Sokora?)>
<!-- $$ -->
<CLOSABLE (Digamos que otro bot implementa esto, ¿podrá importar mis datos de Sokora?)>
<b><i>Todavía</i> no.</b> Sabemos que suena un poco hipócrita, pero NO es porque pretendamos ejercer confinamiento propietario, simplemente son motivos técnicos: Sokora no tiene una API web y por ello <i>aún</i> está en el mismo estado que otros bots no amistosos con los desarrolladores.
<!-- $$ -->
Estamos (obviamente) trabajando en ello y eventualmente actualizaremos la librería para que sus datos con Sokora puedan ser migrados libremente tal y como merece. ¡Solo denos algo de tiempo!
</CLOSABLE (Digamos que otro bot implementa esto, ¿podrá importar mis datos de Sokora?)>
<!-- $$ -->
<!-- $$ -->
<!-- END(FAQ) -->
