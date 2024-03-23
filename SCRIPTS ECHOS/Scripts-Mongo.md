# Scripts de Mongo
**_Juan Mateo hernández De Luna_**


**Ver bases de datos o colecciones**
  ```  show dbs```

**Usar una collection y/o base**
   ```use dbs```

**Crear una collecion**
     ```db.createCollection()```

**Usar la base que creaste (Eje. dbTDAH)**
    ```use dbTDAH```

**Ver tus colleciones**
    ```show collections```

**Ver todos los datos de: "empleados"** 
    ```db.empleados.find ( )```

**Insertar un dato en "empleados"**
  ```  db.empleados.insertOne({ nombre: 'Juan', edad: 19 })```

**Insertar Uno**
```db.libros.insertOne({"_id":10, "titulo" : "Los enamorados infieles", "autor":"La chupitos", "precio":1234.10})```

**db.libros.updateOne**
```({_id:10},{$set:{precio:10.2, "cantidad":50}}```

**INC** 
_Incrementa el valor de un campo_
```db.libros.updateMany({"_id":9},{$inc:{precio:5}})```

**MUL**
_Multiplica el valor de un campo_
```db.libros.updateMany({cantidad:{$gt:20}},{$mul:{precio:2}})```

**REPLACE**
_Remplaza un documento completo_
```db.libros.replaceOne( {"_id":10},{"titulo":"Las pato aventuras del Chompiras"})```

**BORRAR DOCUEMNTOS**
```db.libros.deleteOne( {"titulo":'Angel y Alsion'})```

**BORRAR VARIOS**
```db.libros.deleteMany( { cantidad: { $gt: 20 } })```

**BUSCAR CON UNA PALABRA**
```db.libros.find({"titulo":/t/})```

**ORDENAR ACENDENTEMENTE LOS LIBROS**
```db.libros.find({}, { titulo: 1, precio: 1, _id: 0 }).sort({ titulo: -1 })```

**BUSCAR LOS QUE TERMINES CON "TOS"**
```db.libros.find({"titulo":/tos$/})```

**BUSCAR UNO QUE EMPIECE CON "M"**
```db.libros.find({"titulo":/^M/})```

**TODOS LO QUE CONTENGA LA PALABRA "PARA"**
```db2> db.libros.find({"titulo":{$regex:'para'}}) usando regex```

**En libros de editorial "Biblio" con precio > 40 o de la editorial "Planeta" con precio > 30**
```db.libros.find({ $or: [{ $and: [{ editorial: 'Biblio' }, { precio: { $gt: 40 } }]}, { $and: [{ precio: { $gt: 30 } }, { editorial: 'Planeta' }]}] })```

## METODOS DE ORDENAMIENTO 
**Mostrar todos los titulos y precios
AHORA EN ORDEN (ARRIBA - ABAJO)**
```db.libros.find({},{titulo:1,precio:1,_id:0}).sort({titulo:1})```

**Y AHORA (ABAJO - ARRIBA)**
```db.libros.find({},{titulo:1,precio:1,_id:0}).sort({titulo:-1})```

**________SKIP**
_SKIP (SALTAR ALGUNOS DOCUMENTOS)_
Este salta los primeros 3 datos
```db.libros.find({}, { "titulo": 1, "precio": 1, "_id": 0, "editorial": 1 }).skip(3)```

**SIZE (NUMERO DE DOCUMENTOS QUE DEVUELVE LA CONSULTA)**
```db.libros.find({}, { "titulo": 1, "precio": 1, "_id": 0, "editorial": 1 }).size()```

**LIMIT**
```db.libros.find({}, { "titulo": 1, "precio": 1, "_id": 0, "editorial": 1 }).limit(2)```

**PONERLOS EN ORDEN Y MOSTRAR LOS PRIMEROS 3**
```db.libros.find({}, { "titulo": 1, "precio": 1, "_id": 0, "editorial": 1 }).sort({"titulo":1}).limit(3)```

**ELIMINAR COMPLETAMNETE LA BASE ACTUAL**
```db.dropDatabase()```

**ELIMINA UNA COLECCION**
```db.dropDatabase()```



