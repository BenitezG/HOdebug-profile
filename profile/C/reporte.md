En primer lugar compile los tres programas con las opciones -O0, -O1 y -O3
gcc -O0 profile_me_1.c -o profile_me_1_0.e
y asi con todas
despues los ejecute con time ./progama.e
el programa con la opción -O0 arrojo los siguientes resultados:
real	0m4,549s
user	0m4,237s
sys	0m0,312s

con la opcion -O1:
real	0m3,789s
user	0m3,469s
sys	0m0,312s

y con la opcion -O3:
real	0m0,001s
user	0m0,001s
sys	0m0,000s

con esta ultima opcion dismiuye considerablemente el tiempo de ejecucion

Luego utilice el gprof, compilandolos con las opciones anteriores y agregando -pg antes del -o
ejecute el programa y se generó un archivo gmon.out
luego ejecute gprof programa.e gmon.out
Para la opcion -O0 el resultado fue:
  %   cumulative   self              self     total           
 time   seconds   seconds    calls  ns/call  ns/call  name    
 77.09      2.88     2.88 25000000   115.33   115.33  first_assign
 15.02      3.44     0.56                             main
  8.18      3.75     0.31 25000000    12.24    12.24  second_assign

para la opcion -01:
  %   cumulative   self              self     total           
 time   seconds   seconds    calls  ns/call  ns/call  name    
 82.01      2.53     2.53 25000000   101.04   101.04  first_assign
 14.02      2.96     0.43                             main
  4.08      3.08     0.13 25000000     5.02     5.02  second_assign
  0.33      3.09     0.01                             frame_dummy

en este caso se observa que se gasto un tiempo en hacer un trabajo basura (frame_dummy)

para la opcion -03 no arroja datos

Por ultimo utilice perf y arrojo los siguientes datos
opcion -O0:
0,200646284 seconds time elapsed

opcion -O1:
0,239886997 seconds time elapsed

opcion -O3
0,000981193 seconds time elapsed

Se observa nuevamente que la opcion -O1 genera un aumento en el tiempo de ejecucion y que la opcion -O3 lo disminuye notablemente
