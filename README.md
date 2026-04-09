# KPIFlow — Panel de Control Empresarial

Dashboard empresarial con KPIs generados automáticamente, login, registro y perfil de usuario.

## Estructura

```
dashboard/
├── app.py                  # Flask app principal
├── requirements.txt
├── dashboard.db            # SQLite (se crea automáticamente)
└── templates/
    ├── base.html           # Layout base
    ├── login.html          # Pantalla de inicio de sesión
    ├── register.html       # Registro de nuevo usuario
    ├── dashboard.html      # Panel principal con KPIs y gráficas
    └── profile.html        # Perfil y cambio de contraseña
```

## Instalación y ejecución

```bash
cd dashboard
pip install -r requirements.txt --break-system-packages
python app.py
```

Abre el navegador en: **http://localhost:5000**

## Cuenta demo rápida

En la pantalla de login pulsa **"Acceder con cuenta demo"** para entrar directamente.

O crea tu propia cuenta en `/register`.

## Funcionalidades

### Auth
- Registro con nombre, empresa, email y contraseña
- Login con hash de contraseña (werkzeug)
- Sesión con Flask session
- Demo user de acceso rápido

### Dashboard
- 8 KPIs principales: Ingresos, Beneficio, Clientes, Churn, MRR, ARR, NPS, LTV/CAC
- Gráfica de barras: Ingresos vs Gastos vs Beneficio (Chart.js)
- Gráfica donut: Distribución por canal de ventas
- Gráfica funnel: Embudo de conversión horizontal
- Tabla de top productos con barra de margen
- Objetivos del trimestre con progress bars
- Feed de actividad reciente
- Selector de período (Q1–Q4)
- Botón "Regenerar datos" que llama a la API sin recargar
- Resumen ejecutivo automático en texto

### Perfil
- Editar nombre y empresa
- Cambiar contraseña
- Zona de peligro (exportar / eliminar cuenta)

### API
- `GET /api/kpis?period=Q3+2025` → JSON con todos los KPIs (sin autenticación requerida internamente, sí requiere sesión)

## Variables de entorno

```bash
SECRET_KEY=tu-clave-secreta  # Opcional, hay una por defecto para desarrollo
```

## Tech stack

- **Backend**: Flask + SQLite (sin ORM externo)
- **Auth**: Werkzeug password hashing
- **Frontend**: HTML/CSS/JS vanilla + Chart.js 4.4
- **Tipografía**: Syne + DM Sans + DM Mono
- **Sin dependencias de Node ni npm**
