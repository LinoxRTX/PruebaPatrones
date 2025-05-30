Perfecto, con base en los requisitos que indicas, te propongo una estructura clara para abordar la **evaluación individual** de diseño UML con patrones de diseño y relaciones UML. A continuación te detallo cómo organizar tu **informe final** y qué debe contener cada uno de los entregables solicitados:

---

## 🧾 **INFORME FINAL – Evaluación Individual: Diseño UML y Patrones**

---

### **1. Diagrama de Casos de Uso UML**

* **Objetivo:** Representar los requerimientos funcionales del sistema desde la perspectiva del usuario.
* **Elementos a incluir:**

  * Actores principales (Usuario, Administrador, etc.).
  * Casos de uso generales (Ej: *Registrar usuario, Consultar información, Administrar contenido*).
  * Relaciones:

    * `<<include>>` (obligatoria): cuando un caso de uso siempre se ejecuta como parte de otro.
    * `<<extend>>` (opcional): cuando se ejecuta bajo ciertas condiciones.
  * Organización clara con nombres significativos.

> Puedes usar herramientas como **draw\.io**, **Lucidchart**, o **StarUML** para diseñarlo.

---

### **2. Diagrama de Clases UML**

* **Objetivo:** Mostrar la estructura estática del sistema.
* **Debe contener:**

  * Clases con atributos y métodos (visibilidad `+` pública, `-` privada).
  * Relaciones:

    * **Asociación**: conexión general entre clases.
    * **Agregación**: relación de “tiene un” donde los objetos pueden vivir independientemente.
    * **Composición**: relación fuerte, el objeto contenido no puede existir sin el contenedor.
    * **Dependencia**: cuando una clase utiliza otra, pero no la contiene.
  * Indicar visibilidad, multiplicidad, y navegabilidad.

---

### **3. Diagrama de Implementación UML**

* **Objetivo:** Mostrar cómo los componentes del software se organizan físicamente.
* **Componentes típicos:**

  * Componentes de software (clases empaquetadas).
  * Módulos (p. ej., UI, lógica de negocio, acceso a datos).
  * Relación de dependencia entre clases o componentes.

---

### **4. Justificación Técnica (máx. 1 página)**

#### **Patrones aplicados** (ejemplo):

* **Singleton**: Aplicado en la clase `ConfiguracionSistema`, para garantizar una única instancia global.
* **Prototype**: Implementado en `DocumentoLegal`, para clonar plantillas de documentos.
* **Bridge**: Usado entre `Notificador` (abstracción) y `CanalEnvio` (implementación) para variar tipos de notificaciones (Email, SMS).
* **Adapter**: Para adaptar una API externa de pagos a nuestra interfaz `IPago`.

#### **Relaciones UML utilizadas:**

* **<<include>>**: `Registrar usuario` incluye `Validar datos`.
* **<<extend>>**: `Enviar recordatorio` extiende `Registrar reserva`.
* **Asociación**: `Cliente` — `Reserva`.
* **Composición**: `Reserva` — `DetalleReserva`.
* **Dependencia**: `ControladorReserva` depende de `ServicioReserva`.

#### **Fragmentos de seudocódigo (Java)**

**Singleton**

```java
public class ConfiguracionSistema {
    private static ConfiguracionSistema instancia;
    private ConfiguracionSistema() {}
    public static ConfiguracionSistema getInstancia() {
        if (instancia == null) instancia = new ConfiguracionSistema();
        return instancia;
    }
}
```

**Prototype**

```java
public abstract class DocumentoLegal implements Cloneable {
    public DocumentoLegal clonar() throws CloneNotSupportedException {
        return (DocumentoLegal) super.clone();
    }
}
```

**Bridge**

```java
interface CanalEnvio { void enviar(String mensaje); }
abstract class Notificador {
    protected CanalEnvio canal;
    public Notificador(CanalEnvio c) { canal = c; }
    abstract void notificar(String mensaje);
}
```

**Adapter**

```java
class PagoAdapter implements IPago {
    private APIExternaPago api;
    public void procesarPago(double monto) {
        api.realizarTransferencia(monto);
    }
}
```

---

### **5. Informe Final**

* Formato: `.docx` o `.pdf`
* Estructura sugerida:

  * Portada (nombre, fecha, asignatura)
  * Introducción breve
  * Objetivo del diseño
  * Diagrama de Casos de Uso
  * Diagrama de Clases
  * Diagrama de Implementación
  * Justificación técnica (con seudocódigo)
  * Conclusión
  * Anexos (si corresponde)

---

¿Te gustaría que te ayude a **diseñar un caso de ejemplo realista** (por ejemplo, un sistema de gestión de reservas, biblioteca, e-commerce, etc.) para aplicar todo esto? Puedo ayudarte a crear los diagramas, fragmentos y justificación completa.
