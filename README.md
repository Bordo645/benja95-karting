# 🏁 Benja #95 — Karting Performance Tracker

Panel oficial de seguimiento de rendimiento de Benjamín Gartner en pista.

## 🚀 Setup en 3 pasos

### 1. Supabase — Crear la tabla

Entrá a tu [Supabase Dashboard](https://supabase.com/dashboard) → tu proyecto → **SQL Editor** y ejecutá:

```sql
CREATE TABLE IF NOT EXISTS sessions (
  id uuid DEFAULT gen_random_uuid() PRIMARY KEY,
  created_at timestamp with time zone DEFAULT now(),
  date date NOT NULL,
  circuit text NOT NULL,
  type text NOT NULL DEFAULT 'Prueba',
  position integer,
  total_time text,
  best_lap text,
  worst_lap text,
  laps integer,
  temperature numeric,
  weather text,
  notes text
);

-- Habilitar acceso público (para uso familiar)
ALTER TABLE sessions ENABLE ROW LEVEL SECURITY;
CREATE POLICY "Allow all" ON sessions FOR ALL USING (true) WITH CHECK (true);
```

### 2. Obtener credenciales

En Supabase: **Settings → API**

- **Project URL** → copiá el valor de `URL`
- **Anon Key** → copiá el valor de `anon / public`

### 3. Subir a GitHub Pages (gratis)

```bash
# Clonar / iniciar repo
git init
git add index.html README.md
git commit -m "🏁 Benja #95 — Initial launch"
git branch -M main
git remote add origin https://github.com/TU_USUARIO/benja95-karting.git
git push -u origin main
```

Luego en GitHub: **Settings → Pages → Source: Deploy from branch → main → / (root) → Save**

Tu página quedará en: `https://TU_USUARIO.github.io/benja95-karting`

---

## 📱 Primer uso

Al abrir la página por primera vez, aparece un modal pidiendo las credenciales de Supabase.

- Ingresás URL + Anon Key → clic en **Guardar y conectar**
- Los datos quedan guardados en el navegador (localStorage)
- Próximas visitas se conectan automáticamente
- También podés usar **modo local** sin Supabase (los datos quedan en el navegador)

---

## 🎯 Funcionalidades

| Función | Descripción |
|---|---|
| Registrar sesión | Prueba libre, Clasificación, Competencia, Entrenamiento |
| Circuito | Nombre libre + autocompletado de circuitos ya cargados |
| Tiempos | Total, mejor vuelta, peor vuelta |
| Clima | Temperatura + condición (soleado, lluvia, húmedo, etc.) |
| Posición | Para días de competencia |
| Vueltas | Cantidad total de vueltas |
| Notas | Observaciones, setup, sensaciones del piloto |
| Historial | Filtros por tipo, circuito y año |
| Circuitos | Vista resumen por pista con best lap y podios |
| Stats globales | Sesiones totales, circuitos, mejor vuelta, podios |

---

## 🏢 Sponsor

**BolsaPlast SRL** — Sponsor oficial del proyecto Benja #95

---

*Un proyecto familiar. La pasión por la velocidad no se hereda, se enciende.*
