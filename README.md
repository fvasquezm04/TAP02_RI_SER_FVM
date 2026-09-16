# Taller-Cinematica-ROS2-MoveIt

## Comandos utilizados 

* git clone https://github.com/author/original_robot_repo.git temp_original_repo (para clonar el Repo que contenia el xacro y urdf)
* ros2 pkg create abb_irb1600_support --build-type ament_cmake (para crear un nuevo paquete de ROS2)
* cp -r temp_original_repo/urdf abb_irb1600_support/
* cp -r temp_original_repo/meshes abb_irb1600_support/ (para trnasferir el urdf y los STLs)
* ros2 launch urdf_launch display.launch.py urdf_package:=abb_irb1600id_support urdf_package_path:=urdf/irb1600id.xacro (para visualizar la importacion del robot)
* ros2 launch moveit_setup_assistant setup_assistant.launch.py (activa el wizard para configurar el moveit del robot)
* ros2 launch irb1600id_moveit_config demo.launch.py (corre el nodo y lo visualiza en RVIZ2)
* ros2 run tf2_ros tf2_echo base_link tool0 (muestra la transformada homogenea de la herramienta)
* ros2 topic echo /joint_states --once (muestra los angulos de cada una de las articulaciones para la posicion actual del robot)
* mkdir -p ~/ws_abb_irb_1600/src/irb1600id_moveit_config/scripts (crea una carpeta para los scripts que seran utilizados)
* cd ~/ws_abb_irb_1600/src/irb1600id_moveit_config/scripts
* code pick_and_place.py (crea el script para las trayectorias)
* ros2 run irb1600id_moveit_config scene.py (corre el script que genera el obstaculo y el resto de objetos)
* ros2 launch irb1600id_moveit_config run_cycle.launch.py (indica al robot que debe comenzar con la trayectoria)
* ros2 run irb1600id_moveit_config get_jacobian.py --config PICK (obtiene los jacobianos del tramo 4B)
* ros2 run irb1600id_moveit_config get_jacobian.py --config PLACE (obtiene los jacobianos del tramo 4D)
* python3 verify_jacobian_velocity.py (compara la velocidad obtenida por el jacobiano con la velocidad en la trayectoria obtenida por moveit)
  
