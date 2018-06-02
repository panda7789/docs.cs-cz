---
title: Historie jazyka C# – průvodce v C#
description: Co vzhledu jazyk líbí v nejstarších verzích, a jak vyvinul od?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: e659f2438e9785a02f7016e49b78015ad46b9133
ms.sourcegitcommit: 3540f614fc94f77ca4ab58df66db2d0f4d52dfee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/01/2018
ms.locfileid: "34696972"
---
# <a name="the-history-of-c"></a>Historie jazyka C# #

Co vzhledu jazyk v jeho nejdřívější ztělesněních vytvořit? A jak vyvinul během let od?

## <a name="c-version-10"></a>C# verze 1.0

Přejděte zpět a podívejte se, C# verze 1.0 hledá mnoho jako Java. Jako [součástí jeho stanovené cíle pro ECMA](http://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), se žádá o jako "objektově orientované jazyk jednoduchý, moderní, obecné účely."  V době vyhledávání jako Java, čeho se dosáhne těmito časná cíli.

Ale když se podíváte zpět na C# 1.0 nyní, budete by sami trochu dizzy. Neobsahovala možnosti integrované asynchronní a některé funkce slick kolem obecné typy, které jsme provést pro udělena. Jako matter z skutečnosti neobsahovala obecné úplně.  A [LINQ](../linq/index.md)? Není k dispozici dosud. Které by byly třeba některé letech.

C# verze 1.0 hledá odřapíkovaného funkcí ve srovnání s dnes. By najít sami zápis některé podrobné kódu. Ale ještě, budete muset spustit někde. C# verze 1.0 byl přijatelná alternativa k Java na platformě Windows.

## <a name="c-version-20"></a>C# verze 2.0

Nyní věcí spustit získat zajímavé. Podívejme se na některé hlavní funkce jazyka C# 2.0, vydané v 2005, společně s Visual Studio 2005:

- [Obecné typy](../programming-guide/generics/index.md)
- [Částečné typy](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonymní metody](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Typy s možnou hodnotou Null](../programming-guide/nullable-types/index.md)
- [Iterátory](../programming-guide/concepts/iterators.md)
- [Kovariance a kontravariance](../programming-guide/concepts/covariance-contravariance/index.md)

Při C# může spustili jako poměrně obecné jazyk Object-Oriented (ú), verze 2.0 c změnit, rychle. Jakmile měly jejich nohou nich, se po některé závažné vývojáře problémové body. A jejich došlo po jejich velký způsobem.

Obecné typy máte typy a metody, které může fungovat na libovolný typ a zároveň zachovat bezpečnost typů. Ano, například s <xref:System.Collections.Generic.List%601> umožňuje mít `List<string>` nebo `List<int>` a provádět typ bezpečné operace na tyto řetězce nebo celá čísla, zatímco iterace je. Toto je lepší, než vytváření `ListInt` dědice nebo přetypování z `Object` pro všechny operace.

C# iterátory verze 2.0 uvést do režimu. Stručně uvést, to umožňuje iteraci v rámci položky v `List` (nebo jiné výčtové typy) s `foreach` smyčky. Jako první třídy součástí jazyk s výrazně lepší čitelnost jazyk a lidově schopnost důvod o kód.

Ještě, C# pokračovat a přehrávání kousek zjištěná v jazyce Java. Java měl již vydaných verzí, které zahrnuty obecné typy a iterátory. Ale které brzy změní jako jazyky dál momentální od sebe.

## <a name="c-version-30"></a>C# verze 3.0

C# 3.0 verze byla v pozdní 2007, společně s Visual Studio 2008, i když úplné člun funkcí jazyka by ve skutečnosti součástí rozhraní .NET Framework verze 3.5. Tato verze označena hlavní změnu růst jazyka C#. Zjistí-C# jako skutečně formidable programovací jazyk. Podívejme se na některé hlavní funkce v této verzi:

