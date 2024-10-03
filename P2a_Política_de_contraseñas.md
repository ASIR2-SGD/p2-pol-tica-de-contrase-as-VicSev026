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

# Desarrollo 
## Sistema de contraseñas de Linux
#### Lista de usuarios
/etc/passwd: Guarda usuarios, contraseñas, uid, gid y GECOS

#### Contraseñas ocultas y cifradas
/etc/shadow: se guardan los usuarios, contraseñas cifradas y varios campos que administran el veciminto de la contraseña

## PAM (Plugable authentication Module)
El sistema de módulos encastrados para autenticación (Pluggable Authentication Modules (PAM)) es el método por el cual los sistemas Linux implementan mecanismos de autenticación y permiten que las aplicaciones no tengan necesidad de armar mecanismos propios.

La autenticación en PAM se basa en bibliotecas dinámicas llamadas módulos PAM que se vinculan o encastran unos con otros, formando una «pila» que completa el proceso de validación que requiere la aplicación.

Esta pila se arma tomando en cuenta cuatro procesos se combinan para armar la autenticación y que pueden variar según la aplicación, el entorno, las necesidades de seguridad, los dispositivos disponibles, el tipo de usuario, etc.


## Configuración del servidor
Instalamos libpwquality
```bash
sudo apt install libpwquality-tools libpam-pwquality
```
Me meto en el archivo
```bash
sudo nano /etc/security/pwquality.conf
```
Y le añado lo necesario para el tipo de contraseña que necesito
```bash
minlen = 6
dcredit = -1
ucredit = -1
lcredit = -1
ocredit = -1
```
Para ver si se aplicó+
```bash
sudo nano /etc/pam.d/common-password
```
Y ver si está en funcionamiento debe tener esta linea sin ser comentada
```bash
password requisite pam_pwquality.so retry=3
```

### Pwsocre
|          | Score    | Longitud | Requisitos|Ejemplos|
|----------|----------|----------|-----------|--------|
| No valida| <40 <br>Resultado = 19      | 6        |ucredit = -1 |meera1  |
| Débil    | 38-50 <br> Resultado = 42   | 6        |ucredit=-1<br> dcredit = -1| Cass1la
| Media    | 50-80 <br> Resultado = 71   | 8        |ucredit=-1<br> dcredit = -1 <br> maxrepeat= -1     |L0farience9
| Extrema  |<80       |10        |ucredit=-1<br> dcredit = -1 <br> maxrepeat= -1 <br> ocredit = -1 | J*ta9ak8yro
### Ejercicio
    Contraseña debil (min.8, [0-9], [A-Z], *pepe)
    Contraseña media (min.12, [0-9], [A-Z], [a-z], [#,$...], *pepe)
