# Política de contraseñas

## Contexto
Por defecto, la mayoría de sistemas operativos, vienene con una política de contraseña muy laxa, una contraseña segura presenta una barrera más al atacante, que en su intento de acceder al sistema, indudablemete dejará más rastro y en algunos casos a provocar el abandondo de ataque.

## Objetivos
* Entender el sistema de contraseñas del sistema operativo linux
* Entender el PAM (Plugable authentication Module)
* Instalar y configurar la libreria _pwquality_
* Comprobar y verificar que se ha llevado la práctica de forma correcta
* Documentar la práctica.
___

### Ejercicio
    Contraseña debil (min.8, [0-9], [A-Z], *pepe)
    Contraseña media (min.12, [0-9], [A-Z], [a-z], [#,$...], *pepe)

Restricciones, contraseña1 que falla, pwscore, contraseña2 buena, pwscore