- [Automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
- [Výrazy dotazů](../linq/query-expression-basics.md)
- [výraz lambda](https://www.daedtech.com/introduction-to-c-lambda-expressions/)
- [Stromy výrazů](https://blogs.msdn.microsoft.com/charlie/2008/01/31/expression-tree-basics/)
- [Metody rozšíření](https://www.codeproject.com/Tips/709310/Extension-Method-In-Csharp)

V retrospect mnoho z těchto funkcí pravděpodobně nevyhnutelné i nelze oddělit. Všechny zapadají strategicky. Obecně je představit, že používání funkce jazyka C# verze byla výrazu dotazu, také známé jako Language-Integrated Query (LINQ).

Zobrazení více nuanced prověří stromů výrazů lambda – výrazy a anonymní typy jako základ, na kterém je vytvořený LINQ. Ale v obou případech C# 3.0 zobrazí revoluční koncept. C# 3.0 bylo zahájeno jen pro vypnutí C# do hybridním objektově orientované / funkční jazyk.

Konkrétně může zapisovat teď stylu SQL, deklarativní dotazy k provádění operací na kolekce, mimo jiné. Místo psaní `for` cykly k výpočtu průměru seznam celých čísel, můžete to teď udělat jako jednoduše jako `list.Average()`. Kombinace výrazy dotazů a rozšiřující metody provedené se zdát, že tento seznam celých čísel byl zadán mnoho efektivněji.

Trvalo čas pro uživatele, kteří mají skutečně pochopit a integrovat koncept, ale postupně se. A teď let později, kód je mnohem víc stručné sdělení, jednoduchý a funkční.

## <a name="c-version-40"></a>C# verze 4.0

C# verze 4.0 by neměly mít složité čas životních Přelomová stav verze 3.0. Verze 3.0 C# měl přesunout jazyk správně zapojený odhlašování ze stínové jazyka Java a do úroveň. Jazyk byl rychle stal elegantní.

Na další verzi zavádět některé zajímavé nové funkce:

- [Dynamické vazby](../language-reference/keywords/dynamic.md)
- [S názvem nepovinné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Obecná kovariantní a kontravariant](../../standard/generics/covariance-and-contravariance.md)
- [Vložené typy spolupráce](https://stackoverflow.com/questions/20514240/whats-the-difference-setting-embed-interop-types-true-and-false-in-visual-studi)

Vestavěné typy spolupráce zmírnit problémové nasazení. Obecné kovariance a kontravariance získáte další power použít obecné typy, ale jsou trochu academic a pravděpodobně nejvíce vezme v úvahu autory framework a knihovny. Pojmenované a nepovinné parametry umožňují eliminovat mnoho přetížení metody a zajistí pohodlí. Ale žádná z těchto funkcí jsou přesně zlepší změny.

Hlavní funkce byla zavedení `dynamic` – klíčové slovo. `dynamic` – Klíčové slovo, dát do jazyka C# verze 4.0 možnost přepsat kompilátoru na zadáním kompilaci. Pomocí dynamické klíčové slovo, můžete vytvořit konstrukce podobná dynamicky zadávaných jazyky, jako je JavaScript. Můžete vytvořit `dynamic x = "a string"` a poté přidejte šest, ponechává vyřešit, která má proběhnout vedle modulu runtime.

To vám dává potenciální chyby, ale také skvělé power v rámci jazyk.

## <a name="c-version-50"></a>C# verze 5.0

C# verze 5.0 se velmi cílených verze jazyka. Téměř všechny úsilí pro tuto verzi se stala součástí jiného koncept Přelomová jazyk.  Tady je seznam hlavních funkce:

- [Asynchronní členy](../async.md)
- [Volající – atributy s informacemi](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Informace o atributu volající umožňuje snadno načíst informace o kontextu, ve kterém spouštíte bez nutnosti tuny standardní reflexí kódu. Má mnoho používá v diagnostiky a úloh protokolování.

Ale `async` a `await` jsou skutečné hvězdiček této verze. Pokud tyto funkce dodán v 2012, C# změnit hra znovu pečení asynchrony do jazyka jako účastník první třídy. Pokud jste někdy řešeno dlouhotrvající operace a provádění a weby zpětných volání, budete pravděpodobně kontakt máte rádi tato funkce jazyka.

## <a name="c-version-60"></a>C# verze 6.0

Verze 3.0 a 5.0 C# měl přidat některé působivé funkce v jazyce objektově orientované. Verze 6.0 by přejděte od provádění dominantní používání funkce a místo vydání řadu funkcí, které ctí uživatelé jazyka. Tady jsou některé z nich:

- [Statické importy](../language-reference/keywords/using-static.md)
- [Filtry výjimek](https://www.thomaslevesque.com/2015/06/21/exception-filters-in-c-6/)
- [Inicializátory vlastnost](http://geekswithblogs.net/WinAZ/archive/2015/06/30/whatrsquos-new-in-c-6.0-auto-property-initializers.aspx)
- [Výraz vozidlo členy](https://lostechies.com/jimmybogard/2015/12/17/c-6-feature-review-expression-bodied-function-members/)
- [Šiřitel hodnotu Null.](https://davefancher.com/2014/08/14/c-6-0-null-propagation-operator/)
- [Interpolace řetězců](../language-reference/tokens/interpolated.md)
- [nameof – operátor](https://stackoverflow.com/questions/31695900/what-is-the-purpose-of-nameof)
- [Inicializátory indexu](csharp-6.md#index-initializers)

Každá z těchto funkcí je zajímavé v sobě. Ale pokud si prohlédnete je zcela, zobrazí zajímavé vzor. V této verzi jazyka C# eliminovat standardní jazyk, aby kód víc ve formátu Terse zasílaná a čitelné. Proto ventilátory čistá, jednoduchého kódu, tato verze jazyka nemohla obrovské win.

Když není funkce tradiční jazyk sám o sobě, co udělali jednu věc společně s touto verzí. Budou vydané [Roslyn kompilátoru jako služba](https://github.com/dotnet/roslyn). Kompilátor jazyka C# je teď vytvořené v C# a kompilátor můžete použít v rámci svého programování úsilí.

## <a name="c-version-70"></a>C# verze 7.0

Nejnovější hlavní verzi je C# verze 7.0. Tato verze má některé věcem evolučním a nástrojů v vein C# 6.0, ale bez kompilátor jako služba. Tady jsou některé z nových funkcí:

- [Out proměnné](http://www.c-sharpcorner.com/article/out-variables-in-c-sharp-7-0/)
- [Řazené kolekce členů a deconstruction](https://www.thomaslevesque.com/2016/08/23/tuple-deconstruction-in-c-7/)
- [Shoda vzoru](./csharp-7.md#pattern-matching)
- [Lokální funkce](http://www.infoworld.com/article/3182416/application-development/c-7-in-depth-exploring-local-functions.html)
- [Rozšířené výraz vozidlo členy](./csharp-7.md#more-expression-bodied-members)
- [Místní hodnoty REF a vrátí](./csharp-7.md#ref-locals-and-returns)

Všechny tyto funkce nabízí nové funkce nástrojů pro vývojáře a možnost zápisu i čisticí kódu než kdy dřív. Zvýraznění je sloučíte deklarace proměnné pro použití s `out` – klíčové slovo a tím, že více vrácených hodnot prostřednictvím řazené kolekce členů.

Ale C# se provádí požadavek put pro někdy širší použití. .NET core teď cílí žádný operační systém a má jeho očí správně zapojený do cloudu a na přenositelnost.  To jistě zabírá jazyk návrhářům nápady a čas, kromě objevuje nové funkce.

_Článek_ [ _původně publikovaná na blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, s laskavým svolením Erik Dietrich a Patrik Smacchia._
