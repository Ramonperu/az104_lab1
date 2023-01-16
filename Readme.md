# LAB 01 - Manage Azure Active Directory Identities
Enero 16 de 2023*, Ramón Peinado Ruiz

Vamos a aprender a usar las identidades de Azure Active Directory

**Objetivos:**

------

• Task 1: Crear y configurar los usuarios de Azure AD. 

• Task 2: Crear grupos de Azure AD con afiliación dinámica.

• Task 3: Crear Azure AD Tenats.

• Task 4: Administrar usuarios de Azure AD.

**Diagrama:**

------

<img src="/img/1ºimagenn.png" alt="2ºimagenn" style="zoom:80%;" />



### TASK 1:

------

Dentro del portal buscamos ***Azure Active Directory> Administrar>Usuarios***, posteriormente clicamos en nuestra cuenta para mostrar la configuración de nuestro perfil, editamos la ubicacion de uso para Estados Unidos y guardamos los cambios



<img src="/img/2ºimagenn.png" alt="2ºimagenn"  />

Volvemos a acceder a los usuarios pero esta vez clicamos en crear un nuevo usuario con estos datos:

| Settings                   | Value               |
| -------------------------- | ------------------- |
| User name                  | az104-01a-aaduser1  |
| Name                       | az104-01a-aaduser1  |
| Let me create the password | enabled             |
| Initial password           | Pa55w.rd124         |
| Usage location             | United States       |
| Job title                  | Cloud Administrator |
| Department                 | IT                  |



Rellenamos los datos dentro del portal



<img src="/img/3ºimagenn.png" alt="3ºimagenn" style="zoom:80%;" />



<img src="/img/4ºimagenn.png" alt="3ºimagenn" style="zoom:80%;" />	Hemos de copiar el nombre del usuario junto con el dominio para usarlo mas adelante

En mi caso seria:

 *az104-01a-aaduser1@ramonperuoutlook.onmicrosoft.com*



A continuación, vamos al usuario recién creado,

***Administrar> Asignar Roles*** y le asignamos el rol de Administrador

<img src="/img/5ºimagenn.png" alt="5ºimagenn"  />



Iniciamos sesión dentro del portal de azure con nuestro nuevo usuario recien creado, vamos a crear el siguiente nuevo usuario a raíz de este ya que el primero es Administrador.

***Home>Azure AD>Administrar>Usuario> +Nuevo usuario***



| Settings                   | Value                |
| -------------------------- | -------------------- |
| User name                  | az104-01a-aaduser2   |
| Name                       | az104-01a-aaduser2   |
| Let me create the password | enabled              |
| Initial password           | Pa55w.rd124          |
| Usage location             | United States        |
| Job title                  | System Administrator |
| Department                 | IT                   |

La pestaña de usuarios quedaría tal que así.

<img src="/img/6ºimagenn.png" alt="6ºimagenn"  />

Nuestro primero objetivo quedaría realizado.

### TASK 2:

------

***Home>Azure AD>Administrar>Licencias***

Activamos las dos licencias de prueba que aparecen

*Las licencias Azure AD Premium P1 o P2 son necesarias para implementar grupos dinámicos*

<img src="/img/7ºimagenn.png" alt="6ºimagenn"  />

Tras realizar esto volvemos a ***Home>Azure AD>Administrar>Grupos*** y creamos un grupo con los siguientes datos



| Setting           | Value                           |
| ----------------- | ------------------------------- |
| Group type        | Security                        |
| Group name        | IT Cloud Administrators         |
| Group description | Contoso IT cloud administrators |
| Membership type   | Dynamic User                    |

Rellenamos los datos

<img src="/img/9ºimagenn.png" alt="9ºimagenn"  />

Y añadimos la siguiente consulta:

| Setting  | Value               |
| -------- | ------------------- |
| Property | jobTitle            |
| Operator | Equals              |
| Value    | Cloud Administrator |

<img src="/img/8ºimagenn.png" alt="8ºimagenn"  />

