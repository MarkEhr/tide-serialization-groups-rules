Reglas para definir grupos de serialización en Symfony
===
>Para proyectos desarrollados dentro de TIDE


1. Los nombres serán definidos en snake case y en inglés   

1. Todas las entidades tienen un grupo base, definido como `{nombre_de_la_entidad}_read`   
   * El grupo base estará en todas las propiedades __públicas__ que no sean relaciones
   (e.g. string, int, boolean, etc. ).
   * *Propiedades públicas* hace referencia a las propiedades que quieran ser expuestas en el api, **no**
   a que hayan sido declaradas como públicas. 

1. Por cada propiedad que contenga una relación, se definirá un grupo de serialización nuevo
con el nombre `{nombre_de_la_entidad}_read_{nombre_de_la_propiedad}`

1. Las propiedades deberán tener __un__ solo grupo de serialización de lectura y __uno__ de escritura.

1. Todos los grupos requeridos para escribir o leer la entidad en el caso más común del endpoint serán 
incluidos en el `normalization_context` o `denormalization_context` configurado para la entidad. Si se 
requieren agregar más propiedades a la serialización, los grupos __no__ se agregan en la propiedad, 
si no que el grupo único que tiene la propiedad deberá ser agregado a la configuración de la entidad.

1. Aún cuando se editen entidades ya hechas que no sigan esta guía, las nuevas propiedades que se les 
agreguen deberán seguir esta guía.

> Todas las reglas aplican para grupos de normalización y des-normalización. Únicamente
> cambiar la palabra `read` por `write` para des-serialización 
