# 💸 Personal Finance Tracker (WPF + C#)

> **Aplicación de escritorio** desarrollada en **.NET (WPF)** para la gestión de gastos personales, presupuestos y registros financieros mensuales utilizando archivos **CSV** como almacenamiento principal.

---

## 🧭 Descripción General

**Personal Finance Tracker** es una herramienta de escritorio que permite registrar, visualizar y analizar gastos personales de manera simple y automática.  
El sistema reemplaza la gestión manual en Excel por una interfaz moderna donde el usuario puede:
- Ingresar nuevos gastos desde un formulario.
- Visualizar los registros ordenados automáticamente por fecha.
- Separar gastos por categorías (Alimentación, Transporte, Higiene, Otros, etc.).
- Controlar ingresos, ahorros y saldos disponibles.
- Integrar múltiples fuentes de datos CSV (por ejemplo: *Pluxee*, *Gastos Generales*, *Resumen Mensual*).

---

## 🎯 Objetivos del Proyecto

1. **Eliminar la necesidad de editar manualmente Excel.**
2. **Automatizar la inserción ordenada de registros por fecha.**
3. **Centralizar los gastos e ingresos en una interfaz intuitiva.**
4. **Permitir exportar o actualizar datos en formato CSV.**
5. **Ofrecer una base extensible para futuros módulos (gráficos, estadísticas, sincronización en la nube, etc.).**

---

## 🏗️ Arquitectura del Proyecto

El sistema sigue una arquitectura **MVVM (Model-View-ViewModel)** típica de aplicaciones WPF modernas.

```
📦 PersonalFinanceTracker
├── 📁 Models
│   ├── Expense.cs
│   ├── Income.cs
│   ├── BudgetSummary.cs
│   └── Category.cs
│
├── 📁 ViewModels
│   ├── MainViewModel.cs
│   ├── ExpenseViewModel.cs
│   ├── BudgetViewModel.cs
│   └── SettingsViewModel.cs
│
├── 📁 Views
│   ├── MainWindow.xaml
│   ├── ExpenseForm.xaml
│   ├── BudgetSummary.xaml
│   └── SettingsView.xaml
│
├── 📁 Services
│   ├── CsvService.cs           # Lectura/escritura de archivos CSV
│   ├── FileDialogService.cs    # Manejo de archivos locales
│   └── SortingService.cs       # Ordenamiento automático por fecha
│
├── 📁 Data
│   ├── expenses.csv
│   ├── budget.csv
│   └── income.csv
│
├── 📁 Helpers
│   └── RelayCommand.cs
│
├── App.xaml
└── README.md
```

---

## 🧩 Módulos Principales

### 1. **Registro de Gastos**
Permite ingresar los datos de cada gasto con los campos:
- **Fecha**
- **Concepto**
- **Categoría**
- **Monto**
- **Comentario**
- **Pluxee (opcional)**

Cada registro se guarda automáticamente en `expenses.csv` y se inserta en la posición correcta según la fecha (más reciente primero).

---

### 2. **Presupuesto Mensual**
Representa el estado financiero mensual en base a:
- **Arriendo**
- **Celular**
- **Gimnasio**
- **Transporte**
- **Alimentación**
- **Higiene**
- **Otros Gastos**
- **Total Gastos**
- **Ahorro Objetivo**
- **Saldo Disponible**
- **Total Disponible**
- **Pluxee Disponible**

Se carga desde `budget.csv` y se actualiza automáticamente al agregar nuevos gastos.

---

### 3. **Ingresos**
Registro de ingresos como sueldo, bonos o ingresos variables.  
Los datos se almacenan en `income.csv` y se integran al resumen financiero mensual.

---

### 4. **Visualización y Reportes**
- Listado de movimientos ordenado por fecha descendente.
- Filtro por categoría, rango de fechas o monto.
- Cálculo dinámico de totales por categoría.
- Resumen general con indicadores clave:
  - 💰 Total Gastado  
  - 🏦 Saldo Disponible  
  - 🎯 Ahorro Alcanzado  

