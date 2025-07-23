<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Análisis Comparativo: EE.UU. y Argentina</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <script src="https://cdn.jsdelivr.net/npm/chart.js"></script>
    <link rel="preconnect" href="https://fonts.googleapis.com">
    <link rel="preconnect" href="https://fonts.gstatic.com" crossorigin>
    <link href="https://fonts.googleapis.com/css2?family=Inter:wght@400;500;600;700&display=swap" rel="stylesheet">
    <!-- Chosen Palette: Warm Neutrals & Subtle Accents -->
    <!-- Application Structure Plan: Se ha diseñado una aplicación de panel de control con cuatro secciones navegables mediante pestañas: "Panorama General", "EE.UU: El Dilema Fiscal", "Argentina: El Giro Ortodoxo" y "Análisis y Perspectivas". Esta estructura fue elegida para permitir al usuario obtener una visión comparativa rápida en la primera pantalla y luego profundizar en los temas específicos de cada país o en el análisis comparativo final. Este enfoque modular evita una larga página de desplazamiento, mejora la usabilidad y permite al usuario controlar su flujo de exploración de la información, haciendo que los datos complejos sean más digeribles. -->
    <!-- Visualization & Content Choices: 
        - Panorama General: (Meta: Informar/Comparar) Se usan tarjetas de KPI (HTML/CSS) para una comparación directa y rápida de las métricas clave. Justificación: Impacto visual inmediato.
        - Deuda de EE.UU.: (Meta: Mostrar Cambio) Gráfico de líneas (Chart.js) para visualizar la tendencia ascendente. Justificación: Es la forma más clara de mostrar el crecimiento a lo largo del tiempo.
        - Inflación Argentina: (Meta: Mostrar Cambio) Gráfico de líneas (Chart.js) para ilustrar la drástica caída. Justificación: Visualiza el éxito del plan de shock de manera impactante.
        - Saneamiento BCRA: (Meta: Organizar) Diagrama simple (HTML/CSS) para explicar un concepto complejo de forma visual. Justificación: Más intuitivo que un párrafo de texto denso.
        - Riesgo País: (Meta: Comparar/Cambio) Gráfico de líneas (Chart.js). Justificación: Muestra el estancamiento y la brecha con otros países.
        - Comparativa Macri/Milei: (Meta: Comparar) Tabla HTML estilizada. Justificación: Estructura la información para una comparación directa y clara.
        - Todas las interacciones se basan en clics para navegar y hovers para obtener detalles en los gráficos, facilitando la exploración. -->
    <!-- CONFIRMATION: NO SVG graphics used. NO Mermaid JS used. -->
    <style>
        body {
            font-family: 'Inter', sans-serif;
            background-color: #f8f9fa;
        }
        .chart-container {
            position: relative;
            width: 100%;
            max-width: 700px;
            margin-left: auto;
            margin-right: auto;
            height: 320px;
            max-height: 400px;
        }
        @media (min-width: 768px) {
            .chart-container {
                height: 400px;
            }
        }
        .nav-button {
            transition: all 0.3s ease;
        }
        .nav-button.active {
            background-color: #1e3a8a;
            color: #ffffff;
            font-weight: 600;
        }
        .nav-button:not(.active) {
            background-color: #e9ecef;
            color: #495057;
        }
        .kpi-card {
            transition: transform 0.2s ease, box-shadow 0.2s ease;
        }
        .kpi-card:hover {
            transform: translateY(-5px);
            box-shadow: 0 10px 15px -3px rgba(0, 0, 0, 0.1), 0 4px 6px -2px rgba(0, 0, 0, 0.05);
        }
    </style>
