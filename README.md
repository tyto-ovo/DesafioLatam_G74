# DesafioLatam_G74

ejercicios consulta multiples tablas sql

SELECT posts.title, comments.content FROM posts INNER JOIN comments
ON posts.id = comments.post_id;

SELECT posts.title, posts.content, comments.content FROM posts LEFT JOIN comments
ON posts.id = comments.post_id;

SELECT posts.title, posts.content, comments.content FROM posts FULL JOIN comments
ON posts.id = comments.post_id;

SELECT posts.title, posts.content, comments.content FROM posts CROSS JOIN comments

SELECT nombre, precio FROM productos
WHERE precio > (SELECT AVG(precio) FROM productos);

SELECT p.nombre AS nombre_producto, SUM(v.cantidad) AS productos_vendidos
FROM productos p INNER JOIN ventas v
ON p.id = v.producto_id
GROUP BY p.nombre;

SELECT p.title FROM posts p LEFT JOIN comments c
ON p.id = c.post_id
WHERE c.content IS NULL;

SELECT p.title, COUNT(c.id) AS cantidad_comentarios FROM posts p
INNER JOIN comments c
ON p.id = c.post_id
GROUP BY p.title
HAVING COUNT(c.post_id) > 1;

SELECT COUNT(*) AS total_combinaciones FROM posts 
CROSS JOIN comments;
