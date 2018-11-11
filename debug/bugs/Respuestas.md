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


