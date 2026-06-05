# Análisis de Dominio – Sistema de Reservas de Equipamiento Deportivo

## 1. Tablas que usa la API

- **reserva** – tabla principal, una fila por cada reserva
- **recurso** – lo que se reserva (pista de tenis, pádel, etc.)
- **usuario** – quien hace la reserva

## 2. Campos de la tabla reserva

| Campo            | Tipo    | ¿Lo envía el usuario? | Notas                          |
|------------------|---------|-----------------------|--------------------------------|
| id_reserva_local | entero  | No                    | Lo genera la base de datos     |
| id_recurso       | entero  | Sí                    | Qué recurso quiere reservar    |
| id_usuario       | entero  | No                    | Lo añade el servidor automáticamente |
| numero_plazas    | entero  | Sí                    | Cuántas plazas necesita        |
| fecha            | fecha   | Sí                    | Formato YYYY-MM-DD             |
| hora_inicio      | hora    | Sí                    | Formato HH:MM                  |
| hora_fin         | hora    | Sí                    | Formato HH:MM                  |
| coste            | decimal | No                    | Lo calcula el servidor         |
| motivo           | texto   | Sí (opcional)         | Para qué es la reserva         |
| observaciones    | texto   | Sí (opcional)         | Cualquier nota extra           |

## 3. Validaciones básicas

- La fecha no puede ser del pasado
- hora_inicio debe ser anterior a hora_fin
- numero_plazas no puede superar la capacidad del recurso
- No puede haber dos reservas del mismo recurso a la misma hora
- La contraseña del usuario **nunca** se devuelve en la API
