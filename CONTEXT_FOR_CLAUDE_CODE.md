# Bariloche 2026 — Contexto del proyecto

## Qué es esto
App web de planificación de viaje a Bariloche (14–18 agosto 2026) para dos personas:
- **Santi** (Santiago Nahuel Hernández) — viaja desde Mendoza (MDZ)
- **Amigo** — viaja desde Buenos Aires (BUE)

## Qué hace la app
- Planificador interactivo de viaje con 6 secciones: Resumen, Vuelos, Hospedaje, Ski & Equipo, Actividades, Traslados
- Checkboxes para "seleccionar" una opción por categoría (vuelo, hospedaje, equipo, etc.)
- Las selecciones se sincronizan automáticamente al Resumen
- Totales separados por persona (Santi vs Amigo, distintos orígenes = distintos precios de vuelo)
- Agregar / editar / eliminar ítems en todas las secciones via modal
- Estado guardado en localStorage

## Stack
- HTML + CSS + JS vanilla, un solo archivo `index.html`
- Sin dependencias externas salvo Tabler Icons (CDN)
- Diseño que usa CSS variables de claude.ai (--color-text-primary, etc.) — hay que reemplazarlas con valores reales para que funcione standalone

## Lo que hay que hacer al crear el repo
1. Crear `index.html` con la app completa (ver sección abajo)
2. Reemplazar las CSS variables de claude.ai por valores reales (light + dark mode con media query)
3. Agregar `README.md`
4. `git init`, primer commit, conectar a GitHub

## CSS variables a reemplazar
En la app se usan estas variables del host (claude.ai). Para standalone hay que definirlas:

```css
:root {
  --color-background-primary: #ffffff;
  --color-background-secondary: #f5f5f4;
  --color-background-tertiary: #eeede9;
  --color-text-primary: #1a1a18;
  --color-text-secondary: #6b6b68;
  --color-text-tertiary: #9b9b98;
  --color-border-tertiary: rgba(0,0,0,0.12);
  --color-border-secondary: rgba(0,0,0,0.22);
  --color-border-primary: rgba(0,0,0,0.35);
  --font-sans: -apple-system, BlinkMacSystemFont, 'Segoe UI', sans-serif;
  --font-serif: Georgia, serif;
  --border-radius-md: 8px;
  --border-radius-lg: 12px;
  --border-radius-xl: 16px;
}

@media (prefers-color-scheme: dark) {
  :root {
    --color-background-primary: #1c1c1a;
    --color-background-secondary: #252523;
    --color-background-tertiary: #2e2e2b;
    --color-text-primary: #f0ede8;
    --color-text-secondary: #a8a8a4;
    --color-text-tertiary: #6b6b68;
    --color-border-tertiary: rgba(255,255,255,0.10);
    --color-border-secondary: rgba(255,255,255,0.18);
    --color-border-primary: rgba(255,255,255,0.28);
  }
}
```

## Datos precargados en la app
### Vuelos
- Santi: MDZ–BRC–MDZ ~$350.000 ARS
- Amigo: BUE–BRC–BUE ~$260.000 ARS

### Hospedaje (14–18 ago, ~$100.000 p/p)
- Villa los Coihues (Airbnb + Booking)
- Bariloche Sur (Airbnb)
- Airbnb opción 3 y 4 (centro)
- Hotel Booking 1 y 2
- Hospedaje Penthouse 1004, Moving Hostel, Hostel Achalay (Hostelworld)
- Villa Catedral (Airbnb AR, precio en USD)

### Ski — Sáb 15 ago, Cerro Catedral
- Pase: $160.000
- Equipo: Epic Bariloche $52k / Nieve Austral $53.5k / Travesía Catedral $55k
- Ropa de nieve: ~$65.000 (casco + antiparras incluidos)

### Actividades — Dom 16 ago
- 2do día Catedral, Piedras Blancas (trineos), Cerro Otto, Llao Llao + Campanario, Circuito Chico

### Traslados
- Aeropuerto ↔ Hospedaje, Hospedaje ↔ Catedral, excursiones — todos a cotizar

## Mejoras posibles para el repo
- [ ] Export a PDF del resumen
- [ ] Compartir estado via URL (encode en base64)
- [ ] Notas por día en el itinerario (editable)
- [ ] Campo de presupuesto máximo con alerta visual
- [ ] Modo "comparar" para ver dos hospedajes side by side
