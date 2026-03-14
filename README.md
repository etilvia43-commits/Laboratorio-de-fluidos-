# Laboratorio-de-fluidos-
<!DOCTYPE html>
<html lang="es">

<head>

<meta charset="UTF-8">
<title>Laboratorio Virtual - Dinámica de Fluidos</title>

<style>

body{
font-family:Arial;
margin:0;
background:#eef2f7;
}

header{
background:#1e3799;
color:white;
padding:20px;
text-align:center;
}

section{
background:white;
margin:30px;
padding:25px;
border-radius:10px;
box-shadow:0 0 10px rgba(0,0,0,0.1);
}

h2{
color:#1e3799;
}

button{
background:#1e3799;
color:white;
border:none;
padding:10px;
border-radius:5px;
cursor:pointer;
}

input{
padding:5px;
margin:5px;
}

.result{
font-weight:bold;
color:#b71540;
}

</style>

</head>


<body>

<header>

<h1>Dinámica de Fluidos</h1>
<p>Laboratorio virtual interactivo</p>

</header>


<section>

<h2>Introducción</h2>

<p>
Este recurso académico presenta los conceptos fundamentales de dinámica de fluidos,
incluyendo viscosidad, número de Reynolds, ley de Poiseuille y sedimentación de Stokes.
</p>

</section>


<section>

<h2>Viscosidad</h2>

<p>
La viscosidad es la propiedad de un fluido que mide su resistencia a fluir.
</p>

<p><b>Ecuación:</b></p>

<p>τ = μ (du/dy)</p>

<table border="1">

<tr>
<th>Variable</th>
<th>Significado</th>
<th>Unidad</th>
</tr>

<tr>
<td>τ</td>
<td>Esfuerzo cortante</td>
<td>Pa</td>
</tr>

<tr>
<td>μ</td>
<td>Viscosidad dinámica</td>
<td>Pa·s</td>
</tr>

<tr>
<td>du/dy</td>
<td>Gradiente de velocidad</td>
<td>s⁻¹</td>
</tr>

</table>

</section>


<section>

<h2>Número de Reynolds</h2>

<p>Determina el tipo de flujo de un fluido.</p>

<p>Re = ρVD / μ</p>

<ul>

<li>Re < 2000 → Flujo laminar</li>
<li>2000 - 4000 → Transición</li>
<li>Re > 4000 → Turbulento</li>

</ul>

</section>


<section>

<h2>Ley de Poiseuille</h2>

<p>

Describe el flujo laminar en tuberías.

</p>

<p>

Q = (π R⁴ ΔP) / (8 μ L)

</p>

</section>


<section>

<h2>Ley de Stokes</h2>

<p>

Describe la velocidad terminal de una partícula en un fluido.

</p>

<p>

Vt = (2 g r² (ρp − ρf)) / (9 μ)

</p>

</section>



<section>

<h2>Ejercicio Resuelto 1 (Reynolds)</h2>

Datos:

<ul>
<li>ρ = 900 kg/m³</li>
<li>V = 1.5 m/s</li>
<li>D = 0.02 m</li>
<li>μ = 0.05 Pa·s</li>
</ul>

<p>

Re = (ρVD)/μ

</p>

<p>

Re = (900 × 1.5 × 0.02)/0.05

</p>

<p class="result">

Re = 540 → Flujo laminar

</p>

</section>



<section>

<h2>Ejercicio Resuelto 2 (Poiseuille)</h2>

Datos:

<ul>

<li>L = 50 m</li>
<li>R = 0.01 m</li>
<li>μ = 0.2 Pa·s</li>
<li>Q = 0.001 m³/s</li>

</ul>

<p>

ΔP = (8 μ L Q) / (π R⁴)

</p>

<p class="result">

ΔP ≈ 2.5 × 10⁶ Pa

</p>

</section>



<section>

<h2>Ejercicio Resuelto 3 (Stokes)</h2>

Datos:

<ul>

<li>ρp = 2650 kg/m³</li>
<li>ρf = 1000 kg/m³</li>
<li>d = 50 μm</li>
<li>μ = 0.001 Pa·s</li>

</ul>

<p class="result">

Velocidad terminal ≈ 0.0022 m/s

</p>

</section>



<section>

<h2>Ejercicio Interactivo: Reynolds</h2>

Densidad <input id="rho">

Velocidad <input id="vel">

Diámetro <input id="diam">

Viscosidad <input id="vis">

<br><br>

<button onclick="calcRe()">Calcular</button>

<p id="resultadoRe" class="result"></p>

</section>



<section>

<h2>Laboratorio Virtual Poiseuille</h2>

Radio del tubo

<input type="range" id="radio" min="0.005" max="0.02" step="0.001">

<button onclick="calcQ()">Calcular Caudal</button>

<p id="resultadoQ" class="result"></p>

</section>



<section>

<h2>Laboratorio Virtual Stokes</h2>

Radio partícula

<input type="range" id="r" min="0.00001" max="0.0001" step="0.00001">

<button onclick="calcV()">Calcular Velocidad</button>

<p id="resultadoV" class="result"></p>

</section>



<section>

<h2>Reproducibilidad</h2>

<p>

Herramientas utilizadas:

<ul>

<li>HTML</li>
<li>CSS</li>
<li>JavaScript</li>

</ul>

Este recurso fue generado con asistencia de inteligencia artificial y revisado manualmente.

</p>

</section>



<script>

function calcRe(){

rho=parseFloat(document.getElementById("rho").value)

v=parseFloat(document.getElementById("vel").value)

d=parseFloat(document.getElementById("diam").value)

mu=parseFloat(document.getElementById("vis").value)

Re=(rho*v*d)/mu

let tipo=""

if(Re<2000) tipo="Laminar"

else if(Re<4000) tipo="Transición"

else tipo="Turbulento"

document.getElementById("resultadoRe").innerHTML="Re = "+Re.toFixed(2)+" → "+tipo

}



function calcQ(){

r=document.getElementById("radio").value

mu=0.2
L=50
dp=1000

Q=(Math.PI*Math.pow(r,4)*dp)/(8*mu*L)

document.getElementById("resultadoQ").innerHTML="Caudal = "+Q.toFixed(6)+" m³/s"

}



function calcV(){

r=document.getElementById("r").value

g=9.81
rhoP=2650
rhoF=1000
mu=0.001

vt=(2*g*r*r*(rhoP-rhoF))/(9*mu)

document.getElementById("resultadoV").innerHTML="Vt = "+vt.toFixed(4)+" m/s"

}

</script>


</body>
</html>
