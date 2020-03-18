---
title: Běžné webové technologie na straně klienta
description: Architekt moderní webové aplikace s ASP.NET core a Azure | Běžné webové technologie na straně klienta
author: ardalis
ms.author: wiwagn
ms.date: 12/04/2019
ms.openlocfilehash: 2809c8539b42e8e2250039dceed1389b3cbdcd8a
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "77449371"
---
# <a name="common-client-side-web-technologies"></a>Běžné webové technologie na straně klienta

> "Webové stránky by měly vypadat dobře zevnitř i zvenku."  
> _- Paul Cookson_

ASP.NET základní aplikace jsou webové aplikace a obvykle se spoléhají na webové technologie na straně klienta, jako je HTML, CSS a JavaScript. Oddělením obsahu stránky (HTML) od jejího rozložení a stylu (CSS) a jejího chování (pomocí JavaScriptu) mohou složité webové aplikace využít princip oddělení zájmů. Budoucí změny struktury, návrhu nebo chování aplikace lze provést snadněji, pokud tyto obavy nejsou vzájemně propojeny.

Zatímco HTML a CSS jsou relativně stabilní, JavaScript, pomocí aplikačních rámců a utilit vývojáři pracují s stavět webové aplikace, se vyvíjí závratnou rychlostí. Tato kapitola se zabývá několika způsoby, kterými používají weboví vývojáři JavaScript, a poskytuje přehled na vysoké úrovni o knihovnách na straně klienta Angular a React.

> [!NOTE]
> Blazor poskytuje alternativu k JavaScriptovým rámcům pro vytváření bohatých, interaktivních klientských uživatelských rozhraní. Podpora Blazor na straně klienta je stále ve verzi preview, takže prozatím je mimo rozsah pro tuto kapitolu.

## <a name="html"></a>HTML

HTML je standardní značkovací jazyk používaný k vytváření webových stránek a webových aplikací. Jeho prvky tvoří stavební kameny stránek, které představují formátovaný text, obrázky, vstupy formulářů a další struktury. Když prohlížeč provede požadavek na adresu URL, ať už načte stránku nebo aplikaci, první věc, která je vrácena, je dokument HTML. Tento dokument HTML může odkazovat nebo obsahovat další informace o jeho vzhledu a rozložení ve formě CSS nebo chování ve formě JavaScriptu.

## <a name="css"></a>CSS

CSS (Kaskádové šablony stylů) se používá k ovládání vzhledu a rozložení prvků HTML. Styly CSS lze aplikovat přímo na element HTML, definovaný samostatně na stejné stránce nebo definované v samostatném souboru a odkazované stránkou. Styly kaskády na základě toho, jak se používají k výběru daného prvku HTML. Styl může být například aplikován na celý dokument, ale bude přepsán stylem, který se použije na určitý prvek. Podobně styl specifický pro prvek by byl přepsán stylem, který byl použit na třídu CSS, která byla použita na prvek, který by byl přepsán stylem zaměřeným na konkrétní instanci tohoto prvku (prostřednictvím jeho ID). Obrázek 6-1

![Pravidla specifičnosti CSS](./media/image6-1.png)

**Obrázek 6-1.** PRAVIDLA SPECIFIČNOSTI CSS, v pořádku.

Nejlepší je zachovat styly ve vlastních samostatných souborech stylů a použít kaskádové soubory založené na výběru k implementaci konzistentních a opakovaně použitelných stylů v aplikaci. Je třeba se vyhnout umístění pravidel stylu v rámci html a použití stylů na určité jednotlivé prvky (spíše než celé třídy prvků nebo prvků, u kterých byla použita určitá třída CSS) by mělo být výjimkou, nikoli pravidlem.

### <a name="css-preprocessors"></a>Preprocesory CSS

