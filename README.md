<h1 align="center"> BASE DE DATOS II</h1>
<h1 align="center"> PORTAFOLIO</h1>
<img align='right' src='https://user-images.githubusercontent.com/5713670/87202985-820dcb80-c2b6-11ea-9f56-7ec461c497c3.gif' width='200"'>

➤ enlace de repositorio: **[hito 2](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%202)**

➤ enlace de repositorio: **[hito 3](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%203/procesual)**

➤ enlace de repositorio: **[hito 4](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%204)**
➤ enlace de repositorio: **[hito 5](https://github.com/REXFOX195/base-de-datos-2/tree/master/hito%205/Proyecto%20final)**
```javascript
ejemplo
#verifica si una cadena leila al reves  es la misma cadena
CREATE or replace FUNCTION CADENACAPICUA(cadena TEXT,cadena1 text)
RETURNS text

BEGIN
     DECLARE mensaje text default '';
 CASE
      when mensaje=strcmp(cadena,cadena1) then
      if mensaje=0 then
      SET mensaje = ' cadenas iguales';
      end if;
      ELSE SET mensaje = 'cadenas distintas';
      END CASE;
 RETURN mensaje;
END;

select CADENACAPICUA('dba i', 'dba ii')
```


- 🔭 docente LIC. WILLIAM BARRA
- 🌱 MATERIA BASE DE DATOS II
- 👯 UNIVERSIDAD UNIFRANZ
