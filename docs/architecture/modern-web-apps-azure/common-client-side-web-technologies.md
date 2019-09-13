---
title: Běžné webové technologie na straně klienta
description: Architekt moderních webových aplikací pomocí ASP.NET Core a Azure | Běžné webové technologie na straně klienta
author: ardalis
ms.author: wiwagn
ms.date: 01/30/2019
ms.openlocfilehash: 4dd747293fba4c18c2d10738d36f4d98cfd3f5b9
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70926504"
---
# <a name="common-client-side-web-technologies"></a>Běžné webové technologie na straně klienta

> "Weby by měly vypadat dobře zevnitř a ven."  
> _- Paul Cookson_

Aplikace ASP.NET Core jsou webové aplikace a obvykle spoléhají na webové technologie klienta, jako je HTML, CSS a JavaScript. Díky oddělení obsahu stránky (HTML) od jejího rozložení a stylů (CSS) a jeho chování (prostřednictvím JavaScriptu) můžou komplexní webové aplikace využít oddělení zásad, které se týkají. Budoucí změny struktury, návrhu nebo chování aplikace je možné snadněji, pokud tyto otázky nejsou provázány.

I když jsou HTML a CSS relativně stabilní, JavaScript, pomocí aplikačních architektur a vývojářů nástrojů pracujících s nástrojem k vytváření webových aplikací se vyvíjí při Breakneck rychlosti. Tato kapitola si vyhledá několik způsobů, jak je jazyk JavaScript používán webovými vývojáři jako součást vývoje aplikací, jak poskytuje podrobný přehled o úhlových a reagujících knihovnách na straně klienta.

## <a name="html"></a>HTML

HTML (HyperText Markup Language) je standardní značkovací jazyk používaný k vytváření webových stránek a webových aplikací. Jeho prvky tvoří stavební kameny stránek, které představují formátovaný text, obrázky, vstupy formulářů a další struktury. Když prohlížeč odešle požadavek na adresu URL, ať už načte stránku nebo aplikaci, první věc, kterou vrátí, je dokument HTML. Tento dokument HTML může odkazovat nebo obsahovat další informace o jeho vzhledu a rozložení ve formě šablony stylů CSS nebo chování ve formě JavaScriptu.

## <a name="css"></a>CSS

CSS (šablony stylů CSS) slouží k řízení vzhledu a rozložení prvků jazyka HTML. Styly CSS lze použít přímo na prvek jazyka HTML, který je definován samostatně na stejné stránce nebo definovaný v samostatném souboru a na který je odkazováno stránkou. Styly jsou kaskádovitě na základě toho, jak jsou použity pro výběr daného prvku jazyka HTML. Styl se například může vztahovat na celý dokument, ale by se přepsal stylem, který se aplikuje na konkrétní element. Podobně styl specifický pro element by byl potlačen stylem, který se použil pro třídu šablony stylů CSS, která byla použita na element, který by měl být přepsán stylem, který cílí na konkrétní instanci tohoto prvku (prostřednictvím jeho ID). Obrázek 6-1

![Pravidla pro specifickou šablonu stylů CSS](./media/image6-1.png)

**Obrázek 6-1.** Pravidla pro specifickou šablonu stylů CSS v pořadí.

Doporučuje se, abyste zachovali styly ve vlastních samostatných souborech se šablonami stylů a používali kaskádové styly pro implementaci konzistentních a opakovaně použitelných stylů v rámci aplikace. Umístění pravidel stylu v rámci kódu HTML by se mělo vyhnout, a použití stylů pro konkrétní jednotlivé prvky (spíše než celé třídy prvků nebo prvků, které mají pro ně použity konkrétní třídy CSS) by měla být výjimka, nikoli pravidlo.

### <a name="css-preprocessors"></a>Preprocesory CSS

