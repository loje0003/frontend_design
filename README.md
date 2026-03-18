# Opgaveskabelon til "Figma til kode"

Se opgavebeskrivelsen på Fronter.

## Medfølgende Data

Der medfølger indholdsdata i form af lokale JSON-filer, som du kan bruge til din opgave. Det er ikke et krav til opgaven, men det kan gøre det nemmere og hurtigere at få tekst og billeder ind i dit projekt.

> [!NOTE]
> Bemærk, at CaseStudy-siden allerede inkluderer data fra en lokal JSON-fil.
> Bemærk også, at ikke alle billeder fra Figma-filen er i det lokale indholdsdata.

Dokumentationen til anvendelsen af dataene finder du på: [https://frontend-design-theme.netlify.app/](https://frontend-design-theme.netlify.app/).

Her er et eksempel på, hvordan du kan bruge dataene i dine Astro-komponenter:

```astro
import employees from "@data/employees.json";

console.log(employees);
```

## Brug af hjælpekomponenter

### DynamicImage.astro (`@helpers/DynamicImage.astro`)

Brug denne komponent til at vise billeder dynamisk fra lokale datafiler. Du skal blot sende stien fra datasættet direkte til komponenten.

Eksempel med data:

```astro
{employees.map((employee) => (
  <DynamicImage
    imagePath={employee.img}
    altText={employee.name}
    width={200}
    height={200}
  />
))}
```

### DynamicIcon.astro (`@helpers/DynamicIcon.astro`)

`DynamicIcon` bruges til at vise SVG-ikoner dynamisk baseret på et navn fra dine data.

Eksempel med data:

```astro
{employee.social_links.map((link) => (
  <DynamicIcon name={link.icon} />
))}
```

Her vises et ikon for hvert socialt medie, hvor `icon`-feltet matcher filnavnet på SVG-ikonet i `src/icons/`.

---

## Import af SVG-ikoner direkte

Du kan importere SVG-ikoner direkte i dine komponenter ved at importere dem:

```astro
import Checkmark from "@icons/checkmark.svg";

<Checkmark width={32} height={32} class="my-icon" />
```

Se evt. `src/pages/svgs.astro` for flere eksempler på direkte import og brug af SVG-ikoner.

/**\*\***\***\*\*** REFLEKSION \***\*\*\*\*\*\*\***/

I arbejdet med denne opgave har vi fået en bedre forståelse for opbygning af komponentbaserede løsninger i Astro, men vi har også oplevet flere udfordringer undervejs.

En af de største udfordringer har været brugen af container queries. Vi har haft svært ved at få dem til at fungere korrekt, især i forhold til hvornår og hvor de skulle anvendes. Det gjorde, at vi i flere tilfælde brugte unødvendig tid på at fejlfinde, før vi opnåede det ønskede responsive layout.
Det har givet os en bedre forståelse af, hvordan container queries adskiller sig fra media queries, og hvornår det er oplagt at bruge dem, selvom vi endnu ikke helt har mestret dem.

Derudover opdagede vi sent i processen, at der var en mere effektiv måde at håndtere typografi på. I stedet for at style fonts i hvert enkelt komponent, kunne vi have oprettet en fælles løsning, hvor font-styles blev defineret ét sted. Det ville have gjort vores kode mere konsistent og lettere at vedligeholde.

En anden læring har været arbejdet med grid og subgrid. Det var til tider udfordrende at få elementer til at flugte korrekt, men gennem iteration har vi fået en bedre forståelse for, hvordan layout kan styres mere præcist.
Afslutningsvis har opgaven givet os en bedre forståelse for samspillet mellem HTML, CSS og komponenter i Astro. Selvom vi har mødt udfordringer, har processen været lærerig, og vi står nu med en større forståelse for både struktur, styling og responsivt design.
