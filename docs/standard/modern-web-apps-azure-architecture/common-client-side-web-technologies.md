---
title: Běžné webové technologie na straně klienta
description: Navrhování moderních webových aplikací pomocí ASP.NET Core a Azure | Běžné webové technologie na straně klienta
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 36bb18d21740f406d33306c212195fa5dbb25ee1
ms.sourcegitcommit: 3500c4845f96a91a438a02ef2c6b4eef45a5e2af
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/07/2019
ms.locfileid: "55828329"
---
# <a name="common-client-side-web-technologies"></a>Běžné webové technologie na straně klienta

> "Webů by měla vypadat dobře zevnitř a out."  
> _- Paul Cookson_

Webové aplikace jsou aplikace ASP.NET Core a obvykle spoléhají na straně klienta webových technologiích jako HTML, CSS a JavaScriptu. Oddělením obsah stránka (HTML) od její rozložení a stylů (CSS) a její chování (prostřednictvím JavaScriptu) složité aplikace můžou využívat Princip oddělení obavy. Budoucí změny struktury, návrhu nebo chování aplikace můžete provést další snadno při tyto problémy nejsou vzájemně propojeny.

HTML a CSS jsou poměrně stabilní, JavaScript, prostřednictvím aplikační architektury a nástroje pro vývojáře pracovat s k vytváření webových aplikací, se vyvíjí breakneck rychlostí. Tato kapitola zjistí několik způsobů, jak vývojáři webů jako součást vývoje aplikací, protože poskytuje podrobný přehled Angular a React knihoven na straně klienta se používá jazyk JavaScript.

## <a name="html"></a>HTML

HTML (DHTML) je Standardní značkovací jazyk používaný k vytváření webových stránek a webových aplikací. Jeho prvky formuláře stavební kameny stránek, představující formátovaný text, obrázky, vstupy formuláře a jiné struktury. Pokud prohlížeč odešle požadavek na adresu URL, zda načítání stránky nebo aplikace, je nejprve thing, který je vrácený dokument HTML. Tento dokument HTML mohou odkazovat nebo obsahovat další informace o jeho vzhled a rozložení v podobě šablony stylů CSS nebo chování ve formě jazyka JavaScript.

## <a name="css"></a>CSS

CSS (Cascading šablony stylů) slouží k řízení vzhledu a rozložení prvků HTML. Styly CSS možné použít přímo na prvek jazyka HTML, definovat samostatně na stejné stránce nebo definované v samostatném souboru a odkazuje na stránku. Závislosti na tom, jak se používají pro daný element HTML select kaskádových stylů. Styl, mohou vztahovat na celý dokument, ale by být přepsána styl, který se aplikuje na konkrétního prvek. Podobně je specifické pro element styl by být přepsána styl aplikován na třídu šablony stylů CSS, která byla použita k elementu, který pak by být přepsán ve stylu cílení na konkrétní instanci daného prvku (prostřednictvím jejího id). Obrázek 6-1

**Obrázek 6-1.** Pravidla šablon stylů CSS specifičnosti v pořadí.

![](./media/image6-1.png)

Doporučujeme zachovat styly v souborech samostatné šablony stylů a použít na základě výběru CSS k implementaci stylů konzistentní vzhledem k aplikacím a opakovaně použitelné v rámci aplikace. Mělo by se vyhnout umístění pravidel stylu v kódu HTML a aplikování stylů na konkrétní jednotlivé elementy (nikoli celé třídy elementy nebo elementy, které jste využili zejména Třída CSS použitá jim) by měl být výjimky, ne pravidlo.

### <a name="css-preprocessors"></a>Preprocesory šablon stylů CSS

