# lav

> Lavi's practice run

## First steps

Pentru a nu avea probleme cu citirea codului:
- Instaleaza Visual Studio Code
https://code.visualstudio.com/
- Instaleaza o extensie pentru formatul .vue
(vezi extensie.png)

## Structura proiect

Tot ce te intereseaza pe tine se afla in src/

Vue.js este modular, rezultatul final este alcatuit din componente independente.
Fiecare componenta (cu extensia .vue) are trei parti:
- Template (pseudo-HTML)
- Script (Loc unde se defineste logica (metode, script-uri, etc) cat si continutul dinamic
- Style (CSS)

## Structura modulara

ca sa intelegi care e treaba cu componentele, imagineaza-ti cum ar putea arata pagina noastra:
<template> //o sa intelegi in curand care e treaba cu template
    <div>
        <navbar></navbar>
        <news></news>
        <files></files>
        <chat></chat>
        <footer></footer>
    </div>
</template>

In exemplul de mai sus navbar, news, files, chat si footer sunt componente. Template-ul de mai sus ar apartine componentei principale (App.vue)

Mai de parte, sa ne imaginam componenta navbar
<template>
    <div class="nav">
        <span>Secretariat Virtual</span>
        <loginbox></loginbox>
    </div>
</template>

In exemplul de mai sus, observi un mix de HTML normal cu o noua componenta - loginbox.
Componentele sunt nestable, which is nice.

Voi intra mai in amanunt in componentele pe care ti le-am pregatit.
Start from App.vue and then go down the rabbit hole.

Spor!

PS: Nu te grabi sa rulezi aplicatia. Arata ca naiba si nu vei intelege nimic din ea. Citeste-mi intai notitele

## Build Setup

``` bash
# deschide un folder cu proiecte (let's call it C:\proiecte)
c:
cd proiecte

# copiaza sursa mea folosind git. Iti va crea automat un subfolder "lav"
git clone https://github.com/petrepopescu21/lav.git

# intra in acel subfolder
cd lav

# install dependencies
npm install

# serve with hot reload at localhost:8080
npm run dev

# Site-ul se va deschide automat in browser la adresa http://localhost:8080
# Orice modificare faci in cod, in urma salvarii, va genera un refresh automat

For detailed explanation on how things work, checkout the [guide](http://vuejs-templates.github.io/webpack/) and [docs for vue-loader](http://vuejs.github.io/vue-loader).
