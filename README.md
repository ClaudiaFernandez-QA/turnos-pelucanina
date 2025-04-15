# 🐾 Turnos Pelu Canina - API Testing

Este proyecto simula un sistema de turnos para un petshop especializadao en baño, corte de pelo y corte de uñas para mascotas.

Este proyecto fue creado como ejercicio práctico para profundizar en habilidades de API Testing con Postman, Newman y Data Driven Testing con archivos `.json`.

---

## 🎯 Objetivo del Proyecto

- Simular un flujo de alta de turnos.
    
- Aplicar validación de datos.
    
- Usar Postman como herramienta principal para automatizar pruebas.
    
- Ejecutar las pruebas con Newman en la terminal.
    
---

## 🧠 Lógica del Negocio Asumida

Dado que usamos [crudcrud.com](https://crudcrud.com/) como backend simulado (sin validaciones reales), aplicamos reglas de negocio directamente desde Postman para simular el comportamiento de una API profesional.

- 🔐 **Todos los campos son obligatorios** y deben cumplir su tipo de dato.
    
- 📅 **Horario permitido**: solo turnos entre `09:00` y `17:00`, en horas enteras (ej: `10:00`, `14:00`, no se acepta `14:30`).
    
- 🐶 **Tamaño permitido de mascotas**: `"chico"`, `"mediano"`, `"grande"`.
    
- 🛁 **Servicios válidos**:
    
    - `baño`
        
    - `corte de pelo`
        
    - `corte de uñas`
        
- 📞 **Formato de teléfono** : string numérico de 10 a 12 dígitos.
    
- 📆 **Formato de fecha**: `YYYY-MM-DD`.
    
- ✅ **`services`** debe ser un array con al menos un servicio y máximo tres.
    
---

## 🌐 Cómo configurar crudcrud.com

`crudcrud.com` actúa como un servidor backend temporal que **persiste datos por 24hs** y permite hacer pruebas sin necesidad de un backend real.

### 🔧 Pasos para generar tu token:

1. Ingresá a 👉 [https://crudcrud.com](https://crudcrud.com)
    
2. Automáticamente se te mostrará una URL como esta: [<i>https://crudcrud.com/api/0123abc456def7890ghi12345678</i>](https://crudcrud.com/api/0123abc456def7890ghi12345678)
    
3. Copiá **solo la parte del token**, que sería: _0123abc456def7890ghi12345678_
    
4. Ahora, abrí el archivo `turnos.postman_environment.json` con un editor de texto.  
    Buscá esta parte:  
    {  
    "key": "token",  
    "value": "aca_va_tu_token"  
    }
    
5. Pegá ahí tu token entre comillas. Y guardá.
    

## 🧠 Consideraciones adicionales

- El token de `crudcrud.com` expira en 24hs.
    
- Si al correr el flujo ves errores 404 o "No se encontró ID", probablemente el token ya haya vencido. Generá uno nuevo.
    
---

## ⚙️ Requisitos Técnicos

Para ejecutar este proyecto necesitás:

- [Postman](https://www.postman.com/) instalado (opcional, para exploración manual)
    
- [Node.js](https://nodejs.org/) instalado (para usar Newman)
    
- Instalar Newman:
    

``` bash
npm install -g newman

 ```

---

## 🚀 Ejecución con Newman

Este comando corre el flujo completo de creación y validación de turnos:

``` bash
newman run "Collection/turnos.postman_collection.json" \
  -e "Environment/turnos.postman_environment.json" \
  -d "Data/turnos_data.json" \
  --reporters cli
 ```