Šablony stylů CSS nemají podporu pro podmíněnou logiku, proměnné a další funkce programovacího jazyka. Proto velké šablony stylů často obsahují mnoho opakování, protože stejná barva, písmo nebo jiné nastavení se aplikují na mnoho různých variací prvků HTML a tříd CSS. Předprocesory šablon stylů CSS mohou vašim šablonám pokrývat základní [Princip](https://deviq.com/don-t-repeat-yourself/) přidáním podpory proměnných a logiky.

Nejoblíbenější preprocesory CSS jsou Sass a méně. Rozšiřuje šablony stylů CSS a jsou zpětně kompatibilní, což znamená, že prostý soubor CSS je platný soubor Sass nebo LESS. Sass je založen na Ruby a méně je založen na jazyce JavaScript a obě se obvykle spouštějí jako součást místního procesu vývoje. K dispozici jsou nástroje příkazového řádku i integrovaná podpora v aplikaci Visual Studio pro jejich spouštění pomocí úloh Gulp nebo grunt.

## <a name="javascript"></a>JavaScript

JavaScript je dynamický a interpretovaný programovací jazyk, který byl standardizován ve specifikaci jazyka ECMAScript. Je programovací jazyk webu. Podobně jako CSS může být JavaScript definován jako atributy v rámci prvků HTML, jako bloky skriptu na stránce nebo v samostatných souborech. Stejně jako v případě šablon stylů CSS je obecně doporučováno uspořádat JavaScript do samostatných souborů a uchovávat tak co nejvíce z HTML nalezeného na jednotlivých webových stránkách nebo zobrazeních aplikací.

Při práci s JavaScriptem ve webové aplikaci je k dispozici několik úloh, které je obvykle potřeba provést:

- Výběr prvku jazyka HTML a načtení nebo aktualizace jeho hodnoty.

- Dotazování webového rozhraní API na data.

- Odeslání příkazu webovému rozhraní API (a reakce na zpětné volání s jeho výsledkem).

- Ověřování probíhá.

Všechny tyto úlohy můžete provádět pouze pomocí JavaScriptu, ale existuje mnoho knihoven, aby byly tyto úlohy jednodušší. Jedna z prvních a nejpravděpodobnějších těchto knihoven je jQuery, která je nadále oblíbená volbou pro zjednodušení těchto úloh na webových stránkách. V případě aplikací s jednou stránkou (jednostránkové) jQuery neposkytuje mnoho z požadovaných funkcí, které nabízí a reaguje.

### <a name="legacy-web-apps-with-jquery"></a>Starší verze Web Apps s jQuery

I když Ancient podle standardů rozhraní JavaScript Framework, jQuery bude i nadále používána jako velmi běžně používaná knihovna pro práci s HTML/CSS a sestavování aplikací, které vytvářejí volání rozhraní API pro Web API. JQuery ale funguje na úrovni modelu DOM (Document Object Model) prohlížeče a ve výchozím nastavení nabízí pouze imperativní, spíše než deklarativní model.

Představte si například, že pokud hodnota v textovém poli přesáhne 10, element na stránce by měl být viditelný. V jQuery by to bylo obvykle implementováno zápisem obslužné rutiny události pomocí kódu, který by zkontroloval hodnotu TextBox a nastavil viditelnost cílového prvku na základě této hodnoty. Toto je nepodmíněný přístup založený na kódu. Jiné rozhraní může místo toho použít datovou vazbu pro svázání viditelnosti prvku s hodnotou textového pole deklarativně. To by nevyžadovalo zápis kódu, ale místo toho vyžaduje pouze upravení prvků, které jsou součástí atributů vazby dat. Vzhledem k tomu, že chování na straně klienta přirůstá složitější, přístupy k vazbám mezi daty často vedou k jednodušším řešením s menším množstvím kódu a

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs – architektura SPA

| **Jednotek** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| Vyabstrakce DOM. | **Ano** | **Ano** |
| Podpora AJAX | **Ano** | **Ano** |
| Deklarativní datová vazba | **Ne** | **Ano** |
| Směrování ve stylu MVC | **Ne** | **Ano** |
| Šablonování | **Ne** | **Ano** |
| Směrování s přímým odkazem | **Ne** | **Ano** |

Většina funkcí jQuery, které chybí, je možné přidat s přidáním dalších knihoven. Architektura SPA, jako je úhlová, ale poskytuje tyto funkce lépe integrovaným způsobem, protože je navržená se všemi z nich na začátku. JQuery je také velmi imperativní knihovna, což znamená, že je třeba volat funkce jQuery, aby cokoli s jQuery bylo možné dělat. Většina práce a funkcí, které poskytují architektury SPA, se dají provádět deklarativně, takže není potřeba zapisovat žádný skutečný kód.

Vazba dat je skvělým příkladem. V jQuery obvykle pouze jeden řádek kódu pro získání hodnoty prvku modelu DOM nebo pro nastavení hodnoty elementu. Tento kód však musíte napsat kdykoli, když potřebujete změnit hodnotu prvku a někdy k tomu dojde ve více funkcích na stránce. Dalším běžným příkladem je viditelnost prvku. V jQuery může existovat mnoho různých míst, kde byste měli napsat kód pro řízení, zda byly určité prvky viditelné. V každém z těchto případů platí, že při použití datové vazby není nutné zapisovat kód. Stačí vytvořit vazbu hodnoty nebo viditelnosti prvků v dotazu na *ViewModel* na stránce a změny tohoto ViewModel by se automaticky projevily ve vázaných prvcích.

### <a name="angular-spas"></a>Úhlová Jednostránkovéa

AngularJS se rychle stala jedním z nejoblíbenějších rozhraní JavaScript v celém světě. S úhlovými 2 tým znovu sestavil rozhraní od základu (pomocí [TypeScript](https://www.typescriptlang.org/)) a předává je do jednoduchého úhlu. V současné době verze 4 má úhlová architektura i pro vytváření aplikací s jednou stránkou.

Úhlové aplikace jsou sestavené z komponent. Komponenty kombinují šablony HTML se speciálními objekty a ovládají část stránky. V tomto příkladu se zobrazuje jednoduchá součást z úhlů:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Komponenty jsou definovány pomocí @Component funkce dekoratér, která přebírá metadata o komponentě. Vlastnost Selector Určuje ID prvku na stránce, kde se tato součást zobrazí. Vlastnost Template je jednoduchá šablona HTML, která obsahuje zástupný text, který odpovídá vlastnosti názvu komponenty definované na posledním řádku.

Díky práci s komponentami a šablonami namísto elementů modelu DOM mohou úhlové aplikace pracovat na vyšší úrovni abstrakce a s menším celkovým kódem než aplikace napsané pomocí JavaScriptu (označované také jako "Vanilla JS") nebo pomocí jQuery. Úhlová také některá pořadí uspořádání souborů skriptu na straně klienta. V rámci konvence používají úhlové aplikace společnou strukturu složek se soubory skriptu modulu a komponenty umístěnými ve složce aplikace. Mezi zabývající se skripty se sestavou, nasazením a testováním aplikace obvykle nachází ve složce vyšší úrovně.

Úhlová i vhodná použití nástrojů rozhraní příkazového řádku (CLI). Začínáme s úhlovým vývojem v místním prostředí (za předpokladu, že už máte nainstalované Git a npm), obsahuje jednoduše klonování `npm install` úložiště `npm start`z GitHubu a spuštění a. Kromě toho úhlové dodává svůj vlastní nástroj CLI, který může vytvářet projekty, přidávat soubory a pomáhat s úlohami testování, sdružování a nasazení. Tento nástroj rozhraní příkazového řádku (přívětivost) pro rozhraní příkazového řádku vydává hlavně obzvláště kompatibilní s ASP.NET Core, což také přináší skvělé podpoře CLI

Společnost Microsoft vyvinula referenční aplikaci [eShopOnContainers](https://aka.ms/MicroservicesArchitecture), která zahrnuje úhlovou implementaci. Tato aplikace zahrnuje úhlové moduly pro správu nákupních košíků online obchodů, načítání a zobrazování položek ze svého katalogu a vytváření objednávek při zpracování. Ukázkovou aplikaci můžete zobrazit a stáhnout z [GitHubu](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

Na rozdíl od úhlů, který nabízí úplnou implementaci vzoru pro zobrazení modelu, reaguje pouze na zobrazení. Nejedná se o architekturu, pouze o knihovnu, takže pro vytvoření zabezpečeného hesla budete muset využít další knihovny.

Jednou z nejdůležitějších funkcí, které reagují, je použití virtuálního modelu DOM. Virtuální DOM umožňuje reagovat s několika výhodami, včetně výkonu (virtuální DOM může optimalizovat, které části skutečného modelu DOM se musí aktualizovat) a testovat (není nutné mít v prohlížeči možnost testovat reakce a jeho interakce s virtuálním objektem DOM).

Reakce je také neobvyklá v tom, jak funguje s HTML. Místo toho, abyste museli mít striktní oddělení mezi kódem a označením (s odkazy na JavaScript, které se zobrazují v atributech HTML, případně), reaguje přidat HTML přímo do svého kódu JavaScriptu jako JSX. JSX je syntaxe podobná HTML, která se může kompilovat do čistě JavaScriptu. Příklad:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Pokud už znáte JavaScript, měli byste snadno reagovat na učení. K dispozici není skoro tolik výukové křivky nebo speciální syntaxe, která se týká úhlů nebo jiných oblíbených knihoven.

Vzhledem k tomu, že reakce není úplným rozhraním, obvykle budete chtít, aby jiné knihovny zpracovaly věci jako směrování, volání webového rozhraní API a správu závislostí. Dobrým aspektem je, že si můžete vybrat nejlepší knihovnu pro každou z těchto věcí, ale nevýhodou je, že je potřeba provést všechna tato rozhodnutí a ověřit, jestli všechny zvolené knihovny fungují dobře společně, až budete hotovi. Pokud chcete dobrý výchozí bod, můžete použít Startovní sadu, jako je reakce Slingshot, která předvede sadu kompatibilních knihoven společně s reagují.

### <a name="choosing-a-spa-framework"></a>Výběr architektury SPA

Při zvažování, které rozhraní JavaScript Framework bude fungovat nejlépe pro podporu vašeho SPA, pamatujte na následující skutečnosti:

- Je váš tým obeznámen s architekturou a jejími závislostmi (včetně TypeScriptu v některých případech)?

- Jak dogmatickým je rozhraní a souhlasíte s jeho výchozím způsobem?

- Zahrnuje to (nebo doprovodná knihovna) všechny funkce, které vaše aplikace vyžaduje?

- Je dobře dokumentováná?

- Jak aktivní je jeho komunita? Jsou vytvořeny nové projekty, které s ní sestavují?

- Jak aktivní je hlavní tým? Jsou vyřešené problémy a pravidelně se odesílají nové verze?

Rozhraní JavaScript Framework se nadále vyvíjí s Breakneck rychlostí. Pomocí výše uvedených doporučení můžete zmírnit riziko výběru rozhraní, na které budete později spoléhat. Pokud máte obzvláště rizikové – Averse, vezměte v úvahu rozhraní, které nabízí komerční podporu a/nebo je vyvíjeno velkým podnikem.

> ### <a name="references--client-web-technologies"></a>Odkazy – klientské webové technologie
>
> - **HTML a CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs. TOLIK**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Stylování ASP.NET Core aplikací s využitím méně, Sass a písma Super**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Vývoj na straně klienta v ASP.NET Core**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://facebook.github.io/react/>
> - **Reakce Slingshot**  
> <https://github.com/coryhouse/react-slingshot>
> - **Reakce vs. 2 porovnání**  
> <https://www.codementor.io/codementorteam/react-vs-angular-2-comparison-beginners-guide-lvz5710ha>
> - **5 nejlepších platforem JavaScript 2017**  
> <https://hackernoon.com/5-best-javascript-frameworks-in-2017-7a63b3870282>

>[!div class="step-by-step"]
>[Předchozí](common-web-application-architectures.md)Další
>[](develop-asp-net-core-mvc-apps.md)
