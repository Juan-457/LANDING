# LANDING

Repositorio usado como fuente de landings estaticas antes de migrarlas o
publicarlas dentro de otros proyectos.

## Caso documentado: Biotica N2 en Fauno

En mayo de 2026 se migro la landing de Biotica N2 al repo compartido de Fauno:

- Repo destino: `https://github.com/faunotech/fauno-next-gen`
- Carpeta destino: `apps/fenix-web/public/BioticaN2/`
- PR usado: `https://github.com/faunotech/fauno-next-gen/pull/237`
- URL esperada post-merge: `https://fauno.ai/BioticaN2/`
- Hosting tecnico: `https://landingfauno.web.app/BioticaN2/`

La carpeta debia llamarse exactamente `BioticaN2`, no `para-fauno`,
`para fauno` ni otro nombre temporal.

## Que revisar antes de copiar una landing a Fauno

Antes de abrir un PR contra `faunotech/fauno-next-gen`, revisar:

- No incluir archivos de prueba, prototipos o borradores.
- No incluir `.git`, `.github`, workflows, dumps, exports ni archivos internos.
- No incluir `CNAME` dentro de subcarpetas de `public`.
- No incluir imagenes sueltas no referenciadas por HTML/CSS/JS.
- Evitar nombres de archivo con espacios, tildes o caracteres problematicos para URLs.
- Confirmar que todas las rutas internas sean relativas si la landing vive en una subcarpeta.
- Confirmar que no haya placeholders, textos mezclados de otra marca o contenido en otro idioma sin revisar.
- Confirmar que no haya assets externos temporales, por ejemplo URLs de `lh3.googleusercontent.com`.
- Confirmar que no se use Tailwind por CDN ni dependencias que generen estilos en runtime para produccion.
- Revisar typos de marca, por ejemplo `UmanoAI`, `Fauno` y `Biotica`.

## Archivos que pidieron eliminar en la review de Fauno

En el PR de Biotica N2, el reviewer pidio eliminar estos archivos antes de mergear:

- `apps/fenix-web/public/BioticaN2/test.html`
- `apps/fenix-web/public/BioticaN2/WhatsApp Image 2026-05-12 at 12.18.34 PM.jpeg`
- `apps/fenix-web/public/BioticaN2/CNAME`

Motivos:

- `test.html` era un prototipo/borrador: tenia otro diseno, Tailwind via CDN,
  placeholders, texto mezclado en ingles y espanol, imagenes externas efimeras y un
  typo de marca.
- La imagen de WhatsApp no estaba referenciada por la landing y tenia espacios en el
  nombre del archivo.
- `CNAME` solo aplica en el root de GitHub Pages; dentro de
  `apps/fenix-web/public/BioticaN2/` no tiene efecto y genera confusion.

## Flujo recomendado para proximas modificaciones

1. Preparar la landing limpia en este repo.
2. Revisar el checklist anterior.
3. Copiar solo los archivos estaticos necesarios al repo destino.
4. Crear una rama nueva, nunca pushear directo a `main` del repo compartido.
5. Abrir PR contra `faunotech/fauno-next-gen:main`.
6. Revisar los comentarios del bot del PR: suele dejar una preview de Firebase Hosting.
7. Comentar en el PR la URL directa de la landing, por ejemplo:
   `https://landingfauno--pr-XXX-xxxx.web.app/BioticaN2/`.
8. Resolver los comentarios de review en la misma rama.
9. Esperar que los checks pasen antes de pedir merge.
10. Despues del merge, revisar la URL final en el dominio de Fauno.

## Comentarios y preview del PR

En Fauno, el preview no se busca entrando directo a Vercel. Aparece en GitHub,
dentro de los comentarios o checks del Pull Request. En el caso de Biotica N2,
el bot dejo una URL con esta forma:

```text
https://landingfauno--pr-237-re5s42j7.web.app
```

Para revisar una landing dentro de una subcarpeta, agregar el path:

```text
https://landingfauno--pr-237-re5s42j7.web.app/BioticaN2/
```

Cuando se actualiza el PR con nuevos commits, puede tardar unos minutos en aparecer
el nuevo deploy preview. Si el check figura `in_progress`, esperar antes de pedir
aprobacion final.
