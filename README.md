# Full Stack Open — Part 4 · Blog List backend

Backend de la llista de blogs (part 4 del curs Full Stack Open): prova del backend, tests amb `node:test` + SuperTest i autenticació per token.

## Execució local

```bash
npm install      # instal·la dependències
npm run dev      # mode desenvolupament (nodemon, reinicia en cada canvi)
npm start        # mode producció
npm test         # executa els tests (DB de test independent: bloglist_test)
```

El servidor escolta a `http://localhost:3003` (o al port definit per la variable d'entorn `PORT`).

## Endpoints

- `GET /api/blogs` — llista tots els blogs (amb l'usuari creador expandit).
- `POST /api/blogs` — crea un blog (requereix token Bearer; 400 si falten title/url).
- `DELETE /api/blogs/:id` — elimina un blog (només el creador; requereix token).
- `PUT /api/blogs/:id` — actualitza un blog.
- `GET /api/users` — llista els usuaris (amb els seus blogs).
- `POST /api/users` — crea un usuari (username/password >= 3 caràcters, username únic).
- `POST /api/login` — autenticació per token JWT.

## Tests

- `tests/list_helper.test.js` — funcions auxiliars (dummy, totalLikes, favoriteBlog, mostBlogs, mostLikes).
- `tests/blog_api.test.js` — CRUD de blogs amb SuperTest (inclou tests de permís d'eliminació).
- `tests/user_api.test.js` — creació i validacions d'usuaris.

Els tests usen una base de dades separada (`bloglist_test`) i s'executen amb `NODE_ENV=test`.