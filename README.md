

[![Ver Documentación](https://img.shields.io/badge/Web-Ver%20Documentacion-darkblue)](https://fedes10.github.io/EJ1_ex2_ED_Federico_Tarea1_Examen/)

# Sistema de Gestión de Películas, Examen Federico

Bienvenido a la documentación técnica del proyecto **EJ1_ex2_ED_Federico_Tarea1_Examen**. Esta es una aplicación de escritorio desarrollada en **Java** diseñada para la gestión administrativa de un cine o videoclub.

## 📄 Descripción General

El programa ofrece una interfaz gráfica de usuario (GUI) intuitiva basada en ventanas, permitiendo al usuario realizar operaciones CRUD (Crear, Leer, Actualizar, Borrar) sobre películas y directores, así como visualizar estadísticas de ventas.


## 🚀 Funcionalidades Principales

### 1. Menú Principal (`Design.java`)
Es el punto de entrada visual de la aplicación. Ofrece acceso rápido a las distintas secciones mediante botones interactivos con efectos visuales (`MouseListener` para cambio de iconos al pasar el ratón).
*   **Funcionalidad destacada:** Generación de gráficos estadísticos. Al hacer clic en el botón de estadísticas, la aplicación consulta la base de datos y utiliza la librería **JFreeChart** para mostrar un gráfico de barras con el total de ventas por película.

### 2. Gestión de Películas y Directores
*   **Agregar (`Ajouter_Film.java`):**
    *   Permite registrar una nueva película especificando título, precio y género (Romance, Acción, Ciencia Ficción).
    *   **Lógica dinámica:** Ofrece la opción de seleccionar un director existente desde una lista desplegable (`JComboBox`) o registrar un nuevo director en el mismo formulario mediante botones de opción (`JRadioButton`).
*   **Eliminar (`Supprimer_Film.java`):**
    *   Permite dar de baja películas o directores.
    *   La interfaz se adapta dinámicamente: al elegir borrar una película, muestra la lista de películas; al elegir director, muestra la lista de directores.

### 3. Ventas
*   Incluye un módulo de ventas (referenciado como `Vente_Film`) accesible desde el menú principal para gestionar las transacciones.

## 🛠️ Stack Tecnológico

El proyecto utiliza las siguientes tecnologías y librerías:

*   **Lenguaje:** Java SE.
*   **Interfaz Gráfica (GUI):**
    *   **Java Swing:** Uso extensivo de componentes como `JFrame`, `JPanel`, `JLabel` (usados como botones con imágenes), `JComboBox`, `JTextField` y `JRadioButton`.
    *   **AWT:** Manejo de eventos (`ActionListener`, `MouseAdapter`) y diseño (`LayoutManagers`).
*   **Base de Datos:**
    *   **JDBC:** Conectividad nativa para ejecutar sentencias SQL (`Statement`, `PreparedStatement`, `ResultSet`).
    *   La conexión se gestiona centralizadamente (referencia a `Main.connection`).
*   **Visualización de Datos:**
    *   **JFreeChart:** Librería externa utilizada para renderizar gráficos de barras (`ChartFactory.createBarChart`) basados en los datos obtenidos mediante `JDBCCategoryDataset`.

## 📂 Estructura del Código

### Paquete `projet`

| Clase | Responsabilidad |
| :--- | :--- |
| **`Design`** | Ventana principal. Orquesta la navegación y visualiza el gráfico de ventas. |
| **`Ajouter_Film`** | Formulario de alta. Maneja validaciones de entrada y lógica condicional para directores nuevos vs. existentes. |
| **`Supprimer_Film`** | Formulario de baja. Carga datos en tiempo real desde la BD para poblar las listas de selección. |
| **`Film`** | (Clase de Modelo/DAO) Encapsula la lógica de acceso a datos para la entidad Película (métodos `insert`, `select`, `sup_film`). |
| **`Realisateur`** | (Clase de Modelo/DAO) Encapsula la lógica para la entidad Director (métodos `insert`, `select`, `sup_rel`). |
| **`Main`** | (Clase de Utilidad) Se encarga de establecer la conexión con la base de datos. |

## 📋 Requisitos de Ejecución

1.  **JDK Instalado:** Versión compatible con Java Swing.
2.  **Librerías Externas:**
    *   `jfreechart-x.x.x.jar`
    *   `jcommon-x.x.x.jar`
3.  **Base de Datos:**
    *   Debe estar accesible y configurada en la clase `Main`.
    *   Tablas requeridas: `Film`, `Realisateur`, `Vente`.
    *   Recursos (Imágenes): Las rutas a las imágenes están hardcodeadas (ej. `C:\Users\Hatem\...`), por lo que se recomienda actualizarlas a rutas relativas para asegurar la portabilidad del proyecto.