Šablony stylů CSS neobsahují podporu pro podmíněnou logiku, proměnných a dalších funkcí programovacích jazyků. Proto velké šablony stylů často obsahují velké množství opakování, jako stejné barvy, písma nebo jiné nastavení platí pro mnoho různých variant prvků jazyka HTML a CSS třídy. Šablony stylů CSS preprocesory může pomoct vaší šablony stylů, postupujte [zásada SUCHÝCH](https://deviq.com/don-t-repeat-yourself/) přidáním podpory pro proměnné a logiku.

Nejoblíbenějších šablon stylů CSS preprocesory jsou Sass a menší. Obě rozšíření šablon stylů CSS a jsou zpětně kompatibilní s ním, což znamená, že je prostý soubor CSS platný Sass nebo menší soubor. Sass využívá Ruby a méně, je založené na jazyce JavaScript a obě obvykle běží jako součást vašeho místního vývojového procesu. Obě mají příkazového řádku nástroje pro spuštění je k dispozici, jakož i integrované podpory v sadě Visual Studio pomocí úlohy Gulp ani Grunt.

## <a name="javascript"></a>JavaScript

JavaScript je dynamická, interpretovaný programovací jazyk, který byl standardizované ve specifikaci jazyka ECMAScript. Je programovací jazyk na webu. Jako šablony stylů CSS JavaScript může být definován jako atributů v rámci elementů HTML jako bloky skriptu v rámci stránky, nebo do samostatných souborů. Stejně jako šablony stylů CSS obecně doporučujeme uspořádat do samostatných souborů tak, JavaScript zajistit jejich oddělených co nejvíce z HTML na jednotlivé webové stránky nebo aplikace zobrazení.

Při práci s použitím jazyka JavaScript do webové aplikace, existuje několik úloh, které běžně budete muset provést:

- Výběr elementu HTML a načítání a/nebo aktualizuje jeho hodnotu.

- Dotazování webové rozhraní API pro data.

- Odesílání příkazu k webovému rozhraní API (a zpracování zpětného volání s jeho výsledek).

- Provedení ověření.

Můžete provést všechny tyto úlohy s použitím jazyka JavaScript samostatně, ale existuje mnoho knihoven pro usnadnění těchto úloh. Jedním z první a nejúspěšnější tyto knihovny je jQuery, která zůstává oblíbených volbou pro zjednodušení tyto úlohy na webových stránkách. Pro jednostránkové aplikace (SPA) jQuery neposkytuje mnoho požadované funkce, které nabízejí Angular a React.

### <a name="legacy-web-apps-with-jquery"></a>Starší verze webových aplikací v jazyce jQuery

Ačkoli staré standardy rozhraní JavaScript, jQuery i nadále se velmi často používaný knihovny pro práci s HTML/CSS a vytváření aplikací, které provádět volání AJAX pro webové rozhraní API. JQuery však funguje na úrovni prohlížeč modelu objektu dokumentu (DOM) a ve výchozím nastavení nabízí jenom imperativní, nikoli deklarativní, model.

Představte si například, že pokud do textového pole hodnota přesahuje 10, element na stránce nastavena jako viditelná. V jQuery to by obvykle provádí zápis obslužné rutiny události s kódem, který by zkontrolovat hodnoty textového pole a nastavit viditelnost elementu target podle této hodnoty. Toto je nezbytné, založený na kódu přístup. Jiné framework místo toho použít vázání dat deklarativně vazba viditelnost prvku na hodnotu textového pole. To nebude vyžadovat psaní kódu, ale místo toho pouze vyžaduje upravení související pomocí atributů vazby dat prvky. Růstem složitějšího chování na straně klienta datové vazby přistupuje často výsledkem jednodušší řešení s méně kódu a podmíněné složitost.

### <a name="jquery-vs-a-spa-framework"></a>vs jQuery SPA Framework

| **faktor** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| Abstrahuje modelu DOM | **Ano** | **Ano** |
| Podpora pro AJAX | **Ano** | **Ano** |
| Vazby deklarativní Data | **Ne** | **Ano** |
| MVC – vizuální styl směrování | **Ne** | **Ano** |
| Šablon | **Ne** | **Ano** |
| Deep-Link Routing | **Ne** | **Ano** |

Většina funkcí, které jQuery chybí vnitřně je možné přidat přidání dalších knihoven. Ale SPA architekturu jako třeba Angular nabízí tyto funkce integrálnější způsobem, protože je navržen s všechny v úvahu od začátku. JQuery je také velmi imperativní knihovny, což znamená, že je potřeba volat funkce jQuery, aby bylo možné provádět pomocí jQuery. Velká část práce a funkce, které poskytují rozhraní SPA lze provést pomocí deklarace, nevyžadují žádný skutečný kód má být proveden zápis.

Datová vazba je skvělé příklad tohoto objektu. V jQuery obvykle trvá jen jeden řádek kódu má být získána hodnota prvku modelu DOM, nebo nastavení hodnoty prvku. Ale budete muset tento kód napsat, kdykoli budete potřebovat ke změně hodnoty prvku a někdy k tomu dojde ve víc funkcí na stránce. Dalším běžným příkladem je viditelnost elementu. V jQuery může být mnoho různých místech, kde by psát kód pro ovládací prvek, zda byly některé prvky viditelné. Ve všech těchto případech se při použití datových vazeb žádný kód by bylo potřeba zapsat. By jednoduše vytvořit vazbu hodnotu nebo viditelnost na jeden či více elementů *viewmodel* na stránce a změny, které by viewmodel automaticky projeví v vázaných prvků.

### <a name="angular-spas"></a>Angular SPA

AngularJS rychle stal jeden z oblíbených architektur JavaScript na světě. Pomocí Angular 2 tým znovu framework od základů vytvořit nahoru (pomocí [TypeScript](https://www.typescriptlang.org/)) a přejmenované z AngularJS k jednoduše Angular. Aktuálně ve verzi 4 Angular nadále robustní architektura určená k vytváření jednostránkové aplikace.

Aplikace typu angular jsou sestaveny z komponenty. Součásti šablony ve formátu HTML v kombinaci s speciální objekty a řídit části stránky. Jednoduché komponenty z dokumentace pro Angular je znázorněna zde:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Součásti jsou definovány pomocí @Component dekoratéru funkce, která přijímá metadata o komponentě. Identifikuje vlastnost selektor id elementu na stránce, kde se zobrazí tato komponenta. Vlastnost šablony je jednoduchá Šablona HTML, který obsahuje zástupný symbol, který odpovídá vlastnosti název komponenty, které jsou definované na posledním řádku.

Při práci s prvky a šablony, namísto elementů modelu DOM aplikací Angular může pracovat na vyšší úrovni abstrakce a s menším množstvím kódu celkové než aplikace napsané v jazyce jenom JavaScript (také nazývané "vanilla JS") nebo s jQuery. Angular také ukládá některé pořadí na způsob uspořádání souborů skriptu na straně klienta. Podle konvence aplikací Angular pomocí modulu a komponenty soubory skriptu, které jsou umístěné v adresáři aplikace běžné strukturu složek. Angular skripty týkající se vytváření, nasazování a testování aplikace jsou obvykle umístěny v nadřazené složky.

Angular je také vynikající možnosti využití nástrojů rozhraní příkazového řádku (CLI). Začínáme s místně Angular vývoje (za předpokladu, že už máte, git a npm nainstalované) se skládá z jednoduše klonování úložiště z Githubu a spuštěna `npm install` a `npm start`. Kromě toho se dodává Angular vlastní nástroj rozhraní příkazového řádku, který můžete vytvářet projekty, přidat soubory a pomoci v oblastech testování, vytváření sady a nasazení úlohy. Toto rozhraní příkazového řádku nástroje friendliness díky Angular zejména kompatibilní s ASP.NET Core, která rovněž obsahuje skvělou podporu rozhraní příkazového řádku.

Společnost Microsoft vyvinula referenční aplikace [aplikaci eShopOnContainers](https://aka.ms/MicroservicesArchitecture), což zahrnuje implementace Angular jednostránková aplikace. Tato aplikace obsahuje Angular moduly ke správě nákupního košíku, načtení a zobrazení položky z katalogu online úložiště a zpracování vytvoření objednávky. Můžete zobrazit a stáhnout ukázkovou aplikaci z [Githubu](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

Na rozdíl od Angular, které nabízí úplnou implementaci vzor Model-View-Controller, React se týká pouze zobrazení. To není rozhraní .NET framework, právě knihovny, tak vytvářet SPA budete muset využít další knihovny.

Mezi nejdůležitější funkce reagují na je jeho použití virtuální modelu DOM. Virtuální modelu DOM React poskytuje několik výhod, včetně výkonu (virtuální modelu DOM můžete optimalizovat které části aplikace skutečný modelu DOM potřeba aktualizovat) a možnost testování (není nutné mít prohlížeče k testování React a jeho interakce s jeho virtuální modelu DOM).

React je také neobvyklé jak funguje s HTML. Místo generování striktní oddělení mezi kódem a značky (s odkazy na JavaScript možná uvedených v atributech HTML), React přidá jako JSX HTML přímo v rámci jeho kód jazyka JavaScript. JSX je HTML syntaxe, který může kompilovat do čistého jazyka JavaScript. Příklad:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Pokud už znáte jazyk JavaScript, by měl být snadno učení React. Není k dispozici téměř tolik Křivka osvojování nebo speciální syntaxe součástí jako Angular nebo další oblíbené knihovny.

Protože React není úplné rozhraní framework, je vhodné obvykle další knihovny pro zpracování věci, jako je směrování, webové volání rozhraní API a správy závislostí. Skvělé na tom je, můžete si vybrat nejlepší knihovny pro každou z nich, ale nevýhodou je, že je potřeba provést všechny tato rozhodnutí a ověřte, zda všechny vybrané knihovny fungují dobře spolupracovaly až to budete mít. Pokud chcete dobrým výchozím bodem, můžete použít průvodce jako Slingshot React, který hotových sadu kompatibilních knihoven na spolu s React.

### <a name="choosing-a-spa-framework"></a>Výběr rozhraní SPA

Když vzhledem k tomu, které rozhraní JavaScript je nejvhodnější pro podporu vašich jednostránková aplikace, mějte na paměti následující aspekty:

- Je váš tým vědět, jak rozhraní framework a jeho závislosti (včetně TypeScript v některých případech)?

- Jak sebevědomý je rozhraní a vyjadřujete svůj souhlas s jeho výchozí způsob plnění úkolů?

- (Nebo knihovnu doprovodná) zahrnuje všechny funkce, které vaše aplikace vyžaduje?

- Je dobře zdokumentovaná?

- Měří se její komunita? Jsou vytvářet nové projekty vytvořené s jeho pomocí?

- Měří se jeho základní týmu? Jsou problémy vyřešené a nové verze dodané pravidelně?

Architektury JavaScriptu dál rozvíjet breakneck rychlostí. Použijte požadavky uvedené výše pro zmírnění rizika, které vyberete, které budete později odmítnout, který je závislý na rozhraní. Pokud jste zejména riziko průmyslu, vezměte v úvahu rozhraní, které nabízí podporu obchodních a/nebo je vyvíjena ve velkých podnicích.

> ### <a name="references--client-web-technologies"></a>Odkazy – klientské webové technologie
> - **HTML a CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. MÉNĚ**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Používání stylů pro aplikace ASP.NET Core s menší, Sass a knihovnou aplikací Font Awesome**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Vývoj klientské strany v ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://facebook.github.io/react/>
> - **React Slingshot**  
> <https://github.com/coryhouse/react-slingshot>
> - **Vs react porovnání Angular 2**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **5 nejlepších architektury JavaScriptu 2017**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
>[Předchozí](common-web-application-architectures.md)
>[další](develop-asp-net-core-mvc-apps.md)