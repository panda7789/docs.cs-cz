---
title: Historie průvodce C# - C#
description: Jak tento jazyk vypadal v jeho nejranějších verzích a jak se od té doby vyvíjel?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: 9114395a5c6cfd8df5da18024921c35828947e0b
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79399684"
---
# <a name="the-history-of-c"></a>Historie C\#

Tento článek obsahuje historii každé hlavní verze jazyka C#. Tým Jazyka C# pokračuje v inovacích a přidávání nových funkcí. Podrobný stav funkce jazyka, včetně funkcí zvažovaných pro nadcházející verze, najdete [v úložišti dotnet/roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) na GitHubu.

> [!IMPORTANT]
> Jazyk C# závisí na typech a metodách v tom, co specifikace Jazyka C# definuje jako *standardní knihovnu* pro některé funkce. Platforma .NET poskytuje tyto typy a metody v počtu balíčků. Jedním z příkladů je zpracování výjimek. Každý `throw` příkaz nebo výraz je kontrolována zajistit objekt, <xref:System.Exception>který je vyvolána je odvozen od . Podobně každý `catch` je kontrolována, aby bylo zajištěno, že <xref:System.Exception>typ ulovené je odvozen od . Každá verze může přidat nové požadavky. Chcete-li používat nejnovější funkce jazyka ve starších prostředích, bude pravděpodobně nutné nainstalovat konkrétní knihovny. Tyto závislosti jsou popsány na stránce pro každou konkrétní verzi. Další informace o [vztazích mezi jazykem a knihovnou](relationships-between-language-and-library.md) pro pozadí této závislosti.

Nástroje sestavení Jazyka C# považují nejnovější hlavní jazykovou verzi za výchozí jazykovou verzi. Mezi hlavními verzemi mohou být bodové verze, které jsou podrobně popsány v jiných článcích v této části. Chcete-li v bodové verzi používat nejnovější funkce, je třeba [nakonfigurovat jazykovou verzi kompilátoru](../language-reference/configure-language-version.md) a vybrat její verzi. Od c# 7.0 došlo k tříbodovým uvolněním:

- [C# 7.3](csharp-7-3.md):
  - C# 7.3 je k dispozici od [Visual Studio 2017 verze 15.7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2.1 SDK](../../core/whats-new/dotnet-core-2-1.md).
- [C# 7.2](csharp-7-2.md):
  - C# 7.2 je k dispozici od [Visual Studio 2017 verze 15.5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).
- [C# 7.1](csharp-7-1.md):
  - C# 7.1 je k dispozici od [Visual Studio 2017 verze 15.3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2.0 SDK](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C# verze 1.0

Když se vrátíte a podíváte, C# verze 1.0, vydané s Visual Studio .NET 2002, vypadal hodně jako Java. V [rámci svých stanovených cílů návrhu pro ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)se snažila být "jednoduchým, moderním, univerzálním objektově orientovaným jazykem".  V té době, vypadal jako Java znamenalo, že dosáhl těchto prvních cílů designu.

Ale když se teď ohlédneš za C# 1.0, budeš mít trochu závrať. Postrádala vestavěné asynchronní funkce a některé funkce úhledných kolem generik, které považujete za samozřejmost. Ve skutečnosti mu chyběly generika úplně.  A [LINQ?](../linq/index.md) Zatím není k dispozici. Tyto dodatky by trvalo několik let, aby vyšel.

C# verze 1.0 vypadal zbaven funkcí, ve srovnání s dneškem. Zjistil bys, že píšeš nějaký podrobný kód. Ale přesto musíte někde začít. C# verze 1.0 byla životaschopnou alternativou k Javě na platformě Windows.

Hlavní rysy C# 1.0 zahrnuty:

- [Třídy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../language-reference/builtin-types/struct.md)
- [Rozhraní](../programming-guide/interfaces/index.md)
- [Akce](../events-overview.md)
- [Vlastnosti](../properties.md)
- [Delegáty](../delegates-overview.md)
- [Výrazy](../programming-guide/statements-expressions-operators/expressions.md)
- [Příkazy](../programming-guide/statements-expressions-operators/statements.md)
- [Atributy](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# verze 1.2

C# verze 1.2 dodávána s Visual Studio .NET 2003. Obsahuje několik malých vylepšení jazyka. Nejpozoruhodnější je, že počínaje touto verzí, `foreach` kód <xref:System.IDisposable.Dispose%2A> generovaný <xref:System.Collections.IEnumerator> ve <xref:System.IDisposable>smyčce volal, <xref:System.Collections.IEnumerator> když to implementováno .

## <a name="c-version-20"></a>C# verze 2.0

Teď to začíná být zajímavé. Podívejme se na některé hlavní funkce jazyka C# 2.0 vydaného v roce 2005 spolu se souborem Visual Studio 2005:

- [Obecné typy](../programming-guide/generics/index.md)
- [Částečné typy](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonymní metody](../language-reference/operators/delegate-operator.md)
- [Typy hodnot s možnou hodnotou s hodnotou Null](../language-reference/builtin-types/nullable-value-types.md)
- [Iterátory](../programming-guide/concepts/iterators.md)
- [Kovariance a kontravariance](../programming-guide/concepts/covariance-contravariance/index.md)

Další funkce jazyka C# 2.0 přidaly funkce k existujícím funkcím:

- Přístupnost pro získání/nastavení
- Převody skupin metod (delegáti)
- Statické třídy
- Odvození delegáta

Zatímco C# může mít spuštěna jako obecný objektově orientovaný (OO) jazyk, C# verze 2.0 změnil, že ve spěchu. Jakmile měli nohy pod sebou, šli po nějaké vážné developer bolesti bodů. A šli po nich významným způsobem.

S obecnými typy, typy a metody mohou pracovat na libovolný typ při zachování bezpečnosti typů. Například s <xref:System.Collections.Generic.List%601> umožňuje mít `List<string>` nebo `List<int>` provádět operace bezpečné pro typ na tyto řetězce nebo celá čísla, zatímco vy iterate přes ně. Použití obecných typů `ListInt` je lepší `ArrayList` než vytvořit, který je odvozen nebo odlévání z `Object` pro každou operaci.

C# verze 2.0 přinesl iterátory. Stručně řečeno, iterátory umožňují prozkoumat všechny položky v `List` (nebo jiné výčíslné typy) se smyčkou. `foreach` S iterátory jako prvotřídní část jazyka dramaticky zvýšila čitelnost jazyka a schopnost lidí důvod o kódu.

A přesto, C # i nadále hrát trochu catch-up s Javou. Java již vydala verze, které zahrnovaly generika a iterátory. Ale to by se brzy změnilo, jak se jazyky stále vyvíjely od sebe.

## <a name="c-version-30"></a>C# verze 3.0

C# verze 3.0 přišel na konci roku 2007, spolu s Visual Studio 2008, i když plné loď jazykových funkcí by ve skutečnosti přijít s rozhraním .NET Framework verze 3.5. Tato verze znamenala významnou změnu v růstu jazyka C#. To vytvořilo C# jako skutečně impozantní programovací jazyk. Podívejme se na některé hlavní funkce v této verzi:

- [Automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
- [Výrazy dotazu](../linq/query-expression-basics.md)
- [Výrazy lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Stromy výrazů](../expression-trees.md)
- [Metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md)
- [Implicitně zadané místní proměnné](../language-reference/keywords/var.md)
- [Dílčí metody](../language-reference/keywords/partial-method.md)
- [Inicializátory objektů a kolekcí](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Při zpětném pohledu se mnohé z těchto rysů zdají nevyhnutelné a neoddělitelné. Všechny do sebe strategicky zapadají. Obecně se předpokládá, že funkce killer verze jazyka C# byla výraz dotazu, označovaný také jako jazykově integrovaný dotaz (LINQ).

Více nuancí zobrazení zkoumá výraz stromy, lambda výrazy a anonymní typy jako základ, na kterém je vytvořen LINQ. V obou případech však c# 3.0 představil revoluční koncept. C# 3.0 začal položit základy pro soustružení C# do hybridní objektově orientované / funkční jazyk.

Konkrétně nyní můžete psát sql stylu, deklarativní dotazy provádět operace na kolekce, mimo jiné. Namísto psaní `for` smyčky vypočítat průměr seznamu celá čísla, můžete nyní provést stejně jednoduše jako `list.Average()`. Kombinace výrazů dotazu a rozšiřujících metod to vypadalo, jako by tento seznam celých čísel dostal mnohem chytřejší.

Trvalo to, než lidé skutečně pochopili a integrovali koncept, ale postupně to udělali. A teď, o několik let později, kód je mnohem stručnější, jednoduché a funkční.

## <a name="c-version-40"></a>C# verze 4.0

C# verze 4.0, vydané s Visual Studio 2010, by měl těžké době žít až do průkopnický stav verze 3.0. S verzí 3.0, C# posunul jazyk pevně ze stínu Java a do popředí. Jazyk se rychle stával elegantním.

Další verze se představit některé zajímavé nové funkce:

- [Dynamická vazba](../language-reference/builtin-types/reference-types.md)
- [Pojmenované/volitelné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Obecná kovarianta a kontravarianta](../../standard/generics/covariance-and-contravariance.md)
- [Vložené typy interop](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Vložené typy interop zmírnily bolest při nasazení. Obecná kovariance a kontravariance vám dávají větší sílu používat generika, ale jsou trochu akademické a pravděpodobně nejvíce oceňují autoři frameworku a knihovny. Pojmenované a volitelné parametry umožňují eliminovat mnoho přetížení metody a poskytují pohodlí. Ale žádný z těchto rysů jsou přesně paradigma mění.

Hlavním rysem bylo zavedení `dynamic` klíčového slova. Klíčové `dynamic` slovo zavedené do jazyka C# verze 4.0 možnost přepsat kompilátor u psaní v době kompilace. Pomocí klíčového slova dynamic můžete vytvářet konstrukce podobné dynamicky zadávaným jazykům, jako je JavaScript. Můžete vytvořit `dynamic x = "a string"` a pak přidat šest k němu, takže je na runtime vyřešit, co by se mělo stát dál.

Dynamická vazba vám dává potenciál pro chyby, ale také velkou sílu v rámci jazyka.

## <a name="c-version-50"></a>C# verze 5.0

C# verze 5.0, vydané s Visual Studio 2012, byla cílená verze jazyka. Téměř veškeré úsilí pro tuto verzi šlo do jiného průkopnického jazykového konceptu: `async` a `await` model pro asynchronní programování.  Zde je seznam hlavních funkcí:

- [Asynchronní členové](../async.md)
- [Atributy informací o volajícím](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Viz také

- [Projekt kódu: Atributy informací o volajícím v c# 5.0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Atribut informace o volajícím umožňuje snadno načíst informace o kontextu, ve kterém používáte, aniž byste se uchýlili k tunové často používané reflexní kód. Má mnoho využití v diagnostice a protokolování úloh.

Ale `async` `await` a jsou skutečné hvězdy tohoto vydání. Když tyto funkce vyšly v 2012, C# změnil hru znovu pečením asynchrony do jazyka jako prvotřídní účastník. Pokud jste se někdy zabývali dlouhotrvajícími operacemi a implementací webů zpětných volání, pravděpodobně jste tuto jazykovou funkci milovali.

## <a name="c-version-60"></a>C# verze 6.0

S verzemi 3.0 a 5.0 c# přidal hlavní nové funkce v objektově orientovaném jazyce. S verzí 6.0, vydané s Visual Studio 2015, by přejít od dělá dominantní funkce killer a místo toho uvolnit mnoho menších funkcí, které z c# programování produktivnější. Zde jsou některé z nich:

- [Statické importy](./csharp-6.md#using-static)
- [Filtry výjimek](./csharp-6.md#exception-filters)
- [Inicializátory automatických vlastností](./csharp-6.md#auto-property-initializers)
- [Výraz tělesně členy](./csharp-6.md#expression-bodied-function-members)
- [Propagátor null](./csharp-6.md#null-conditional-operators)
- [Interpolace řetězců](./csharp-6.md#string-interpolation)
- [nameof – operátor](./csharp-6.md#the-nameof-expression)
- [Indexinizátory](csharp-6.md#extension-add-methods-in-collection-initializers)

Mezi další nové funkce patří:

- Čekají v catch / finally bloky
- Výchozí hodnoty pro vlastnosti pouze pro získání

Každá z těchto vlastností je zajímavá sama o sobě. Ale když se na ně podíváte úplně, vidíte zajímavý vzorec. V této verzi C# eliminovány standardní text jazyka, aby kód stručnější a čitelnější. Takže pro fanoušky čistého, jednoduchého kódu byla tato jazyková verze obrovskou výhrou.

Udělali ještě jednu věc spolu s touto verzí, i když to není tradiční jazyk funkce sama o sobě. Vydali [Roslyn kompilátor jako službu](https://github.com/dotnet/roslyn). Kompilátor Jazyka C# je nyní zapsán v jazyce C# a kompilátor můžete použít jako součást vašeho programovacího úsilí.

## <a name="c-version-70"></a>C# verze 7.0

Nejnovější hlavní verze je C# verze 7.0, vydané s Visual Studio 2017. Tato verze má některé evoluční a cool věci v žílce C# 6.0, ale bez kompilátoru jako služby. Zde jsou některé z nových funkcí:

- [Out proměnné](./csharp-7.md#out-variables)
- [N-tis a dekonstrukce](./csharp-7.md#tuples)
- [Porovnávání vzorů](./csharp-7.md#pattern-matching)
- [Lokální funkce](./csharp-7.md#local-functions)
- [Rozšířené výraztělesně členy](./csharp-7.md#more-expression-bodied-members)
- [Ref místní obyvatelé a vrací](./csharp-7.md#ref-locals-and-returns)

Mezi další funkce patří:

- [Zahození](./csharp-7.md#discards)
- [Binární literály a oddělovače číslic](./csharp-7.md#numeric-literal-syntax-improvements)
- [Výrazy throw](./csharp-7.md#throw-expressions)

Všechny tyto funkce nabízejí skvělé nové funkce pro vývojáře a možnost psát ještě čistší kód než kdy jindy. Zvýraznění je kondenzace deklarace proměnných pro použití s klíčovým slovem `out` a povolením více vrácených hodnot prostřednictvím řazené kolekce členů.

Ale C# je kladen na stále širší použití. .NET Core nyní cílí na jakýkoli operační systém a má své oči pevně na cloud a na přenositelnost.  Tyto nové schopnosti jistě zabírají myšlenky a čas jazykových designérů, kromě toho, že přicházejí s novými funkcemi.

_Článek_ [_původně publikoval na blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, s laskavým svolením Erik Dietrich a Patrick Smacchia._