*(Este módulo se expandirá en versiones futuras para incluir gráficos con OxyPlot o LiveCharts.)*

---

## 💾 Estructura de Datos (CSV)

### `expenses.csv`
| Fecha | Concepto | Categoría | Monto | Comentario | Pluxee |
|--------|-----------|-----------|--------|-------------|---------|
| 05-11-2025 | Café Starbucks | Alimentación | 4500 | Reunión con equipo |  |
| 07-11-2025 | Shampoo Pantene | Higiene | 8900 |  |  |
| 08-11-2025 | Ticket Cine | Entretenimiento | 7500 | Película nueva |  |
| 09-11-2025 | Gasolina | Transporte | 25000 |  |  |
| 10-11-2025 | Almuerzo Sushi | Alimentación | 12000 | Comida con clientes |  |

---

### `budget.csv`
| Pluxee Gasto | Arriendo | Celular | Copilot Pro | Gimnasio | Transporte | Alimentación | Higiene | Otros Gastos | Total Gastos | Ahorro Objetivo | Saldo Disponible | Total Disponible | Pluxee Disponible |
|---------------|-----------|----------|--------------|-----------|--------------|----------------|----------|----------------|-----------------|------------------|------------------|------------------|------------------|
|  | 300000 | 8000 | 15000 | 25000 | 40000 | 180000 | 12000 | 5000 | 580000 | 150000 | 320000 | 470000 | 90000 |

---

### `income.csv`
| Fecha | Concepto | Categoría | Monto | Comentario |
|--------|-----------|-----------|--------|-------------|
| 01-11-2025 | Sueldo | Ingreso Líquido | 1200000 | Pago mensual |  
| 03-11-2025 | Freelance Proyecto Web | Ingreso Extra | 250000 | Proyecto de diseño web |  
| 06-11-2025 | Venta de Libros | Ingreso Extra | 80000 |  |  

---

## 🧰 Tecnologías Utilizadas

| Área | Tecnología |
|------|-------------|
| Framework | .NET 8 (WPF) |
| Lenguaje | C# 12 |
| Patrón de Arquitectura | MVVM |
| UI | WPF XAML con estilos modernos |
| Persistencia | Archivos CSV |
| Librerías sugeridas | CsvHelper, CommunityToolkit.Mvvm, LiveCharts (futuro) |

---

## 🚀 Funcionalidades Planeadas

| Estado | Funcionalidad |
|--------|----------------|
| ✅ | Ingreso manual de gastos |
| ✅ | Lectura y escritura CSV |
| ✅ | Ordenamiento automático por fecha |
| ⏳ | Filtro por categoría y fecha |
| ⏳ | Reporte de totales por categoría |
| ⏳ | Gráficos de gasto mensual |
| 🧩 | Exportación a Excel |
| 🧩 | Sincronización en la nube (Google Drive / OneDrive) |

---

## ⚙️ Cómo Ejecutar el Proyecto

1. **Clona el repositorio**
   ```bash
   git clone https://github.com/tuusuario/PersonalFinanceTracker.git
   cd PersonalFinanceTracker
   ```

2. **Abre el proyecto en Visual Studio**
   - Asegúrate de tener instalado **.NET 8 SDK**.
   - Compila el proyecto (`Ctrl + Shift + B`).

3. **Ejecuta la aplicación**
   - Pulsa **F5** o **Ctrl + F5**.
   - Se abrirá la ventana principal con el listado de gastos y un botón “Agregar Gasto”.

---

## 🧑‍💻 Desarrollo Futuro

- [ ] Implementar validación de datos en formulario.
- [ ] Mejorar diseño visual con Material Design in XAML Toolkit.
- [ ] Añadir panel de estadísticas.
- [ ] Crear sistema de respaldo automático de CSV.
- [ ] Generar informes PDF.

---

## 🧾 Licencia

Este proyecto se distribuye bajo la licencia **MIT**, lo que permite su libre uso y modificación con atribución.

---

## ✨ Autor

**Mauricio**  
Ingeniero Civil Informático  
📍 Chile  
💼 Proyecto personal de automatización financiera