Finalizamos de crear el grupo, volvemos a la pestaña de grupos y creamos un segundo grupo con estos datos.



2º GRUPO:

| Setting           | Value                            |
| ----------------- | -------------------------------- |
| Group type        | Security                         |
| Group name        | IT System Administrators         |
| Group description | Contoso IT System Administrators |
| Membership type   | Dynamic User                     |

Volvemos a añadirle otra consulta

| Setting  | Value                |
| -------- | -------------------- |
| Property | jobTitle             |
| Operator | Equals               |
| Value    | System Administrator |



 3º GRUPO:

| Setting           | Value                           |
| ----------------- | ------------------------------- |
| Group type        | Security                        |
| Group name        | IT Lab Administrators           |
| Group description | Contoso IT cloud administrators |
| Membership type   | Assigned                        |

<img src="/img/10ºimagenn.png" alt="8ºimagenn"  />

Tras esperar unos minutos(Se puede alargar) confirmamos que cada usuario esta asignado a su grupo dinamico

*az104-01a-aaduser1* ha de aparecer en IT Cloud Administrator

<img src="/img/11ºimagenn.png" alt="11ºimagenn"  />

*az104-01a-aaduser2 ha de aparecer en IT System Administrator*

<img src="/img/12ºimagenn.png" alt="12ºimagenn"  />

### TASK 3:

------

***Home>Azure AD>Administrar Tenants>+Create***

<img src="/img/13ºimagenn.png" alt="12ºimagenn"  />

| Setting        | Value                  |
| -------------- | ---------------------- |
| Directory Type | Azure Active Directory |

Clicamos en next: configuracion y rellenamos con los siguientes datos

| Setting             | Value                |
| ------------------- | -------------------- |
| Organization name   | Contoso Lab          |
| Initial domain name | cualquier DNS valido |
| Country/Region      | System Administrator |

Revisamos y creamos

Comprobamos que se ha creado y que podemos cambiar entre los dos tenants

<img src="/img/14ºimagenn.png" alt="14ºimagenn"  />

### TASK 4:

------

Dentro del tenan recien creado vamos a crear un nuevo usuario con los siguientes datos

| Settings                   | Value                |
| -------------------------- | -------------------- |
| User name                  | az104-01b-aaduser1   |
| Name                       | az104-01b-aaduser1   |
| Let me create the password | enabled              |
| Initial password           | Pa55w.rd124          |
| Usage location             | United States        |
| Job title                  | System Administrator |
| Department                 | IT                   |

<img src="/img/15ºimagenn.png" alt="15ºimagenn"  />

Volvemos a copiar el nombre con el dominio que en nuestro caso seria:

 *az104-01b-aaduser1@ramonperuoutlook.onmicrosoft.com*

Regresamos al tenant predeterminado y repetimos este ultimo paso, entramos al perfil y le añadimos afiliacion al grupo de IT Lab Administrator, la lista de usuarios quedaria tal que asi:

<img src="/img/16ºimagenn.png" alt="16ºimagenn"  />



### Eliminación Recursos

------

Home> Directorio ***Predeterminado>Licencias>Todos los productos> Azure AD Premium P2***

<img src="/img/17ºimagenn.png" alt="17ºimagenn"  />

Borramos el usuario invitado desde la pestaña de usuarios del directorio predeterminado

<img src="/img/18ºimagenn.png" alt="18ºimagenn"  />

Borramos los grupos y demas usuarios

<img src="/img/19ºimagenn.png" alt="18ºimagenn"  />

Y por ultimo paso borramos el tenant

<img src="/img/20ºimagenn.png" alt="20ºimagenn"  />

<img src="/img/21ºimagenn.png" alt="21ºimagenn"  />

<img src="/img/22ºimagenn.png" alt="22ºimagenn"  />

Obtenemos los permisos para eliminar y terminamos.

<img src="/img/23ºimagenn.png" alt="23ºimagenn"  />
