---
title: Historie jazyka C# – průvodce v C#
description: Co vzhled jazyka, jako je v jeho nejstarší verze a jak vyvinula od?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 84274f8ddfd8295d5db1e861c790c134ba30c6e2
ms.sourcegitcommit: 16aefeb2d265e69c0d80967580365fabf0c5d39a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/16/2019
ms.locfileid: "58126146"
---
# <a name="the-history-of-c"></a>Historie jazyka C\#

Tento článek obsahuje historii každé hlavní verze produktu C# jazyka. C# Týmu nepřestává vám umožní inovovat a přidání nových funkcí. Podrobný stav funkce jazyka, včetně funkcí pro nadcházejících vydáních najdete [v úložišti dotnet/roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) na Githubu.

> [!IMPORTANT]
> C# Jazyk spoléhá na typy a metody v co C# specifikace definuje jako *standardní knihovny* pro některé funkce. Na platformě .NET nabízí tyto typy a metody v počtu balíčků. Jedním z příkladů je zpracování výjimek. Každý `throw` příkaz nebo výraz je zaškrtnuto, aby objekt vyvolané je odvozen z <xref:System.Exception>. Podobně každý `catch` proběhne kontrola, že typ je zachycena je odvozen od <xref:System.Exception>. Každá verze může přidat nové požadavky. Chcete-li používat nejnovější funkce jazyků v starší prostředí, budete muset nainstalovat konkrétní knihovny. Tyto závislosti jsou popsané na stránce u každé konkrétní verze. Další informace o [vztahy mezi jazykem a knihovny](relationships-between-language-and-library.md) Další informace o této závislosti.

C# Nástroje pro vytváření zvažte nejnovější verzi hlavní jazyk výchozí jazykovou verzi. Můžou existovat dílčích verzí mezi hlavními verzemi, najdete v dalších článcích v této části. Chcete-li používat nejnovější funkce ve verzi bod, je potřeba [konfigurace verze jazyka kompilátoru](../language-reference/configure-language-version.md) a vyberte verzi. Byly tří dílčích verzí od C# 7.0:

