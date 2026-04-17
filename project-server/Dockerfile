FROM denoland/deno:1.38.4

WORKDIR /app/project-server

COPY ./project-server/deno.jsonc ./
COPY ./project-server/deps.ts ./

RUN deno cache --no-lock deps.ts

COPY ./project-server ./
COPY ./shared ../shared/

RUN rm -f deno.lock && deno cache --reload ./api/main.ts && deno cache ./collab/main.ts

CMD ["run", "--allow-net", "--allow-env", "--allow-read=/app/project-server/,/usr/bin/deno", "api/main.ts"]