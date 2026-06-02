# Grupo MF CRM Operativo

Mini-CRM de cliente único construido como HTML+JS standalone (sin servidor, sin build step).
Toda la data persiste en `localStorage` del browser. El HTML se abre directamente como archivo local.

Adaptado del CRM de TCW para el cliente Grupo MF (fragancias y productos de cuidado personal).

---

## Archivos del proyecto

```
crm/
├── index.html              # App principal (toda la lógica vive acá)
├── data.js                 # Seed data generado — NO editar a mano
├── seed-data.py            # Script para regenerar data.js desde el xlsx
└── CLAUDE.md               # Este archivo
```

---

## Dominio del cliente

**Grupo MF** vende fragancias y productos de cuidado personal B2B.

### Tipos de cliente
PYME, Cadena de tiendas, Shopping, Supermercado, Farmacia, Perfumería, Outlet, Electrónica, Integrador / Partner

### Canales de adquisición
Google Ads, Meta Ads (Form), Meta Ads (DM), WhatsApp directo, Referido, Web

### Calificación de leads
A (Muy calificado), B (Potencial), C (Frío)

### Estados del pipeline
NUEVO → CONTACTADO → EN COTIZACIÓN → NEGOCIANDO → GANADO | PERDIDO | DESCARTADO | SIN RESPUESTA

### Defaults
- Días para alerta de seguimiento: 14
- Días para alerta de recompra: 45

---

## localStorage keys

- `gmf_leads` — array de objetos lead
- `gmf_ventas` — array de objetos venta
- `gmf_clients_config` — objeto `{ nombreCliente: { dias_recompra: 45 } }`
- `gmf_setup_done` — flag `"1"` para saltear setup screen

---

## Flujo de actualización de datos

```bash
# 1. Asegurate de que el xlsx actualizado esté en ../grupo-mf-workspace/
# 2. Correr el script:
python3 seed-data.py
# 3. Abrir o recargar index.html
```