* [C# 7.3](csharp-7-3.md):
  - C#7.3 je aktuálně dostupné v [Visual Studio 2017 verze 15.7](https://visualstudio.microsoft.com/vs/whatsnew/)a [.NET Core 2.1 SDK 2.1.300 RC1](../../core/whats-new/index.md).
* [C# 7.2](csharp-7-2.md):
  - C#7.2 je aktuálně dostupné v [Visual Studio 2017 verze 15.5](https://visualstudio.microsoft.com/vs/whatsnew/)a [.NET Core 2.0 SDK](../../core/whats-new/index.md).
* [C# 7.1](csharp-7-1.md):
  - Tyto funkce byly přidány v [Visual Studio 2017 verze 15.3](https://visualstudio.microsoft.com/vs/whatsnew/)a [.NET Core 2.0 SDK](../../core/whats-new/index.md).

## <a name="c-version-10"></a>C# verze 1.0

Když přejděte zpět a podívejte se, C# verze 1.0 vypadal mnohem Java. Jako [součástí jeho návrhu stanovené cíle pro ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html), ho chtěli být "jednoduché, moderní a pro obecné účely objektově orientovaný jazyk."  V době hledání, jako je Java určená ho budete muset tyto počáteční návrh cíle.

Ale pokud se můžete podívat zpět v C# 1.0 nyní, ekvivalent byste našli sami trochu dizzy. Neobsahovala integrované asynchronní funkce a některé funkce uhlazený kolem obecných typů, které můžete provést pro udělen. Jako skutečnosti neobsahovala obecných typů úplně se vynechá.  A [LINQ](../linq/index.md)? Není k dispozici dosud. Tyto doplňky padl některé letech navýšení kapacity.

C# verze 1.0 podívali funkcí v porovnání s dnešní odstraněnými příslušnými daty. By pro vás sami psaním podrobného kódu. Ale ještě, budete muset spustit někde. C# verze 1.0 byl alternativa k Java na platformě Windows.

Hlavní funkce C# 1.0 zahrnuté:

- [Třídy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../programming-guide/classes-and-structs/structs.md)
- [Rozhraní](../programming-guide/interfaces/index.md)
- [Události](../events-overview.md)
- [Vlastnosti](../properties.md)
- [Delegáti](../delegates-overview.md)
- [Výrazy](../programming-guide/statements-expressions-operators/expressions.md)
- [Příkazy](../programming-guide/statements-expressions-operators/statements.md)
- [Atributy](../programming-guide/concepts/attributes/index.md)
- [Literály](../language-reference/keywords/literal-keywords.md)

## <a name="c-version-12"></a>C# verze 1.2

C# verze 1.2 dodávané s Visual Studio 2003. Obsahuje několik vylepšení malé na jazyk. Většina zajímavé je, že od s touto verzí, vytvořit kód v `foreach` smyčky volá <xref:System.IDisposable.Dispose%2A> na <xref:System.Collections.IEnumerator> při, který <xref:System.Collections.IEnumerator> implementované <xref:System.IDisposable>.

## <a name="c-version-20"></a>C# verze 2.0

Teď začít získat zajímavé věci. Pojďme se podívat na některé hlavní funkce C# 2.0, vydána v roce 2005, spolu s Visual Studio 2005:

- [Obecné typy](../programming-guide/generics/index.md)
- [Částečné typy](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonymní metody](../programming-guide/statements-expressions-operators/anonymous-methods.md)
- [Typy s možnou hodnotou Null](../programming-guide/nullable-types/index.md)
- [Iterátory](../programming-guide/concepts/iterators.md)
- [Kovariance a kontravariance](../programming-guide/concepts/covariance-contravariance/index.md)

Další funkce C# 2.0 přidat možnosti do stávajících funkcí:

- Samostatné usnadnění přístupu metody getter a setter
- Metoda skupiny převody (delegátů)
- Statické třídy
- Odvození delegáta

Zatímco C# mohou být spuštěny jako obecný jazyk Object-Oriented (zálohy), C# verze 2.0 se změnilo s nemáte. Po jejich nohou pod nimi měli, k nějaké po některé palčivé závažné pro vývojáře. A po jejich zvládli významné způsobem.

S obecnými typy typy a metody mohou pracovat s libovolného typu zároveň zachovat bezpečnost typů. Například s <xref:System.Collections.Generic.List%601> umožňuje mít `List<string>` nebo `List<int>` a provádět operace zajišťující bezpečnost typů na tyto řetězce nebo celočíselné hodnoty, zatímco iterovat přes ně. Použití obecných typů je lepší než vytvoření `ListInt` , která je odvozena z `ArrayList` nebo přetypování z: `Object` pro každou operaci.

C# verze 2.0 převést do režimu iterátory. Vložit stručně, iterátory umožňují zkoumat všechny položky v `List` (nebo jiné vyčíslitelné typy) s `foreach` smyčky. S iterátory první třídy v rámci jazyka výrazně vylepšit čitelnost jazyka a možnost uživatelů o kód.

A ještě, C# pokračování přehrávání hodně zachytávání pomocí Javy. Java měl již vydaných verzí, které zahrnuty obecné typy a iterátory. Ale jako jazyky dál rozvíjet této doby změny nepublikujete, který brzy změní.

## <a name="c-version-30"></a>C# verze 3.0

C# verze 3.0 byli zaznamenáni v pozdní 2007, spolu s Visual Studio 2008, i když úplné loď jazykové funkce by ve skutečnosti součástí rozhraní .NET Framework verze 3.5. Tato verze je označena jako velkou změnu nárůst jazyka C#. Zjistí-C# jako programovací jazyk, skutečně formidable. Pojďme se podívat na některé hlavní funkce v této verzi:

- [Automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
- [Výrazy dotazů](../linq/query-expression-basics.md)
- [Výrazy lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Stromy výrazů](../expression-trees.md)
- [Rozšiřující metody](../programming-guide/classes-and-structs/extension-methods.md)
- [Implicitně typované lokální proměnné](../language-reference/keywords/var.md)
- [Částečné metody](../language-reference/keywords/partial-method.md)
- [Inicializátory objektu a kolekce](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Když mnohé z těchto funkcí zdá se, že nevyhnutelné a nelze oddělit. Všechny zapadají strategicky. Obecně je představit, že skvělou funkci jazyka C# verze byla výraz dotazu, označované také jako Language-Integrated Query (LINQ).

Přesnější zobrazení prozkoumá stromů výrazů lambda výrazy a anonymní typy jako základ, na kterém je vytvořená LINQ. Ale v obou případech se zobrazí C# 3.0 revoluční koncept. C# 3.0 měl začali připravovat základy pro zapnutí C# do hybridních objektově orientované / funkční jazyk.

Konkrétně může zapisovat teď SQL – vizuální styl, deklarativní dotazů k provádění operací v kolekcích, mimo jiné. Místo psaní `for` smyčky k výpočtu průměru seznamu celých čísel, můžete to teď udělat jako jednoduše jako `list.Average()`. Kombinace – výrazy dotazů a rozšiřující metody dostal zdát, že tento seznam celých čísel vedli mnohem efektivněji.

Jakou trvalo čas lidé skutečně pochopit její podstatu a integrovat koncept, ale postupně udělal. A teď let, kód je mnohem více stručné, jednoduché a funkční.

## <a name="c-version-40"></a>C# verze 4.0

C# verze 4.0 by měli obtížné čas žijete přelomové stav verze 3.0. Verze 3.0 C# měli přesunout jazyk pevně ven z sledování jazyka Java a do význačnost. Jazyk se rychle stal elegantní.

Další verze zavést některé zajímavé nové funkce:

- [Dynamické vazby](../language-reference/keywords/dynamic.md)
- [Pojmenované a nepovinné argumenty.](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Obecná kovariantního a kontravariantního](../../standard/generics/covariance-and-contravariance.md)
- [Vložené typy spolupráce](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Vestavěné typy spolupráce zmírnit problémy nasazení. Obecný kovariance a kontravariance získáte víc možností, jak pomocí obecných typů, ale jsou to trochu akademické instituce a pravděpodobně nejvíce si vážíme autory rozhraní a knihovny. Pojmenované a nepovinné parametry umožňují eliminovat řadu přetížení metod a zajistí pohodlí. Ale žádná z těchto funkcí jsou přesně paradigma změna.

Hlavní funkce bylo zavedení konceptu `dynamic` – klíčové slovo. `dynamic` – Klíčové slovo zavádí do jazyka C# verze 4.0 možnost přepsat kompilátor při psaní v době kompilace. Pomocí klíčového slova dynamické můžete vytvořit konstrukce podobná dynamicky zadávaných jazyky, jako je JavaScript. Můžete vytvořit `dynamic x = "a string"` a pak přidejte 6, ale ponechává runtime řazení, co se stane dále.

Dynamická vazba dává potenciální chyby, ale také větší možnosti v rámci jazyka.

## <a name="c-version-50"></a>C# verze 5.0

C# verze 5.0 se cílené verze jazyka. Téměř všechny úsilí pro tuto verzi byly přidány do jiného konceptu přelomové jazyka: `async` a `await` model pro asynchronní programování.  Tady je seznam hlavních funkcí:

- [Asynchronní členy](../async.md)
- [Atributy informace o volajícím](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Viz také

* [Projekt kódu: Informace o volajícím atributů C# 5.0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Informace o atributu volající umožňuje snadno načíst informace o kontextu, ve kterém spouštíte bez použití svislých spoustu často používaný kód reflexe. Má mnoho použití v diagnostiky a protokolování úloh.

Ale `async` a `await` jsou skutečné hvězdiček v této verzi. Pokud tyto funkce přišli v 2012, C# změnit hry znovu pečení asynchronii do jazyka jako první třídy účastníka. Pokud jste někdy řešeny dlouho běžící operace a provádění weby zpětná volání, pravděpodobně miluju této funkci jazyka.

## <a name="c-version-60"></a>C# verze 6.0

S verze 3.0 a 5.0 C# měli přidat hlavní nové funkce v objektově orientovaný jazyk. S verzí 6.0 by přejít mimo to dominantní skvělou funkci a místo toho verzi mnoho menších funkcí, které provedli programováním v C# zvýšit produktivitu práce. Tady jsou některé z nich:

- [Statické importy](./csharp-6.md#using-static)
- [Filtry výjimek](./csharp-6.md#exception-filters)
- [Inicializátory automatickou vlastnost](./csharp-6.md#auto-property-initializers)
- [Členové s v těle výrazu](./csharp-6.md#expression-bodied-function-members)
- [Null Šiřitel](./csharp-6.md#null-conditional-operators)
- [Interpolace řetězců](./csharp-6.md#string-interpolation)
- [operátor nameof](./csharp-6.md#the-nameof-expression)
- [Inicializátory indexů](csharp-6.md#extension-add-methods-in-collection-initializers)

Mezi další nové funkce patří:

- Operátor await v blocích catch/finally
- Výchozí hodnoty pro vlastnosti jen pro funkci getter

Každá z těchto funkcí je zajímavé v sama o sobě. Ale když se podíváte na ně úplně se vynechá, uvidíte zajímavé vzor. V této verzi C# odstranili často používaný jazyk, aby kód víc stručný a čitelné. Proto pro fanoušky čistá, je kód, byla verze tohoto jazyka je obrovská výhoda.

Když není funkce tradiční jazyk v samotné udělal jednu věc spolu s touto verzí. Vydali [Roslyn kompilátoru jako služba](https://github.com/dotnet/roslyn). Kompilátor jazyka C# je nyní napsané v jazyce C# a kompilátor můžete použít jako součást programování.

## <a name="c-version-70"></a>C# verze 7.0

Nejnovější hlavní verzi je C# verze 7.0. Tato verze má některé evoluční a zajímavé věci v vein jazyka C# 6.0, ale bez kompilátor jako služba. Tady jsou některé nové funkce:

- [Navýšení kapacity proměnné](./csharp-7.md#out-variables)
- [Řazených kolekcí členů a dekonstrukce](./csharp-7.md#tuples)
- [Porovnávání vzorů](./csharp-7.md#pattern-matching)
- [Lokální funkce](./csharp-7.md#local-functions)
- [Rozšířené výraz s v těle členy](./csharp-7.md#more-expression-bodied-members)
- [Místní referenční hodnoty a vrátí](./csharp-7.md#ref-locals-and-returns)

Další funkce zahrnuté:

- [Zahození](./csharp-7.md#discards)
- [Binární literály a oddělovače číslic:](./csharp-7.md#numeric-literal-syntax-improvements)
- [Výrazy throw](./csharp-7.md#throw-expressions)

Všechny tyto funkce nabízejí zajímavé nové funkce pro vývojáře a příležitosti pro zápis i čistější kód než kdy dřív. Zvýraznění je kondenzačních deklarace proměnné pro použití s `out` – klíčové slovo a tím, že více návratových hodnot přes řazené kolekce členů.

Ale jazyka C# je uložením někdy širší využití. .NET core teď cílí libovolný operační systém a má jeho oči pevně v cloudu a přenositelnost.  Tyto nové možnosti jistě zabírat návrháře jazyka nápady a čas, kromě chystá se s novými funkcemi.

_Článek_ [ _původně publikovány na blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, poskytuje Erik Dietrich a Patrick Smacchia._
