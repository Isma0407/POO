# POO
# Clase Persona (Encapsulación)
class Persona:
    def __init__(self, nombre):
        self.nombre = nombre

    def presentar(self):
        return f"Hola, soy {self.nombre}."

# Clase Estudiante que hereda de Persona (Herencia)
class Estudiante(Persona):
    def __init__(self, nombre, grado):
        super().__init__(nombre)
        self.grado = grado

    def info(self):
        return f"{self.presentar()} Soy estudiante de grado {self.grado}."

# Clase Profesor que hereda de Persona (Herencia)
class Profesor(Persona):
    def __init__(self, nombre, materia):
        super().__init__(nombre)
        self.materia = materia

    def info(self):
        return f"{self.presentar()} Soy profesor de {self.materia}."

# Clase Curso que contiene Estudiantes y Profesores (Composición)
class Curso:
    def __init__(self, nombre):
        self.nombre = nombre
        self.profesor = None
        self.estudiantes = []

    def asignar_profesor(self, profesor):
        self.profesor = profesor

    def agregar_estudiante(self, estudiante):
        self.estudiantes.append(estudiante)

    def mostrar_info(self):
        profesor_nombre = self.profesor.nombre if self.profesor else "Sin profesor"
        estudiantes_nombres = ", ".join([e.nombre for e in self.estudiantes]) if self.estudiantes else "Sin estudiantes"
        return f"Curso: {self.nombre}\nProfesor: {profesor_nombre}\nEstudiantes: {estudiantes_nombres}"

# Crear objetos (Polimorfismo)
profesor1 = Profesor("Carlos", "Matemáticas")
estudiante1 = Estudiante("Ana", "10°")
estudiante2 = Estudiante("Luis", "10°")

# Crear curso y asignar profesor y estudiantes
curso_matematicas = Curso("Matemáticas")
curso_matematicas.asignar_profesor(profesor1)
curso_matematicas.agregar_estudiante(estudiante1)
curso_matematicas.agregar_estudiante(estudiante2)

# Mostrar información
print(profesor1.info())
print(estudiante1.info())
print(estudiante2.info())
print("\n" + curso_matematicas.mostrar_info())
