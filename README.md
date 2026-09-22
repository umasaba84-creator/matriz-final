# matriz-final<!DOCTYPE html>
<html lang="es">
<head>
    <meta charset="UTF-8">
    <meta name="viewport" content="width=device-width, initial-scale=1.0">
    <title>Matriz de Análisis Geopolítico</title>
    <script src="https://cdn.tailwindcss.com"></script>
    <style>
        @import url('https://fonts.googleapis.com/css2?family=Inter:wght@300;400;500;600;700&display=swap');
        body { font-family: 'Inter', sans-serif; }
    </style>
</head>
<body class="bg-slate-50 text-slate-800 min-h-screen">
    <header class="bg-slate-900 text-white border-b border-slate-700 py-6 px-4 sm:px-8">
        <div class="max-w-7xl mx-auto flex flex-col md:flex-row justify-between items-center gap-4">
            <div>
                <h1 class="text-2xl font-bold tracking-tight">Matriz de Análisis Geopolítico</h1>
                <p class="text-slate-400 text-sm mt-1">Plataforma Académica de Evaluación y Gestión de Riesgos Geopolíticos</p>
            </div>
            <span class="bg-slate-800 text-slate-300 text-xs px-3 py-1.5 rounded-full border border-slate-700 font-medium">
                Herramienta Académica / Metodología Prospectiva
            </span>
        </div>
    </header>

    <main class="max-w-7xl mx-auto px-4 sm:px-8 py-8 grid grid-cols-1 lg:grid-cols-12 gap-8">
        <section class="lg:col-span-5 space-y-6">
            <div class="bg-white p-6 rounded-xl border border-slate-200 shadow-sm">
                <h2 class="text-lg font-semibold text-slate-900 mb-4 pb-2 border-b border-slate-100 flex items-center gap-2">
                    <svg class="w-5 h-5 text-indigo-600" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M11 5H6a2 2 0 00-2 2v11a2 2 0 002 2h11a2 2 0 002-2v-5m-1.414-9.414a2 2 0 112.828 2.828L11.828 15H9v-2.828l8.586-8.586z"></path></svg>
                    Registro de Escenario Geopolítico
                </h2>
                
                <form id="risk-form" class="space-y-4" onsubmit="event.preventDefault(); addScenario();">
                    <div>
                        <label for="actor" class="block text-xs font-semibold uppercase text-slate-600 mb-1">País / Actor / Organización</label>
                        <input type="text" id="actor" placeholder="Ej. Federación de Rusia, OPEP, OTAN..." required
                            class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 outline-none transition text-sm">
                    </div>

                    <div>
                        <label for="scenario" class="block text-xs font-semibold uppercase text-slate-600 mb-1">Descripción del Escenario</label>
                        <textarea id="scenario" rows="3" placeholder="Sintetice brevemente el evento prospectivo..." required
                            class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 outline-none transition text-sm resize-none"></textarea>
                    </div>

                    <div class="grid grid-cols-2 gap-4">
                        <div>
                            <label for="probability" class="block text-xs font-semibold uppercase text-slate-600 mb-1">Probabilidad (1-5)</label>
                            <select id="probability" onchange="calculateLiveRisk()" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 outline-none transition text-sm bg-white">
                                <option value="1">1 - Muy Baja</option>
                                <option value="2">2 - Baja</option>
                                <option value="3" selected>3 - Media</option>
                                <option value="4">4 - Alta</option>
                                <option value="5">5 - Muy Alta</option>
                            </select>
                        </div>
                        <div>
                            <label for="impact" class="block text-xs font-semibold uppercase text-slate-600 mb-1">Impacto (1-5)</label>
                            <select id="impact" onchange="calculateLiveRisk()" class="w-full px-3 py-2 border border-slate-300 rounded-lg focus:ring-2 focus:ring-indigo-500 focus:border-indigo-500 outline-none transition text-sm bg-white">
                                <option value="1">1 - Insignificante</option>
                                <option value="2">2 - Menor</option>
                                <option value="3" selected>3 - Moderado</option>
                                <option value="4">4 - Mayor</option>
                                <option value="5">5 - Catastrófico</option>
                            </select>
                        </div>
                    </div>

                    <div id="risk-preview" class="p-4 rounded-lg bg-slate-100 border border-slate-200 transition">
                        <div class="flex justify-between items-center mb-1">
                            <span class="text-xs font-semibold uppercase text-slate-500">Cálculo de Riesgo</span>
                            <span id="risk-badge" class="px-2 py-0.5 text-xs font-bold rounded bg-yellow-100 text-yellow-800">MEDIO</span>
                        </div>
                        <div class="text-2xl font-bold text-slate-900" id="risk-value">9</div>
                        <p class="text-xs text-slate-500 mt-1" id="risk-formula">Fórmula: 3 (Probabilidad) × 3 (Impacto)</p>
                    </div>

                    <button type="submit" class="w-full bg-slate-900 hover:bg-slate-800 text-white font-medium py-2.5 px-4 rounded-lg shadow transition duration-150 ease-in-out text-sm flex items-center justify-center gap-2">
                        <svg class="w-4 h-4" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M12 6v6m0 0v6m0-6h6m-6 0H6"></path></svg>
                        Agregar a la Matriz
                    </button>
                </form>
            </div>
        </section>

        <section class="lg:col-span-7 space-y-6">
            <div class="bg-white p-6 rounded-xl border border-slate-200 shadow-sm">
                <div class="flex flex-col sm:flex-row justify-between items-start sm:items-center gap-4 mb-4 pb-2 border-b border-slate-100">
                    <div>
                        <h2 class="text-lg font-semibold text-slate-900">Matriz de Registros</h2>
                        <p class="text-xs text-slate-500">Escenarios geopolíticos evaluados activamente</p>
                    </div>
                    <button onclick="clearMatrix()" class="text-xs font-medium text-red-600 hover:text-red-800 bg-red-50 hover:bg-red-100 px-3 py-1.5 rounded-lg transition border border-red-200 flex items-center gap-1">
                        <svg class="w-3.5 h-3.5" fill="none" stroke="currentColor" viewBox="0 0 24 24"><path stroke-linecap="round" stroke-linejoin="round" stroke-width="2" d="M19 7l-.867 12.142A2 2 0 0116.138 21H7.862a2 2 0 01-1.995-1.858L5 7m5 4v6m4-6v6m1-10V4a1 1 0 00-1-1h-4a1 1 0 00-1 1v3M4 7h16"></path></svg>
                        Borrar Registros
                    </button>
                </div>

                <div class="overflow-x-auto">
                    <table class="w-full text-left text-xs text-slate-600">
                        <thead class="bg-slate-50 uppercase text-slate-500 border-y border-slate-200">
                            <tr>
                                <th class="py-3 px-3">Actor</th>
                                <th class="py-3 px-3">Escenario</th>
                                <th class="py-3 px-3 text-center">P</th>
                                <th class="py-3 px-3 text-center">I</th>
                                <th class="py-3 px-3 text-center">Riesgo</th>
                                <th class="py-3 px-3 text-center">Clasificación</th>
                            </tr>
                        </thead>
                        <tbody id="matrix-tbody" class="divide-y divide-slate-100">
                            <tr id="empty-row">
                                <td colspan="6" class="py-8 text-center text-slate-400">
                                    No hay registros almacenados en la matriz actual.
                                </td>
                            </tr>
                        </tbody>
                    </table>
                </div>
            </div>
        </section>
    </main>

    <script>
        let scenarios = [];

        function getClassification(risk) {
            if (risk <= 4) return { label: 'Bajo', bg: 'bg-emerald-100', text: 'text-emerald-800', border: 'border-emerald-200' };
            if (risk <= 9) return { label: 'Medio', bg: 'bg-yellow-100', text: 'text-yellow-800', border: 'border-yellow-200' };
            if (risk <= 16) return { label: 'Alto', bg: 'bg-orange-100', text: 'text-orange-800', border: 'border-orange-200' };
            return { label: 'Crítico', bg: 'bg-red-100', text: 'text-red-800', border: 'border-red-200' };
        }

        function calculateLiveRisk() {
            const p = parseInt(document.getElementById('probability').value);
            const i = parseInt(document.getElementById('impact').value);
            const risk = p * i;
            const clasif = getClassification(risk);

            document.getElementById('risk-value').textContent = risk;
            document.getElementById('risk-formula').textContent = `Fórmula: ${p} (Probabilidad) × ${i} (Impacto)`;
            
            const badge = document.getElementById('risk-badge');
            badge.textContent = clasif.label.toUpperCase();
            badge.className = `px-2 py-0.5 text-xs font-bold rounded ${clasif.bg} ${clasif.text}`;

            const preview = document.getElementById('risk-preview');
            preview.className = `p-4 rounded-lg border transition ${clasif.bg} ${clasif.border}`;
        }

        function addScenario() {
            const actor = document.getElementById('actor').value.trim();
            const scenario = document.getElementById('scenario').value.trim();
            const p = parseInt(document.getElementById('probability').value);
            const i = parseInt(document.getElementById('impact').value);
            const risk = p * i;
            const clasif = getClassification(risk);

            if (!actor || !scenario) return;

            scenarios.push({ actor, scenario, p, i, risk, clasif });
            renderTable();

            document.getElementById('actor').value = '';
            document.getElementById('scenario').value = '';
            document.getElementById('probability').value = '3';
            document.getElementById('impact').value = '3';
            calculateLiveRisk();
        }

        function renderTable() {
            const tbody = document.getElementById('matrix-tbody');
            if (scenarios.length === 0) {
                tbody.innerHTML = `
                    <tr id="empty-row">
                        <td colspan="6" class="py-8 text-center text-slate-400">
                            No hay registros almacenados en la matriz actual.
                        </td>
                    </tr>`;
                return;
            }

            tbody.innerHTML = scenarios.map((s) => `
                <tr class="hover:bg-slate-50 transition">
                    <td class="py-3 px-3 font-semibold text-slate-800">${escapeHtml(s.actor)}</td>
                    <td class="py-3 px-3 text-slate-600 max-w-xs truncate" title="${escapeHtml(s.scenario)}">${escapeHtml(s.scenario)}</td>
                    <td class="py-3 px-3 text-center font-mono">${s.p}</td>
                    <td class="py-3 px-3 text-center font-mono">${s.i}</td>
                    <td class="py-3 px-3 text-center font-bold font-mono text-slate-900">${s.risk}</td>
                    <td class="py-3 px-3 text-center">
                        <span class="px-2 py-0.5 text-[10px] font-bold rounded uppercase ${s.clasif.bg} ${s.clasif.text}">
                            ${s.clasif.label}
                        </span>
                    </td>
                </tr>
            `).join('');
        }

        function clearMatrix() {
            if (scenarios.length === 0) return;
            scenarios = [];
            renderTable();
        }

        function escapeHtml(str) {
            return str.replace(/[&<>"']/g, function(m) {
                return { '&': '&amp;', '<': '&lt;', '>': '&gt;', '"': '&quot;', "'": '&#039;' }[m];
            });
        }

        calculateLiveRisk();
    </script>
</body>
</html>