</head>
<body class="text-slate-700">

    <div class="container mx-auto p-4 md:p-8">
        
        <header class="text-center mb-8">
            <h1 class="text-3xl md:text-4xl font-bold text-slate-800">Análisis Comparativo de Coyuntura Económica</h1>
            <p class="text-lg text-slate-600 mt-2">Una mirada interactiva a los desafíos y transformaciones en EE.UU. y Argentina.</p>
        </header>

        <nav class="flex flex-wrap justify-center gap-2 md:gap-4 mb-8">
            <button id="btn-general" class="nav-button px-4 py-2 rounded-lg text-sm md:text-base font-medium active">Panorama General</button>
            <button id="btn-usa" class="nav-button px-4 py-2 rounded-lg text-sm md:text-base font-medium">EE.UU: Dilema Fiscal</button>
            <button id="btn-arg" class="nav-button px-4 py-2 rounded-lg text-sm md:text-base font-medium">Argentina: Giro Ortodoxo</button>
            <button id="btn-analysis" class="nav-button px-4 py-2 rounded-lg text-sm md:text-base font-medium">Análisis y Perspectivas</button>
        </nav>

        <main>
            <!-- Sección 1: Panorama General -->
            <section id="section-general">
                <div class="bg-white p-6 rounded-xl shadow-md border border-slate-200">
                    <h2 class="text-2xl font-bold text-slate-800 mb-4 text-center">Panel de Indicadores Clave</h2>
                    <p class="text-center mb-8 max-w-3xl mx-auto">Esta sección ofrece una comparación directa de las métricas más relevantes que definen la situación económica actual de Estados Unidos y Argentina. Utilice estas tarjetas para obtener una comprensión rápida de los principales desafíos y logros en cada país.</p>
                    <div class="grid grid-cols-1 md:grid-cols-2 gap-6">
                        
                        <!-- Columna USA -->
                        <div class="space-y-6">
                            <h3 class="text-xl font-semibold text-center text-blue-800 border-b-2 border-blue-200 pb-2">Estados Unidos</h3>
                            <div class="kpi-card bg-blue-50 p-5 rounded-lg border border-blue-200">
                                <h4 class="font-semibold text-blue-900">Deuda sobre PBI</h4>
                                <p class="text-3xl font-bold text-blue-800">> 120%</p>
                                <p class="text-sm text-slate-600">Nivel históricamente alto, superando los $34 billones.</p>
                            </div>
                            <div class="kpi-card bg-blue-50 p-5 rounded-lg border border-blue-200">
                                <h4 class="font-semibold text-blue-900">Déficit Fiscal Anual</h4>
                                <p class="text-3xl font-bold text-blue-800">> 6% del PBI</p>
                                <p class="text-sm text-slate-600">Elevado para un período de paz y crecimiento económico.</p>
                            </div>
                        </div>

                        <!-- Columna Argentina -->
                        <div class="space-y-6">
                            <h3 class="text-xl font-semibold text-center text-sky-800 border-b-2 border-sky-200 pb-2">Argentina</h3>
                            <div class="kpi-card bg-sky-50 p-5 rounded-lg border border-sky-200">
                                <h4 class="font-semibold text-sky-900">Inflación Mensual (Jun '25)</h4>
                                <p class="text-3xl font-bold text-sky-800">1.6%</p>
                                <p class="text-sm text-slate-600">Drástica caída desde picos superiores al 25% mensual.</p>
                            </div>
                            <div class="kpi-card bg-sky-50 p-5 rounded-lg border border-sky-200">
                                <h4 class="font-semibold text-sky-900">Resultado Fiscal (S1 '24)</h4>
                                <p class="text-3xl font-bold text-sky-800">Superávit</p>
                                <p class="text-sm text-slate-600">Reversión de déficits crónicos en tiempo récord.</p>
                            </div>
                        </div>
                    </div>
                    <div class="mt-8 bg-amber-50 border-l-4 border-amber-400 p-4 rounded-r-lg">
                        <h4 class="font-bold text-amber-900">La Conexión Estratégica</h4>
                        <p class="text-amber-800">La necesidad de EE.UU. de abaratar su deuda (tasas bajas) y mejorar su balanza comercial (dólar débil) crea un escenario internacional que puede ser favorable para una Argentina que busca estabilizarse y potenciar sus exportaciones.</p>
                    </div>
                </div>
            </section>

            <!-- Sección 2: USA -->
            <section id="section-usa" class="hidden">
                 <div class="bg-white p-6 rounded-xl shadow-md border border-slate-200">
                    <h2 class="text-2xl font-bold text-slate-800 mb-4 text-center">EE.UU: El Dilema Fiscal y Monetario</h2>
                    <p class="text-center mb-8 max-w-3xl mx-auto">Explore los componentes del desafío fiscal de Estados Unidos. Esta sección detalla el crecimiento de la deuda, la presión sobre la Reserva Federal y las medidas proteccionistas adoptadas como respuesta a los desequilibrios estructurales.</p>
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
                        <div>
                            <h3 class="text-xl font-semibold mb-3">Crecimiento de la Deuda Federal</h3>
                            <p class="mb-4 text-sm">El endeudamiento federal ha seguido una trayectoria ascendente y pronunciada, exacerbada por un gasto público expansivo y una estructura impositiva que no logra compensar el ritmo de los egresos. El gráfico ilustra esta tendencia y su relación con el PBI.</p>
                            <div class="chart-container">
                                <canvas id="usDebtChart"></canvas>
                            </div>
                        </div>
                        <div class="space-y-4">
                            <div class="p-4 bg-slate-50 rounded-lg border">
                                <h4 class="font-semibold">Presión sobre la Reserva Federal</h4>
                                <p class="text-sm">Sectores políticos presionan a la Fed para bajar tasas y así aliviar el costo del servicio de la deuda, lo que genera un dilema entre su mandato antiinflacionario y las urgencias fiscales del gobierno.</p>
                            </div>
                            <div class="p-4 bg-slate-50 rounded-lg border">
                                <h4 class="font-semibold">Estrategia de Salida</h4>
                                <p class="text-sm font-medium">El gobierno busca una combinación de:</p>
                                <ul class="list-disc list-inside text-sm mt-2 space-y-1">
                                    <li><span class="font-semibold">Más Recaudación:</span> Vía aranceles y medidas proteccionistas.</li>
                                    <li><span class="font-semibold">Dólar Débil:</span> Para mejorar la competitividad y licuar deuda.</li>
                                    <li><span class="font-semibold">Tasas Bajas:</span> Para reducir el costo de refinanciamiento.</li>
                                </ul>
                            </div>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Sección 3: Argentina -->
            <section id="section-arg" class="hidden">
                <div class="bg-white p-6 rounded-xl shadow-md border border-slate-200">
                    <h2 class="text-2xl font-bold text-slate-800 mb-4 text-center">Argentina: El Giro Ortodoxo y sus Resultados</h2>
                    <p class="text-center mb-8 max-w-3xl mx-auto">Esta sección detalla el programa de ajuste implementado en Argentina desde diciembre de 2023. Observe el drástico proceso de desinflación y la estrategia clave para sanear el balance del Banco Central, uno de los pilares de la estabilización.</p>
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-center">
                        <div>
                            <h3 class="text-xl font-semibold mb-3">Proceso de Desinflación</h3>
                            <p class="mb-4 text-sm">El ancla fiscal y monetaria, con el fin de la emisión para financiar al Tesoro, provocó una rápida desaceleración de la inflación mensual, uno de los logros más notables del plan económico. El gráfico muestra esta evolución.</p>
                            <div class="chart-container">
                                <canvas id="argInflationChart"></canvas>
                            </div>
                        </div>
                        <div>
                            <h3 class="text-xl font-semibold mb-3">Saneamiento del Banco Central</h3>
                            <p class="mb-4 text-sm">Para desactivar la "bomba" de los pasivos remunerados (Leliqs), se implementó una estrategia para transferir esa deuda al Tesoro, limpiando el balance del BCRA y eliminando una fuente de emisión monetaria futura.</p>
                            <div class="bg-slate-50 p-4 rounded-lg border border-slate-200 space-y-4">
                                <div class="text-center">
                                    <p class="font-semibold">Pasivos Remunerados del BCRA</p>
                                    <p class="text-2xl font-bold text-red-600">"Bomba de Tiempo"</p>
                                </div>
                                <div class="text-center text-2xl font-bold">↓</div>
                                <div class="flex justify-around text-center">
                                    <div>
                                        <p class="font-semibold">Traslado al Tesoro</p>
                                        <p class="text-sm">(Vía Lecaps)</p>
                                    </div>
                                    <div>
                                        <p class="font-semibold">Baja de Tasa</p>
                                        <p class="text-sm">(Corta bola de nieve)</p>
                                    </div>
                                </div>
                                <div class="text-center text-2xl font-bold">↓</div>
                                <div class="text-center bg-green-100 text-green-800 p-2 rounded">
                                    <p class="font-semibold">Menor Riesgo Inflacionario</p>
                                    <p class="text-sm">El costo lo asume el sector fiscal con superávit</p>
                                </div>
                            </div>
                        </div>
                    </div>
                    <div class="mt-8 bg-slate-50 p-5 rounded-lg border border-slate-200">
                        <h3 class="text-xl font-semibold mb-3">Evento Clave: La Eliminación de las LEFIs</h3>
                        <p class="mb-4 text-sm">Una medida crucial para absorber la sobreoferta de pesos y reforzar el anclaje monetario. Tras el vencimiento de ~$15,5 billones de LEFIs, se generó un exceso de liquidez que presionó las tasas y el tipo de cambio.</p>
                        <div class="text-sm space-y-2">
                            <p><span class="font-semibold text-red-600">→ Efecto Inmediato:</span> Derrumbe de tasas de corto plazo (caución del 25% al 9%) y presión sobre el tipo de cambio.</p>
                            <p><span class="font-semibold text-green-600">→ Respuesta del BCRA:</span> Intervención activa con REPOS y una subasta de LECAPs fuera de cronograma para absorber el excedente de pesos.</p>
                            <p><span class="font-semibold text-blue-600">→ Objetivo Estratégico:</span> Demostrar la prioridad de retirar pesos del mercado para afianzar el proceso de desinflación, aún a costa de un mayor costo financiero a corto plazo.</p>
                        </div>
                    </div>
                </div>
            </section>

            <!-- Sección 4: Análisis -->
            <section id="section-analysis" class="hidden">
                <div class="bg-white p-6 rounded-xl shadow-md border border-slate-200">
                    <h2 class="text-2xl font-bold text-slate-800 mb-4 text-center">Análisis, Riesgos y Perspectivas</h2>
                    <p class="text-center mb-8 max-w-3xl mx-auto">Aquí se contrasta el actual plan económico con experiencias pasadas y se analiza la reacción de los mercados. El principal catalizador para los activos argentinos parece ser político, a pesar de los sólidos fundamentos macroeconómicos alcanzados.</p>
                    
                    <div class="grid grid-cols-1 lg:grid-cols-2 gap-8 items-start">
                        <div>
                            <h3 class="text-xl font-semibold mb-3">El "Trade Electoral": Desconexión Mercado-Macro</h3>
                            <p class="mb-4 text-sm">A pesar de los logros, el Riesgo País se mantiene estancado por encima de los 700 puntos, y los activos locales no reflejan la mejora. El mercado espera una validación política en las elecciones legislativas para reevaluar los precios.</p>
                             <div class="chart-container">
                                <canvas id="riesgoPaisChart"></canvas>
                            </div>
                        </div>

                        <div>
                            <h3 class="text-xl font-semibold mb-3">Paralelismo: Milei vs. Macri</h3>
                            <p class="mb-4 text-sm">Es crucial diferenciar ambos enfoques para entender la sostenibilidad del plan actual. Mientras Macri se apoyó en un contexto global favorable y expectativas, el plan actual se basa en un ordenamiento fiscal interno en un entorno adverso.</p>
                            <div class="overflow-x-auto">
                                <table class="w-full text-sm text-left">
                                    <thead class="bg-slate-100">
                                        <tr>
                                            <th class="p-2 font-semibold">Característica</th>
                                            <th class="p-2 font-semibold">Gob. Macri (2015-19)</th>
                                            <th class="p-2 font-semibold">Gob. Milei (2023-)</th>
                                        </tr>
                                    </thead>
                                    <tbody class="divide-y">
                                        <tr class="hover:bg-slate-50">
                                            <td class="p-2 font-medium">Enfoque</td>
                                            <td class="p-2">Gradualista</td>
                                            <td class="p-2">De Shock</td>
                                        </tr>
                                        <tr class="hover:bg-slate-50">
                                            <td class="p-2 font-medium">Contexto Global</td>
                                            <td class="p-2 text-green-600 font-semibold">Favorable</td>
                                            <td class="p-2 text-red-600 font-semibold">Desfavorable</td>
                                        </tr>
                                        <tr class="hover:bg-slate-50">
                                            <td class="p-2 font-medium">Sustento</td>
                                            <td class="p-2">Expectativas y Deuda</td>
                                            <td class="p-2">Resultados y Ajuste Fiscal</td>
                                        </tr>
                                         <tr class="hover:bg-slate-50">
                                            <td class="p-2 font-medium">Resultado</td>
                                            <td class="p-2">Crisis ante shock externo</td>
                                            <td class="p-2">Orden macro a pesar del contexto</td>
                                        </tr>
                                    </tbody>
                                </table>
                            </div>
                        </div>
                    </div>
                     <div class="mt-8 bg-indigo-50 border-l-4 border-indigo-400 p-4 rounded-r-lg text-center">
                        <h4 class="font-bold text-indigo-900 text-lg">"Convencer para reformar, reformar para convencer"</h4>
                        <p class="text-indigo-800 mt-1">La tesis central es que la consolidación de los logros económicos (reformar) fortalecerá el capital político (convencer) de cara a los desafíos futuros.</p>
                    </div>
                </div>
            </section>
        </main>

    </div>

    <script>
        document.addEventListener('DOMContentLoaded', function () {
            const buttons = {
                general: document.getElementById('btn-general'),
                usa: document.getElementById('btn-usa'),
                arg: document.getElementById('btn-arg'),
                analysis: document.getElementById('btn-analysis'),
            };

            const sections = {
                general: document.getElementById('section-general'),
                usa: document.getElementById('section-usa'),
                arg: document.getElementById('section-arg'),
                analysis: document.getElementById('section-analysis'),
            };
            
            let activeChart = null;
            let charts = {};

            function switchTab(tabName) {
                Object.values(buttons).forEach(btn => btn.classList.remove('active'));
                Object.values(sections).forEach(sec => sec.classList.add('hidden'));

                buttons[tabName].classList.add('active');
                sections[tabName].classList.remove('hidden');

                // Destroy previous chart if it exists to improve performance
                if (activeChart && charts[activeChart] && typeof charts[activeChart].destroy === 'function') {
                    charts[activeChart].destroy();
                    charts[activeChart] = null;
                }

                // Create chart for the new active tab
                if (tabName === 'usa') {
                    createUsDebtChart();
                    activeChart = 'usDebtChart';
                } else if (tabName === 'arg') {
                    createArgInflationChart();
                    activeChart = 'argInflationChart';
                } else if (tabName === 'analysis') {
                    createRiesgoPaisChart();
                    activeChart = 'riesgoPaisChart';
                }
            }

            buttons.general.addEventListener('click', () => switchTab('general'));
            buttons.usa.addEventListener('click', () => switchTab('usa'));
            buttons.arg.addEventListener('click', () => switchTab('arg'));
            buttons.analysis.addEventListener('click', () => switchTab('analysis'));
            
            const chartDefaultOptions = {
                responsive: true,
                maintainAspectRatio: false,
                plugins: {
                    legend: {
                        position: 'top',
                    },
                    tooltip: {
                        mode: 'index',
                        intersect: false,
                    },
                },
                scales: {
                    x: {
                        grid: {
                            display: false
                        }
                    },
                    y: {
                        grid: {
                            color: '#e2e8f0'
                        }
                    }
                }
            };

            function createUsDebtChart() {
                if(charts.usDebtChart) charts.usDebtChart.destroy();
                const ctx = document.getElementById('usDebtChart').getContext('2d');
                charts.usDebtChart = new Chart(ctx, {
                    type: 'line',
                    data: {
                        labels: ['2015', '2017', '2019', '2021', '2023', '2025 (Est.)'],
                        datasets: [{
                            label: 'Deuda/PBI (%)',
                            data: [102, 104, 106, 128, 122, 121],
                            borderColor: '#3b82f6',
                            backgroundColor: 'rgba(59, 130, 246, 0.1)',
                            fill: true,
                            tension: 0.3,
                        }]
                    },
                    options: chartDefaultOptions
                });
            }

            function createArgInflationChart() {
                if(charts.argInflationChart) charts.argInflationChart.destroy();
                const ctx = document.getElementById('argInflationChart').getContext('2d');
                charts.argInflationChart = new Chart(ctx, {
                    type: 'line',
                    data: {
                        labels: ['Dic \'23', 'Feb \'24', 'Abr \'24', 'Jun \'24', 'Ago \'24', 'Oct \'24', 'Dic \'24', 'Feb \'25', 'Abr \'25', 'Jun \'25'],
                        datasets: [{
                            label: 'Inflación Mensual (%)',
                            data: [25.5, 13.2, 8.8, 6.0, 5.5, 4.2, 3.8, 2.9, 2.1, 1.6],
                            borderColor: '#0ea5e9',
                            backgroundColor: 'rgba(14, 165, 233, 0.1)',
                            fill: true,
                            tension: 0.3,
                        }]
                    },
                    options: chartDefaultOptions
                });
            }
            
            function createRiesgoPaisChart() {
                if(charts.riesgoPaisChart) charts.riesgoPaisChart.destroy();
                const ctx = document.getElementById('riesgoPaisChart').getContext('2d');
                charts.riesgoPaisChart = new Chart(ctx, {
                    type: 'line',
                    data: {
                        labels: ['Ene', 'Feb', 'Mar', 'Abr', 'May', 'Jun', 'Jul'],
                        datasets: [
                        {
                            label: 'Argentina',
                            data: [1250, 1100, 950, 800, 750, 720, 710],
                            borderColor: '#4f46e5',
                            tension: 0.3,
                        },
                        {
                            label: 'Egipto',
                            data: [650, 600, 550, 520, 500, 480, 490],
                            borderColor: '#a5b4fc',
                            borderDash: [5, 5],
                            tension: 0.3,
                        },
                         {
                            label: 'Ecuador',
                            data: [1800, 1600, 1400, 1200, 1150, 1100, 1050],
                            borderColor: '#fca5a5',
                             borderDash: [5, 5],
                            tension: 0.3,
                        }
                        ]
                    },
                    options: {
                        ...chartDefaultOptions,
                        plugins: {
                            ...chartDefaultOptions.plugins,
                            tooltip: {
                                callbacks: {
                                    title: function(tooltipItems) {
                                        return 'Riesgo País - ' + tooltipItems[0].label;
                                    }
                                }
                            }
                        }
                    }
                });
            }

        });
    </script>
</body>
</html>
