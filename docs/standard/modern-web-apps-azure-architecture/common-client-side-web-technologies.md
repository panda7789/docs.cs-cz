---
title: Běžné webové technologie straně klienta
description: Architektury moderních webových aplikací pomocí ASP.NET Core a Azure | Běžné webové technologie straně klienta
author: ardalis
ms.author: wiwagn
ms.date: 10/07/2017
ms.openlocfilehash: 96bafce9c81a3a0486b7b8930367cf47ec5cbcb8
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33592064"
---
# <a name="common-client-side-web-technologies"></a>Běžné webové technologie straně klienta

> "Webů by měla vypadat dobře zevnitř a out."  
> _-Paul Cookson_

## <a name="summary"></a>Souhrn

Aplikace ASP.NET Core jsou webové aplikace a obvykle spoléhají na straně klienta webové technologie, jako je HTML, CSS a JavaScript. Oddělením obsahu stránce (HTML) z jeho rozložení a stylů (CSS) a jeho chování (prostřednictvím JavaScript) můžete využít komplexní webové aplikace se zásadou oddělení otázky. Budoucí změny struktury, návrh nebo chování aplikace můžete provést další snadno při tyto otázky nejsou vzájemně propojeny.

Kód HTML a CSS jsou relativně ustájení, JavaScript, prostřednictvím architektury aplikace a nástroje pro vývojáře pracovat k sestavení webových aplikací, je vyvíjející se breakneck rychlostí. Tato kapitola zjistí několik způsobů, které vývojářům webů jako součást vývoje aplikací, které poskytuje podrobný přehled úhlová a reagují knihovny straně klienta používá JavaScript.

## <a name="html"></a>HTML

HTML (HyperText Markup Language) je standardní jazyk použitý k vytvoření webové stránky a webové aplikace. Jeho prvky představují stavební bloky stránek, představující formátovaný text, obrázky, formuláře vstupy a jiné struktury. Když prohlížeč odešle požadavek na adresu URL, zda načítání stránky nebo aplikace, je nejprve thing tedy vrácený dokument HTML. Tento dokument HTML mohou odkazovat nebo obsahují další informace o jeho vzhled a rozložení ve formě šablon stylů CSS nebo chování ve formátu JavaScript.

## <a name="css"></a>CSS

CSS (Cascading šablony stylů) se používá k řízení vzhledu a rozložení elementů HTML. Styly CSS můžete být použitých přímo na HTML element, na stejné stránce je definován samostatně nebo definované v samostatném souboru a odkazuje na stránku. Podle toho, jak se použije k výběru daného elementu HTML kaskádových stylů. Například styl mohou vztahovat na celý dokument, ale bude možné přepsat styl, který pro konkrétní prvek použít. Podobně je možné styl specifické pro element by možné přepsat styl, který použije pro třídu CSS, které bylo použito pro element, který pak bude možné přepsat styl cílení na konkrétní instanci tohoto prvku (přes jeho id). Obrázek 6-1

**Obrázek 6-1.** Pravidla šablon stylů CSS specifické podobě, v pořadí.

![](./media/image6-1.png)

Je nejvhodnější styly Mějte své vlastní soubory samostatné šablony stylů a použít na základě výběru kaskádových k implementaci konzistentní a opakovaně použitelné styly v aplikaci. Umístění pravidel stylů v kódu HTML, by se mělo zabránit a použití stylů na konkrétní jednotlivé elementy (nikoli celý třídy elementy nebo prvky, které má určitou třídu CSS na ně použity) by měla být výjimka, není toto pravidlo.

### <a name="css-preprocessors"></a>Preprocesorů šablon stylů CSS

