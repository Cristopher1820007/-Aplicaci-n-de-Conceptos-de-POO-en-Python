# -Aplicaci-n-de-Conceptos-de-POO-en-Python
Aplicar los conocimientos adquiridos sobre Definición de Clase, Definición de Objeto, Herencia, Encapsulación y Polimorfismo en Python para desarrollar un programa
# ==============================
# Ejemplo de POO en Python
# Conceptos: Clase, Objeto, Herencia, Encapsulación y Polimorfismo
# ==============================

# Clase base (superclase)
class Persona:
    def __init__(self, nombre, edad):
        self.nombre = nombre          # Atributo público
        self.__edad = edad            # Atributo privado (encapsulación)

    # Método para acceder al atributo privado
    def get_edad(self):
        return self.__edad

    # Método para modificar el atributo privado
    def set_edad(self, nueva_edad):
        if nueva_edad > 0:
            self.__edad = nueva_edad
        else:
            print("La edad debe ser positiva.")

    # Método que será sobrescrito en la clase derivada (polimorfismo)
    def presentarse(self):
        return f"Hola, soy {self.nombre} y tengo {self.__edad} años."


# Clase derivada (herencia)
class Estudiante(Persona):
    def __init__(self, nombre, edad, carrera):
        # Llamada al constructor de la clase base
        super().__init__(nombre, edad)
        self.carrera = carrera

    # Sobrescritura del método presentarse (polimorfismo)
    def presentarse(self):
        return f"Hola, soy {self.nombre}, estudio {self.carrera} y tengo {self.get_edad()} años."


# Otra clase derivada para demostrar polimorfismo adicional
class Profesor(Persona):
    def __init__(self, nombre, edad, materia):
        super().__init__(nombre, edad)
        self.materia = materia

    def presentarse(self):
        return f"Soy el profesor {self.nombre}, enseño {self.materia} y tengo {self.get_edad()} años."


# ==============================
# Programa principal
# ==============================
if __name__ == "__main__":
    # Crear instancias de las clases
    persona = Persona("Carlos", 40)
    estudiante = Estudiante("Ana", 20, "Ingeniería")
    profesor = Profesor("Luis", 50, "Programación")

    # Demostración de encapsulación
    print(persona.presentarse())
    persona.set_edad(41)  # Modificamos edad con setter
    print("Edad actualizada:", persona.get_edad())

    # Demostración de polimorfismo
    print(estudiante.presentarse())
    print(profesor.presentarse())

    # Lista de objetos para mostrar polimorfismo en acción
    personas = [persona, estudiante, profesor]
    for p in personas:
        # Cada objeto ejecuta su propia versión de presentarse()
        print(p.presentarse())
