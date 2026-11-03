# BancoAlimentosComunitario2026
Solución a un problema de un Banco de Alimentos comunitario
Descripción del problema:
Jorge es el voluntario que coordina un banco de alimentos de barrio, sin presupuesto y con voluntarios que cambian cada semana, muchos de ellos personas mayores con poca experiencia en tecnología. Las donaciones llegan sin aviso y en cantidades impredecibles, y parte de la comida caduca en el almacén porque nadie sabe qué vence primero. Además, no hay registro de entregas, así que algunas familias reciben varias veces y otras ninguna, lo que genera conflictos en la comunidad. Necesita reducir el desperdicio y distribuir de forma justa con una herramienta muy fácil de usar. Los recibos fiscales para donantes quedan fuera por ahora

Desarrollo de la implementación mediante una app que permite implementar el correspondiente registro de Familias, donaciones, Inventario y realizar el correspondiente resumen de las operaciones realizadas.

Tecnología: Realizado en html, JavaScript y Phyton en servidor local

Particularidades generadas por la IA chatGPT:

He creado la app Despensa, una aplicación sencilla en español para registrar donaciones, ordenar alimentos por vencimiento, anotar familias y mantener un historial de entregas. Al registrar una entrega, descuenta las unidades del inventario y avisa si esa familia recibió apoyo en los últimos siete días; la decisión final queda en manos del equipo.

Importante:
La información se guarda en el navegador de este dispositivo, así que no se comparte automáticamente entre voluntarios. Los recibos fiscales quedan fuera del alcance del sistema y de los donantes

INSTRUCCIONES DE USO:
1 -Para iniciar a usar la funcionalidades del sistema DESPENSA, hay que crear mínimo una familia con el correspondiente número de integrantes en el apartado Familias.
2- Se debe realizar el registro de las donaciones en el inventario del sistema DESPENSA, en el apartado Inventario, especificando los alimentos donados, cantidad, fecha de vencimiento y persona que realizó la donación para llevar un registro preciso sobre el inventario.
3- Realizar la entrega, en el apartado Entregas, seleccionando a una familia ya registrada, teniendo en cuenta seleccionar los alimentos y la cantidad, dependiendo del disponible en los inventarios, teniendo en cuenta la fecha de vencimiento y automáticamente se realiza el registro de la fecha de entrega.

Finalmente todo se puede revisar desde el apartado de Resumen donde aparecen listadas las entregas realizadas a las familias ordenadas por fecha de entrega.

Definición del Definición del ICP y User Persona del sistema DESPENSA generado por la IA de Github Copilot con ChatGPT:
ICP — Perfil de cliente ideal
El cliente ideal de DESPENSA es una organización comunitaria, banco de alimentos, parroquia, asociación o grupo vecinal que coordina la recepción y distribución de alimentos para personas en situación de vulnerabilidad.

Características principales:

Atiende de manera recurrente a familias o personas de su comunidad.
Gestiona donaciones, inventario y entregas con procesos manuales o herramientas dispersas.
Cuenta con voluntarios o responsables que coordinan las operaciones.
Necesita mejorar la trazabilidad de los alimentos y la organización de las entregas.
Tiene acceso básico a internet y a dispositivos como celulares o computadoras.
Necesidades y desafíos: evitar pérdidas o vencimientos, conocer qué alimentos hay disponibles, coordinar voluntarios y entregas, y mantener información organizada sobre las solicitudes y la atención brindada.

Valor que ofrece DESPENSA: centralizar la gestión de alimentos y facilitar la coordinación entre la organización, sus voluntarios y las personas beneficiarias.

User personas
1. Coordinadora comunitaria — usuaria principal
Perfil: responsable de organizar la despensa y coordinar a los voluntarios. Puede tener experiencia limitada con herramientas digitales.

Objetivos:

Saber qué productos hay disponibles y cuáles requieren atención.
Organizar las donaciones y las entregas.
Evitar duplicaciones, errores y desperdicio.
Consultar información clara para tomar decisiones.
Frustraciones: registros en papel o dispersos, falta de visibilidad del inventario y dificultad para coordinar a varias personas.

Necesita: una herramienta sencilla, fácil de aprender y utilizable desde un celular.

2. Persona beneficiaria — usuaria de atención
Perfil: persona o representante de una familia que solicita o recibe apoyo alimentario.

Objetivos:

Conocer cómo acceder a la ayuda y qué información debe proporcionar.
Recibir atención respetuosa y clara.
Evitar entregar repetidamente los mismos datos.
Frustraciones: no saber cuándo hay alimentos disponibles, tener que repetir su situación o enfrentar procesos confusos.

Necesita: instrucciones comprensibles, un proceso accesible y un manejo respetuoso de su información personal.

3. Voluntario — usuario operativo
Perfil: persona que colabora en la recepción, organización o entrega de alimentos.

Objetivos: conocer sus tareas, registrar movimientos correctamente y colaborar sin depender de instrucciones dispersas.

Necesita: pasos simples y acceso solo a la información necesaria para su labor.

Supuesto de alcance: la organización comunitaria es el cliente ideal del sistema; coordinadores, voluntarios y beneficiarios son perfiles de usuario con necesidades distintas. 
