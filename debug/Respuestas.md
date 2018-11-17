bugs:

add_array_dynamic:
el bug esta en que se ocupan mas lugares de memoria de los necesarios.
en la linea 7 hay que suplantar <= n + 1 por < n.

add_array_static:
error similar, el programa considera posiciones de memoria extras que contienen basura.

add_array_segfault:
mismo error que los anteriores
y además, se generan dos punteros a enteros (a y b, linea 14), pero no se aclara la cantidad de memoria asignada a esos punteros. Para corregirlo hay que asignarle el tamaño del array.

sigsegv:
C:

el small no tira y el big tira error de segmentación.
al ejecutar ulimit -s unlimited eliminamos la restriccion en el tamaño del stack pudiendose ejecutar ambos programas
tecnicamente no es debugging porque el programa anda, sino que es problema de manejo de datos de la pc
dividir las cuentas en cuentas mas chicas, alocando menos cantidad de memoria para cada una.

funny:
al utilizar la opcion -DDEBUG se ejecutan ciertas partes del codigo que de otra manera no lo harian.

fpe:
Al incluir -DTRAPFPE se puede utilizar la funcion set_fpe_x87_sse(). Para poder linkear esta funcion hay que compilar el programa mediante el codigo del programa y el codigo fpe_x87_sse.c.
Esto sería:
gcc programa.c fpe_x87_sse/fpe_x87_sse.c comparison.c -DTRAPFPE -Ifpe_x87_sse -lm
 -o programa.e
Como dice en la nota se tiene que agregar la opcion -lm y aclarar la carpeta donde se busca el archivo .h
Al agregar la opcion -DTRAPFPE cuando queremos ejecutar una operación prohibida sale este mensaje:
Excepción de coma flotante (`core' generado)
Sin embargo cuando no agregamos la opcion -DTRAPFPE la salida del programa al hacer una operacion prohibida no cambia, sino que se ejecuta normalmente.