Šablony stylů CSS postrádají podporu pro podmíněnou logiku, proměnné a další funkce programovacího jazyka. Velké styly tedy často obsahují poměrně dost opakování, protože stejné nastavení barvy, písma nebo jiné nastavení je použito pro mnoho různých variant prvků HTML a tříd CSS. Css preprocesory mohou pomoci vaše styly sledovat [princip DRY](https://deviq.com/don-t-repeat-yourself/) přidáním podpory pro proměnné a logiku.

Nejoblíbenější CSS preprocesory jsou Sass a LESS. Oba rozšířit CSS a jsou zpětně kompatibilní s ním, což znamená, že prostý soubor CSS je platný soubor Sass nebo LESS. Sass je založen na Ruby a LESS je založen na JavaScriptu a oba jsou obvykle spuštěny jako součást vašeho procesu místního vývoje. Oba mají k dispozici nástroje příkazového řádku, stejně jako integrovanou podporu v sadě Visual Studio pro jejich spuštění pomocí úloh Gulp nebo Grunt.

## <a name="javascript"></a>JavaScript

JavaScript je dynamický, interpretovaný programovací jazyk, který byl standardizován ve specifikaci jazyka ECMAScript. Je to programovací jazyk webu. Podobně jako CSS lze JavaScript definovat jako atributy v rámci elementů HTML, jako bloky skriptu na stránce nebo v samostatných souborech. Stejně jako CSS, je doporučeno uspořádat JavaScript do samostatných souborů, udržet ji odděleny co nejvíce od HTML nalézt na jednotlivých webových stránkách nebo zobrazení aplikace.

Při práci s JavaScriptem ve webové aplikaci je obvykle potřeba provést několik úloh:

- Výběr prvku HTML a načítání a/nebo aktualizace jeho hodnoty.

- Dotazování webového rozhraní API na data.

- Odeslání příkazu do webového rozhraní API (a reakce na zpětné volání s jeho výsledkem).

- Provádění ověření.

Všechny tyto úlohy můžete provádět pouze pomocí javascriptu, ale existuje mnoho knihoven, které tyto úkoly usnadňují. Jedním z prvních a nejúspěšnějších z těchto knihoven je jQuery, který je i nadále oblíbenou volbou pro zjednodušení těchto úkolů na webových stránkách. Pro jednostránkové aplikace (SPA), jQuery neposkytuje mnoho požadovaných funkcí, které angular a reagovat nabízejí.

### <a name="legacy-web-apps-with-jquery"></a>Starší webové aplikace s jQuery

Ačkoli starověké standardy javascriptového frameworku, jQuery je i nadále běžně používanou knihovnou pro práci s HTML /CSS a vytvářením aplikací, které provádějí volání AJAX na webová rozhraní API. JQuery však pracuje na úrovni objektového modelu dokumentu prohlížeče (DOM) a ve výchozím nastavení nabízí pouze imperativ, nikoli deklarativní model.

Představte si například, že pokud hodnota textového pole překročí 10, prvek na stránce by měl být viditelný. V jQuery by to obvykle být implementována zápisem obslužné rutiny události s kódem, který by zkontroloval hodnotu textového pole a nastavil viditelnost cílového prvku na základě této hodnoty. Toto je imperativní přístup založený na kódu. Jiný rámec může místo toho použít datové vazby svázat viditelnost prvku na hodnotu textového pole deklarativně. To by nevyžadovalo psaní žádného kódu, ale místo toho vyžaduje pouze zdobení prvků, které jsou spojeny s atributy datové vazby. Jako chování na straně klienta stále složitější, přístupy vazby dat často za následek jednodušší řešení s méně kódu a podmíněné složitosti.

### <a name="jquery-vs-a-spa-framework"></a>jQuery vs spa rámec

| **Faktor** | **jQuery** | **Angular**|
|--------------------------|------------|-------------|
| Abstrahuje dom | **Ano** | **Ano** |
| Podpora AJAX | **Ano** | **Ano** |
| Deklarativní datová vazba | **Ne** | **Ano** |
| Směrování ve stylu MVC | **Ne** | **Ano** |
| Templating | **Ne** | **Ano** |
| Směrování s hlubokým propojením | **Ne** | **Ano** |

Většina funkcí jQuery postrádá vnitřně mohou být přidány s přidáním dalších knihoven. Nicméně, SPA rámec jako Angular poskytuje tyto funkce v integrovanějším způsobem, protože to bylo navrženo se všemi z nich v mysli od začátku. Také jQuery je imperativní knihovna, což znamená, že musíte volat jQuery funkce, aby se něco dělat s jQuery. Velká část práce a funkce, které poskytují spa architektury lze provést deklarativně, vyžadující žádný skutečný kód, který má být zapsán.

Datová vazba je skvělým příkladem. V jQuery obvykle trvá pouze jeden řádek kódu získat hodnotu prvku DOM nebo nastavit hodnotu prvku. Však budete muset napsat tento kód kdykoli budete muset změnit hodnotu prvku a někdy k tomu dojde ve více funkcí na stránce. Dalším běžným příkladem je viditelnost prvku. V jQuery může být mnoho různých míst, kde byste psát kód pro řízení, zda některé prvky byly viditelné. V každém z těchto případů při použití datové vazby by bylo nutné zapsat žádný kód. Jednoduše byste svázat hodnotu nebo viditelnost prvků v otázce *viewmodel* na stránce a změny tohoto modelu zobrazení by se automaticky projeví v vázané prvky.

### <a name="angular-spas"></a>Úhlové sa

Angular zůstává jedním z nejpopulárnějších javascriptových rámců na světě. Vzhledem k tomu, Angular 2, tým přestavěl rámec od základu (pomocí [TypeScript)](https://www.typescriptlang.org/)a rebranded z původního angularJS jméno jednoduše angular. Nyní několik let starý, přepracovaný Angular je i nadále robustní rámec pro vytváření jednostránkových aplikací.

Úhlové aplikace jsou sestaveny z komponent. Komponenty kombinují šablony HTML se speciálními objekty a řídí část stránky. Jednoduchá součást z angularových dokumentů je zobrazena zde:

```js
import { Component } from '@angular/core';

@Component({
    selector: 'my-app',
    template: `<h1>Hello {{name}}</h1>`
})

export class AppComponent { name = 'Angular'; }
```

Komponenty jsou definovány pomocí funkce @Component decorator, která přebírá metadata o komponentě. Vlastnost selektoru identifikuje ID prvku na stránce, kde se zobrazí tato komponenta. Vlastnost šablony je jednoduchá šablona HTML, která obsahuje zástupný symbol, který odpovídá vlastnosti názvu komponenty definované na posledním řádku.

Při práci s komponentami a šablonami, namísto prvků DOM, angular aplikace mohou pracovat na vyšší úrovni abstrakce a s méně celkovým kódem než aplikace napsané pouze pomocí JavaScriptu (také volal "vanilka JS") nebo s jQuery. Úhlový také ukládá určité pořadí na způsob uspořádání souborů skriptů na straně klienta. Podle konvence používají angularské aplikace společnou strukturu složek se soubory modulů a dílčích skriptů umístěnými ve složce aplikace. Úhlové skripty týkající se vytváření, nasazování a testování aplikace jsou obvykle umístěny ve složce vyšší úrovně.

Angular aplikace můžete vyvíjet pomocí cli. Začínáme s vývojem Angular lokálně (za předpokladu, že již máte nainstalovaný git a `npm install` npm) se skládá z pouhého klonování repo z GitHubu a spuštění a `npm start`. Kromě toho angular dodává vlastní cli, které může vytvářet projekty, přidávat soubory a pomáhat s testováním, svazováním a nasazením úkolů. Tato přívětivost CLI dělá angular obzvláště kompatibilní s ASP.NET Core, který také nabízí skvělou podporu CLI.

Společnost Microsoft vyvinula referenční aplikaci [eShopOnContainers](https://aka.ms/MicroservicesArchitecture), která obsahuje implementaci Angular SPA. Tato aplikace obsahuje úhlové moduly pro správu nákupního košíku online obchodu, načtení a zobrazení položek z katalogu a vytváření objednávek. Ukázkovou aplikaci si můžete prohlédnout a stáhnout z [GitHubu](https://github.com/dotnet-architecture/eShopOnContainers/tree/master/src/Web/WebSPA).

### <a name="react"></a>React

Na rozdíl od Angular, který nabízí úplnou implementaci vzoru Model-View-Controller, React se zabývá pouze zobrazeními. Není to rámec, jen knihovna, takže k vytvoření SPA budete muset využít další knihovny. Existuje celá řada knihoven, které jsou navrženy pro použití s Reagova tatožnou aplikací.

Jednou z nejdůležitějších vlastností Reactu je jeho použití virtuálního DOM. Virtuální DOM poskytuje Reagovat s několika výhodami, včetně výkonu (virtuální DOM může optimalizovat, které části skutečného DOM je třeba aktualizovat) a testovatelnost (není třeba mít prohlížeč pro testování React a jeho interakce s jeho virtuální DOM).

Reagovat je také neobvyklé v tom, jak to funguje s HTML. Spíše než mít přísné oddělení mezi kódem a značky (s odkazy na JavaScript uvedené v html atributy možná), React přidává HTML přímo v jeho javascriptový kód jako JSX. JSX je HTML-jako syntaxe, která může kompilovat až do čistého JavaScriptu. Například:

```js
<ul>
{ authors.map(author =>
    <li key={author.id}>{author.name}</li>
)}
</ul>
```

Pokud již znáte JavaScript, učení React by mělo být snadné. Není zdaleka tolik křivky učení nebo speciální syntaxe zapojené jako s úhlové nebo jiné populární knihovny.

Vzhledem k tomu, že React není úplná architektura, budete obvykle chtít, aby ostatní knihovny zpracovávat věci, jako je směrování, volání webového rozhraní API a správa závislostí. Pěkná věc je, můžete si vybrat nejlepší knihovnu pro každou z nich, ale nevýhodou je, že musíte učinit všechna tato rozhodnutí a ověřit všechny vybrané knihovny dobře spolupracovat, když jste hotovi. Pokud chcete dobrý výchozí bod, můžete použít startovací sadu, jako je React Slingshot, která spolu s React zabalí sadu kompatibilních knihoven.

### <a name="vue"></a>Vue

Z jeho začínáme průvodce, "Vue je progresivní rámec pro vytváření uživatelských rozhraní. Na rozdíl od jiných monolitických rámců je Vue navrženod základu tak, aby byl postupně použitelný. Základní knihovna je zaměřena pouze na vrstvu zobrazení a lze ji snadno vyzvednout a integrovat s jinými knihovnami nebo existujícími projekty. Na druhou stranu, Vue je dokonale schopen napájet sofistikované jednostránkové aplikace při použití v kombinaci s moderními nástroji a podpůrnými knihovnami."

Začínáme s Vue jednoduše vyžaduje zahrnutí jeho skript v souboru HTML:

```html
<!-- development version, includes helpful console warnings -->
<script src="https://cdn.jsdelivr.net/npm/vue/dist/vue.js"></script>
```

S rámec přidán, pak jste schopni deklarativně vykreslit data do DOM pomocí vue je jednoduché šablonování syntaxe:

```html
<div id="app">
  {{ message }}
</div>
```

a pak přidáte následující skript:

```js
var app = new Vue({
  el: '#app',
  data: {
    message: 'Hello Vue!'
  }
})
```

To je dost k tomu, aby "Hello Vue!" na stránce. Všimněte si však, že Vue není jednoduše vykreslování zprávy div jednou. Podporuje datové vazby a dynamické aktualizace `message` tak, že pokud `<div>` hodnota změny, hodnota v je okamžitě aktualizován tak, aby odrážely.

Samozřejmě, to jen škrábe povrch toho, čeho je Vue schopen. Je to získal velkou popularitu v posledních několika letech a má velkou komunitu. K dispozici je [obrovský a rostoucí seznam podpůrných komponent a knihoven,](https://github.com/vuejs/awesome-vue#redux) které pracují s Vue rozšířit také. Pokud hledáte přidat klient-side chování do webové aplikace, nebo zvažuje budování úplné SPA, Vue stojí za prošetření.

### <a name="choosing-a-spa-framework"></a>Výběr SPA frameworku

Při zvažování, který javascriptový framework bude nejlépe fungovat pro podporu vašeho SPA, mějte na paměti následující aspekty:

- Je váš tým obeznámen s rámcem a jeho závislostmi (v některých případech včetně jazyka TypeScript)?

- Jak umíněný je rámec, a souhlasíte s jeho výchozí způsob, jak dělat věci?

- Obsahuje (nebo doprovodnou knihovnu) všechny funkce, které vaše aplikace vyžaduje?

- Je to dobře zdokumentováno?

- Jak aktivní je jeho komunita? Budují se s ním nové projekty?

- Jak aktivní je jeho hlavní tým? Jsou problémy vyřešeny a nové verze dodávány pravidelně?

JavaScriptové architektury se nadále vyvíjejí závratnou rychlostí. Pomocí výše uvedených aspekty můžete zmírnit riziko výběru rámce, na které budete později litovat, že budete závislí. Pokud jste obzvláště riziko-averze, zvažte rámec, který nabízí komerční podporu a / nebo je vyvíjen velkým podnikem.

> ### <a name="references--client-web-technologies"></a>Reference – Klientské webové technologie
>
> - **HTML a CSS**  
> <https://www.w3.org/standards/webdesign/htmlcss>
> - **Sass vs MÉNĚ**  
> <https://www.keycdn.com/blog/sass-vs-less/>
> - **Styling ASP.NET základní aplikace s less, sass, a font awesome**  
> <https://docs.microsoft.com/aspnet/core/client-side/less-sass-fa>
> - **Vývoj na straně klienta v ASP.NET jádru**  
> <https://docs.microsoft.com/aspnet/core/client-side/>
> - **jQuery**  
> <https://jquery.com/>
> - **jQuery vs AngularJS**  
> <https://www.airpair.com/angularjs/posts/jquery-angularjs-comparison-migration-walkthrough>
> - **Angular**  
> <https://angular.io/>
> - **React**  
> <https://reactjs.org/>
> - **Vue**  
> <https://vuejs.org/>
> - **Úhlové vs Reagovat vs Vue: Který rámec si vybrat v roce 2020**
> <https://www.codeinwp.com/blog/angular-vs-vue-vs-react/>
> - **Top JavaScript frameworks pro front-end vývoj v roce 2020**  
> <https://www.freecodecamp.org/news/complete-guide-for-front-end-developers-javascript-frameworks-2019/>

>[!div class="step-by-step"]
>[Předchozí](common-web-application-architectures.md)
>[další](develop-asp-net-core-mvc-apps.md)
