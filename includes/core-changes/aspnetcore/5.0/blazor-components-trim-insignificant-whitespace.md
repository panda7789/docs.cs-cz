---
ms.openlocfilehash: ca369c4e3f78648c6e8e0bcb5d54711d3009a769
ms.sourcegitcommit: cb27c01a8b0b4630148374638aff4e2221f90b22
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/09/2020
ms.locfileid: "86174257"
---
### <a name="blazor-insignificant-whitespace-trimmed-from-components-at-compile-time"></a>Blazor: nevýznamné prázdné znaky oříznuté z komponent v době kompilace

Počínaje verzí ASP.NET Core 5,0 Preview 7 kompilátor Razor vynechává v době kompilace nevýznamné prázdné znaky v komponentách Blazor (soubory *. Razor* ). Diskuzi najdete v tématu problém [dotnet/aspnetcore # 23568](https://github.com/dotnet/aspnetcore/issues/23568).

#### <a name="version-introduced"></a>Představená verze

5,0 Preview 7

#### <a name="old-behavior"></a>Staré chování

Ve 3. x verzích serveru Blazor a v Blazor WebAssembly se ve zdrojovém kódu komponenty nepoužívá prázdné znaky. Jenom prázdné textové uzly se vykreslují v model DOM (Document Object Model) v prohlížeči (DOM), a to i v případě, že není k dispozici žádný vizuální efekt.

Vezměte v úvahu následující kód komponenty Blazor:

```razor
<ul>
    @foreach (var item in Items)
    {
        <li>
            @item.Text
        </li>
    }
</ul>
```

Předchozí příklad vykreslí dva prázdné uzly:

* Mimo `@foreach` blok kódu.
* Kolem `<li>` prvku.
* Kolem `@item.Text` výstupu.

Seznam obsahující 100 položek má za následek 402 prázdných uzlů. To je více než polovina všech vykreslených uzlů, i když žádný z uzlů prázdných znaků nemá vizuálně vliv na Vykreslený výstup.

Při vykreslování statického HTML pro součásti se nezachovají prázdné znaky uvnitř značky. Můžete například zobrazit zdroj následující součásti:

```razor
<foo        bar="baz"     />
```

Prázdný znak se nezachová. Předem Vykreslený výstup je:

```razor
<foo bar="baz" />
```

#### <a name="new-behavior"></a>Nové chování

Pokud se `@preservewhitespace` direktiva nepoužívá s hodnotou `true` , prázdné uzly se odeberou, pokud jsou:

* Jsou na začátku nebo na konci elementu.
* Jsou na začátku nebo na konci v rámci `RenderFragment` parametru. Například podřízený obsah předávaný do jiné součásti.
* Předchází nebo dodržujte blok kódu jazyka C#, jako je `@if` a `@foreach` .

#### <a name="reason-for-change"></a>Důvod změny

Cílem pro Blazor v ASP.NET Core 5,0 je vylepšit výkon vykreslování a rozdílů. Nevýznamné uzly stromu prázdných znaků využily až 40 procent času vykreslování v srovnávacích testech.

#### <a name="recommended-action"></a>Doporučená akce

Ve většině případů je vizuální rozložení vykreslené komponenty neovlivněno. Odebrání prázdných znaků však může ovlivnit Vykreslený výstup při použití pravidla šablony stylů CSS `white-space: pre` , jako je. Chcete-li zakázat tuto optimalizaci výkonu a zachovat prázdné znaky, proveďte jednu z následujících akcí:

* Přidejte `@preservewhitespace true` direktivu v horní části souboru *. Razor* , abyste použili předvolby pro konkrétní komponentu.
* Přidejte `@preservewhitespace true` direktivu do souboru *_Imports. Razor* pro použití předvolby pro celý podadresář nebo celý projekt.

Ve většině případů není nutná žádná akce, protože aplikace se obvykle budou často chovat normálně (ale rychleji). Pokud odstranění prázdných znaků způsobí jakékoli problémy určité součásti, použijte `@preservewhitespace true` v této součásti tuto optimalizaci.

#### <a name="category"></a>Kategorie

ASP.NET Core

#### <a name="affected-apis"></a>Ovlivněná rozhraní API

Žádné

<!--

#### Affected APIs

Not detectable via API analysis

-->