Šablony stylů CSS neobsahují podporu pro podmíněnou logiku, proměnné a další funkce programovací jazyk. Proto velké předlohy se styly často zahrnují spoustu opakování, jako stejné barvy, písma nebo ostatní nastavení se použije pro mnoho různých variant elementů HTML a tříd CSS. Preprocesorů šablon stylů CSS může pomoci vaše šablony stylů, postupujte podle [SUCHÝCH Princip](http://deviq.com/don-t-repeat-yourself/) přidáním podpory pro proměnné a logiku.

Nejoblíbenější preprocesorů šablon stylů CSS jsou Sass a menší. Obě rozšířit šablon stylů CSS a je zpětně kompatibilní s, což znamená, že je prostý soubor CSS platný Sass nebo menší soubor. Sass je založen na Ruby a menší je založené na jazyce JavaScript a obě obvykle běží jako součást procesu místní vývoj. Mají obě příkazového řádku nástroje pro spuštění je k dispozici, jakož i integrované podpory v sadě Visual Studio pomocí Gulp nebo Grunt úloh.

## <a name="javascript"></a>JavaScript

JavaScript je dynamická interpretovaný programovací jazyk, který standardizované v specifikace jazyka ECMAScript. Je programovací jazyk webu. Jako šablon stylů CSS může být definováno jako atributy v rámci prvků HTML, JavaScript jako bloky skriptu v rámci jedné nebo v samostatné soubory. Stejně jako šablon stylů CSS se obecně doporučuje uspořádání JavaScript do samostatné soubory udržuje ho oddělené co nejvíce z HTML na jednotlivé webové stránky nebo aplikace zobrazení nalezen.

Při práci s JavaScript ve webové aplikaci, existuje několik úloh, které běžně budete muset provést:

-   Výběr HTML element a načítání a aktualizuje jeho hodnota

-   Dotazování webového rozhraní API pro data

-   Odesílání příkaz do webového rozhraní API (a reagovat na zpětné volání s jeho výsledek)

-   Provedení ověření

Můžete provést všechny tyto úlohy v jazyce JavaScript samostatně, ale existuje mnoho knihovny usnadnění tyto úlohy. Jedním z první a těch nejúspěšnějších těchto knihoven je jQuery, který je stále oblíbených volba pro zjednodušenou tyto úlohy na webových stránkách. Pro jednostránkové aplikace (SPA) jQuery neposkytuje požadované funkce, které úhlová a reagují nabízí řadu.

### <a name="legacy-web-apps-with-jquery"></a>Starší verze webové aplikace s jQuery

I když staré standardy JavaScript framework, jQuery nadále knihovnu velmi běžně používané pro práci s HTML/šablon stylů CSS a vytváření aplikací, které volání AJAX na webových rozhraní API. JQuery však funguje na úrovni modelu objektu dokumentu (DOM) prohlížeče a ve výchozím nastavení nabízí pouze imperativní, nikoli deklarativní, model.

Představte si například, pokud do textového pole hodnota přesahuje 10, element na stránce by měla být dostupná. V jQuery to se obvykle provádí zápis obslužné rutiny události s kódem, který by zkontrolujte hodnotu textového pole a nastavit viditelnost cílový element na základě této hodnoty. Toto je nutné, založené na kódu přístup. Jiné framework může místo toho použít datovou vazbu deklarativně svázat viditelnost elementu na hodnotu textové pole. Nebude vyžadovat psaní kódu, ale místo toho pouze vyžaduje architekturu související s atributy vazby dat prvky. Jelikož chování straně klientů složitější, datová vazba blíží často výsledek v jednodušší řešení s méně kódu a podmíněného složitost.

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs SPA Framework

| **Koeficient** | **jQuery** | **úhlová**|
|--------------------------|------------|-------------|
| Abstrahuje modelu DOM | **Ano** | **Ano** |
| Podpora jazyka AJAX | **Ano** | **Ano** |
| Deklarativní datová vazba | **Ne** | **Ano** |
| Směrování MVC – styl | **Ne** | **Ano** |
| Ukázka | **Ne** | **Ano** |
| Přímý odkaz směrování | **Ne** | **Ano** |

Většinu funkcí, které jQuery chybí vnitřně lze přidat při přidání dalších knihoven. Rozhraní SPA jako úhlová však poskytuje tyto funkce integrace způsobem, protože je navržen ke všem z nich pamatovat od začátku. JQuery je také velmi imperativní knihovny, což znamená, že je potřeba volat funkce jQuery, aby bylo možné provádět žádné kroky s jQuery. Většinu práce a funkce, které poskytují rozhraní SPA lze provést deklarativně, nevyžadují žádný skutečný kód k zapsání.

Datová vazba je skvělým příklad tohoto objektu. V jQuery obvykle trvá jen jeden řádek kódu má být získána hodnota elementu DOM, nebo nastavte hodnotu elementu. Máte ale tento kód napsat kdykoli potřebujete změnit hodnotu elementu a v některých případech to budou provedeny v víc funkcí na stránce. Jiné častým příkladem je viditelnost elementu. V jQuery může být mnoho různých místech, kde by napíšete kód na ovládací prvek zda byly některé prvky viditelné. V každé z těchto případech při použití datových vazeb žádný kód potřebovat k zapsání. By jednoduše vazby hodnotu nebo viditelnost na elementy *viewmodel* na stránce a změny, které by viewmodel automaticky projeví v vázané elementy.

### <a name="angular-spas"></a>Úhlová SPA

AngularJS rychle se stala jedna nejoblíbenější rozhraní JavaScript na světě. Úhlová 2 týmem přetvořit framework od základů nahoru (pomocí [TypeScript](https://www.typescriptlang.org/)) a z AngularJS přejmenované na jednoduše úhlová. Aktuálně na verze 4 úhlová nadále robustní architektura pro vytváření jednostránkové aplikace.

Úhlová aplikace jsou vytvářeny z komponent. Součásti kombinovat šablony HTML s speciální objekty a řídit část stránky. Zobrazí se zde jednoduché komponenty z dokumentace úhlová na:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Součásti jsou definovány pomocí @Component funkce dekoratéra, který přebírá metadata o komponentu. Vlastnost selektor identifikuje id elementu na stránce, kde se zobrazí tuto součást. Vlastnosti šablony je jednoduchý šablonu HTML, která obsahuje zástupný symbol, který odpovídá vlastnosti název součásti, které jsou definované na posledním řádku.

Ve spolupráci s součásti a šablony, místo elementů modelu DOM může úhlová aplikace fungovat na vyšší úrovni abstrakce a méně celkové kódu než aplikací napsaných pomocí právě JavaScript (také nazývané "vanilla JS") nebo s jQuery. Úhlová také ukládá některé pořadí na jak uspořádání souborů klientský skript. Podle konvence úhlová aplikace použít běžné struktura složek, se modul a součást souborů skriptů, které jsou umístěné v adresáři aplikace. Úhlová skripty nevadí, vytváření, nasazení a testování aplikace jsou obvykle umístěné v nadřazené složky.

Úhlová také využívá skvělé nástrojů rozhraní příkazového řádku (CLI). Začínáme s místně úhlová vývoj (za předpokladu, že již máte git a npm nainstalovaná) se skládá jednoduše klonování úložiště z Githubu a spuštění \`npm nainstalujte\` a \`npm počáteční\`. Kromě toho se dodává úhlová svůj vlastní nástroj příkazového řádku, který můžete vytvářet projekty, přidat soubory a pomůže při testování, sdružování a nasazení úlohy. Toto rozhraní příkazového řádku tooling friendliness díky úhlová zejména kompatibilní s ASP.NET Core, který také funkce podpory rozhraní příkazového řádku.

Společnost Microsoft vyvinula referenční aplikace [eShopOnContainers](http://aka.ms/MicroservicesArchitecture), což zahrnuje implementace úhlová SPA. Tato aplikace obsahuje úhlová modulů ke správě online obchod nákupního košíku, zatížení a zobrazení položek ze svého katalogu a vytvoření pořadí zpracování. Můžete zobrazit a stáhnout ukázkovou aplikaci z [Githubu](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>Reagovat

Na rozdíl od úhlová, který nabízí úplnou implementaci vzor Model-View-Controller, reagují se týká pouze zobrazení. Není rozhraní, právě knihovnu, takže k sestavení SPA budete muset využít další knihovny.

Jedním z nejdůležitějších funkcích reagují na je jeho použití virtuální modelu DOM. Virtuální DOM reagují poskytuje několik výhod, včetně výkonu (virtuální DOM může optimalizovat které části skutečné DOM potřeba aktualizovat) a testovatelnosti (není nutné mít v prohlížeči na testování reagují a jeho interakce s jeho virtuální DOM).

Reagují je také neobvyklou v tom, jak funguje s jazykem HTML. Místo striktní oddělení mezi kód a značky (s odkazy na JavaScript zobrazovaných v atributech HTML možná), reagovat přidá jako JSX HTML přímo v rámci jeho kód jazyka JavaScript. JSX je syntaxe stylu HTML, které můžete zkompilovat dolů čistý JavaScript. Příklad:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Pokud už znáte jazyk JavaScript, učení reagují by měla být snadná. Není k dispozici téměř tolik křivku nebo speciální syntaxi jako spojené s úhlová nebo jiné Oblíbené knihovny.

Protože reagují není úplná framework, budete muset obvykle jiné knihovny pro zpracování třeba směrování, webový volání rozhraní API a správě závislosti. Skvělé na tom je, můžete si vybrat nejlepší knihovny pro každou z nich, ale nevýhodou je, že budete muset provést všechny tyto rozhodnutí a ověřte, zda všechny vybrané knihovnách dobře fungují po dokončení. Pokud chcete, aby to dobrý výchozí bod, můžete Startovní sady jako Slingshot reagovat, který hotová sadu kompatibilní knihovny společně s reagují.

### <a name="choosing-a-spa-framework"></a>Výběr SPA Framework

Při zvažování které architekturu JavaScript jsou nejvhodnější pro podporu vašeho SPA, mějte na paměti následující aspekty:

-   Je váš tým obeznámeni s rozhraní a jeho závislosti (včetně TypeScript v některých případech)?

-   Jak zaujatých je rozhraní, a souhlasíte s jeho výchozí způsob plnění úkolů?

-   Ho (nebo knihovnu doprovodné) zahrnuje všechny funkce, které vaše aplikace vyžaduje?

-   Je dobře zdokumentovaných?

-   Jak active je jeho komunita? Jsou nové projekty vytváření integrované s ní?

-   Jak active je jeho základní tým? Jsou problémy se vyřešený a novějšími verzemi sice pravidelně?

Rozhraní JavaScript pokračovat ve vývoji s breakneck rychlost. Použijte informace uvedené výše pro zmírnění rizik výběru rozhraní, které budete později odmítnout, který je závislý na. Pokud jste zvlášť riziko-projeví, nepříznivé, vezměte v úvahu rozhraní, které nabízí podporu komerční nebo je vyvíjen velký podnik.

> ### <a name="references--client-web-technologies"></a>Odkazy – klienta webové technologie
> - **Kód HTML a CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. MENŠÍ**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Práce se styly aplikace ASP.NET Core s méně, Sass a úžasné písma**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Vývoj pro klientské v ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **úhlová**  
> <https://angular.io/>
> - **Reagovat**  
> <https://facebook.github.io/react/>
> - **Reagovat Slingshot**  
> <https://github.com/coryhouse/react-slingshot>
> - **Reagovat vs úhlová porovnání 2**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **5 nejlepší rozhraní JavaScript 2017**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
[Předchozí] (common-web-application-architectures.md) [Další] (develop-asp-net-core-mvc-apps.md)
