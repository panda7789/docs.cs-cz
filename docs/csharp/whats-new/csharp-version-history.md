---
title: Historie C# – C# Průvodce
description: Co jazyk vypadal jako v jeho dřívějších verzích a jak se vyvinulo od verze?
author: erikdietrich
ms.date: 09/20/2017
ms.openlocfilehash: bce61d7a1838753f6cc2397440208e0c02b8194a
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72002691"
---
# <a name="the-history-of-c"></a>Historie jazyka C @ no__t-0

Tento článek poskytuje historii všech hlavních vydání C# jazyka. Tým C# pokračuje v inovacích a přidává nové funkce. Podrobný stav funkcí jazyka, včetně funkcí, které se považují za nadcházející verze, najdete [v úložišti dotnet/Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) na GitHubu.

> [!IMPORTANT]
> C# Jazyk spoléhá na typy a metody v tom, co C# specifikace definuje jako *standardní knihovnu* pro některé funkce. Platforma .NET poskytuje tyto typy a metody v několika balíčcích. Jedním z příkladů je zpracování výjimek. Je zkontrolován každý příkaz `throw` nebo výraz, aby se zajistilo, že vyvolaný objekt je odvozen z <xref:System.Exception>. Podobně je zkontrolováno každé `catch`, aby byl zachycený typ odvozen od <xref:System.Exception>. Každá verze může přidat nové požadavky. Pokud chcete používat nejnovější funkce jazyka ve starších prostředích, budete možná muset nainstalovat konkrétní knihovny. Tyto závislosti jsou zdokumentovány na stránce pro každou konkrétní verzi. Můžete si přečíst další informace o [relacích mezi jazykem a knihovnou](relationships-between-language-and-library.md) pro pozadí na této závislosti.

Nástroje C# pro sestavení považují nejnovější jazykovou verzi za výchozí verzi. V dalších článcích v této části můžou být vydávané body mezi hlavními vydáními, které jsou podrobně popsané. Chcete-li používat nejnovější funkce v bodu vydání, je nutné [nakonfigurovat verzi jazyka kompilátoru](../language-reference/configure-language-version.md) a vybrat verzi. Od C# 7,0 se vydává tři body:

- [ C# 7,3](csharp-7-3.md):
  - C#7,3 je k dispozici počínaje sadou [Visual Studio 2017 verze 15,7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2,1 SDK](../../core/whats-new/dotnet-core-2-1.md).
- [ C# 7,2](csharp-7-2.md):
  - C#7,2 je k dispozici počínaje sadou [Visual Studio 2017 verze 15,5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md).
- [ C# 7,1](csharp-7-1.md):
  - C#7,1 je k dispozici počínaje sadou [Visual Studio 2017 verze 15,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C#verze 1,0

Až se vrátíte zpátky a provedete C# verzi 1,0, která byla vydána se sadou Visual Studio .NET 2002, vyhledali jsme spoustu jako Java. Jako [součást uvedených cílů návrhu pro ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)se snaží být jednoduchý a moderní objektově orientovaný jazyk pro obecné účely.  V takovém případě, jako by jazyk Java chtěl, dosáhly těchto cílů prvotního návrhu.

Pokud se ale teď o C# 1,0 znovu pokusíte, najdete trochu Dizzy. Neobsahovaly integrované asynchronní funkce a některé funkce uhlazený kolem generických typů, které udělíte pro udělení. Vzhledem k tomu, že ve skutečnosti zcela chyběly obecné typy.  A [LINQ](../linq/index.md)? Ještě není k dispozici. Tyto dodatky budou trvat několik let.

C#verze 1,0 prohlédla z vydaných funkcí v porovnání s dnešním datem. Našli jsme, že píšete nějaký podrobný kód. Ale ještě musíte začít někam. C#verze 1,0 byla životaschopnou alternativou k jazyku Java na platformě Windows.

K dispozici jsou C# hlavní funkce 1,0:

- [Třídy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../programming-guide/classes-and-structs/structs.md)
- [Rozhraní](../programming-guide/interfaces/index.md)
- [Události](../events-overview.md)
- [Vlastnosti](../properties.md)
- [Delegáty](../delegates-overview.md)
- [Výrazy](../programming-guide/statements-expressions-operators/expressions.md)
- [Příkazy](../programming-guide/statements-expressions-operators/statements.md)
- [Atributy](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C#verze 1,2

C#verze 1,2 byla dodávána se sadou Visual Studio .NET 2003. Obsahuje několik malých vylepšení jazyka. Nejvýraznější je, že od této verze kód vygenerovaný ve smyčce `foreach` s názvem <xref:System.IDisposable.Dispose%2A> v <xref:System.Collections.IEnumerator>, pokud <xref:System.Collections.IEnumerator> implementoval <xref:System.IDisposable>.

## <a name="c-version-20"></a>C#verze 2,0

Teď začít s zajímavou možností. Pojďme se podívat na některé hlavní funkce C# 2,0 vydané v 2005, společně se sadou Visual Studio 2005:

- [Obecné typy](../programming-guide/generics/index.md)
- [Částečné typy](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonymní metody](../language-reference/operators/delegate-operator.md)
- [Typy hodnot s možnou hodnotou null](../programming-guide/nullable-types/index.md)
- [Iterátory](../programming-guide/concepts/iterators.md)
- [Kovariance a kontravariance](../programming-guide/concepts/covariance-contravariance/index.md)

Další C# funkce 2,0 přidávané funkcím do existujících funkcí:

- Metody get/set oddělené přístupnosti
- Převody skupin metod (delegáti)
- Statické třídy
- Odvození delegáta

I C# když mohly být spuštěny jako jazyk orientovaný na obecné objekty (ó) C# , verze 2,0 se změnila v Pospěšte si. Po tom, co s nimi mají své nožky, se dostaly po některých vážných problémech pro vývojáře. A zavedly se za ně významnou cestou.

S obecnými typy a metody mohou pracovat s libovolným typem, přičemž stále zachovává bezpečnost typů. Například při použití <xref:System.Collections.Generic.List%601> můžete mít `List<string>` nebo `List<int>` a provádět operace bezpečného typu u těchto řetězců nebo celých čísel při iteracích. Použití generických typů je lepší než vytvoření `ListInt`, které je odvozeno od `ArrayList` nebo přetypování z `Object` pro každou operaci.

C#verze 2,0 přenesla iterátory. Pro stručné vložení iterátorů vám umožní prošetřit všechny položky v `List` (nebo jiných výčtových typech) pomocí smyčky `foreach`. Máte iterátory jako součást jazyka, ve kterém je první třída výrazně rozšířená čitelnost jazyka a možnosti lidí o kódu.

A pořád i C# nadále hraje bitovou kopii, která je zachytávání pomocí Java. Java již vydala verze, které obsahovaly generické typy a iterátory. Ale ty by se brzy změnily, protože jazyky se nadále rozvíjejí.

## <a name="c-version-30"></a>C#verze 3,0

C#verze 3,0 byla uvedena v pozdní 2007 společně se sadou Visual Studio 2008, i když plný člun funkcí jazyka by byl skutečně dodán s .NET Framework verze 3,5. Tato verze označila zásadní změnu ve růstu C#. Vytvořil C# se jako skutečně Formidable programovací jazyk. Pojďme se podívat na některé hlavní funkce v této verzi:

- [Automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
- [Výrazy dotazů](../linq/query-expression-basics.md)
- [Výrazy lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Stromy výrazů](../expression-trees.md)
- [Metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md)
- [Implicitně typované lokální proměnné](../language-reference/keywords/var.md)
- [Částečné metody](../language-reference/keywords/partial-method.md)
- [Inicializátory objektu a kolekce](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Mnohé z těchto funkcí se v když zdají být nevyhnutelné i oddělitelné. Všechno se vejdou do společné strategické spolupráce. Obecně se domníváte, C# že funkce Killer ve verzi byla výraz dotazu, označovaný také jako LINQ (Language-Integrated Query).

Další zobrazení odlišit prověřuje stromy výrazů, výrazy lambda a anonymní typy jako základ, na kterém je technologie LINQ vytvořena. Ale v obou případech se C# 3,0 prezentuje koncept revolučního procesu. C#3,0 bylo zahájeno sezákladyování pro C# přechod k hybridnímu objektu orientovanému na objekt.

Konkrétně byste teď mohli zapisovat do stylů SQL, deklarativní dotazy a provádět operace s kolekcemi mimo jiné věci. Místo psaní smyčky `for` pro výpočet průměru seznamu celých čísel můžete to udělat stejně jako `list.Average()`. Kombinace výrazů dotazů a metod rozšíření se zdá, že se v seznamu celých čísel dostalo celé množství karet.

Čas, kdy lidé skutečně poznamenali a integrují koncept, ale postupně udělali. A teď už roky později je kód mnohem výstižnější, jednoduchý a funkční.

## <a name="c-version-40"></a>C#verze 4,0

C#verze 4,0, vydaná se sadou Visual Studio 2010, by měla obtížný čas na přelomové stav verze 3,0. S verzí 3,0 C# přesunula jazyk pevně od stínu Java a do význačnost. Jazyk se rychle stal elegantním.

Další verze zavedla zajímavé nové funkce:

- [Dynamická vazba](../language-reference/keywords/dynamic.md)
- [Pojmenované/nepovinné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Obecné kovariantní a kontravariantní](../../standard/generics/covariance-and-contravariance.md)
- [Vložené typy spolupráce](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Vložené typy spolupráce zmírnily bolesti nasazení. Obecná kovariance a kontravariance poskytují více možností, jak používat obecné typy, ale jedná se o trochu akademickou a pravděpodobně nejvíc vážíme architekturou a autory knihovny. Pojmenované a volitelné parametry umožňují eliminovat mnoho přetížení metod a poskytovat pohodlí. Ale žádná z těchto funkcí se přesně nemění.

Hlavní funkcí bylo zavedení klíčového slova `dynamic`. Klíčové slovo `dynamic` představené C# do verze 4,0 možnost přepsat kompilátor při psaní při kompilaci. Pomocí klíčového slova Dynamic můžete vytvořit konstrukce podobné dynamickým typovým jazykům, jako je JavaScript. Můžete vytvořit `dynamic x = "a string"` a potom do něj přidat šest, a to tak, že ho zachováte až do modulu runtime, abyste mohli řadit, co by mělo probíhat v dalším.

Dynamická vazba poskytuje potenciál pro chyby, ale také skvělou sílu v rámci jazyka.

## <a name="c-version-50"></a>C#verze 5,0

C#verze 5,0, vydaná v rámci sady Visual Studio 2012, byla zaměřená na verzi tohoto jazyka. Skoro veškerá snaha o tuto verzi přešla do jiného přelomové jazyka: model `async` a `await` pro asynchronní programování.  Tady je seznam hlavních funkcí:

- [Asynchronní členové](../async.md)
- [Atributy informací o volajícím](../programming-guide/concepts/caller-information.md)

### <a name="see-also"></a>Viz také

- [Code Project: atributy informací o volajícím v C# 5,0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Atribut informace o volajícím umožňuje snadno načíst informace o kontextu, ve kterém je spuštěno bez použití na tunu kódu reflexe. Obsahuje mnoho použití v diagnostice a úlohy protokolování.

Ale `async` a `await` jsou reálné hvězdičky této verze. Po vyřazení těchto funkcí v 2012 se C# hra znovu změní tak, že asynchronii do jazyka jako účastníka první třídy. Pokud jste se už seznámili s dlouhou dobou provozu a implementací webů s zpětným voláním, pravděpodobně byste tuto funkci jazyka chtěli očekávat.

## <a name="c-version-60"></a>C#verze 6,0

S verzemi 3,0 a 5,0 C# byly přidány hlavní nové funkce do objektově orientovaného jazyka. S verzí 6,0, která byla vydaná s Visual Studio 2013, by nedošlo k tomu, že by se prováděla dominantní funkce Killer a C# místo toho se uvolnilo mnoho menších funkcí, které přidávají větší produktivitu Tady jsou některé z nich:

- [Statické importy](./csharp-6.md#using-static)
- [Filtry výjimek](./csharp-6.md#exception-filters)
- [Inicializátory automatických vlastností](./csharp-6.md#auto-property-initializers)
- [Členové výrazu těle](./csharp-6.md#expression-bodied-function-members)
- [Šiřitel s hodnotou null](./csharp-6.md#null-conditional-operators)
- [Interpolace řetězců](./csharp-6.md#string-interpolation)
- [nameof – operátor](./csharp-6.md#the-nameof-expression)
- [Inicializátory indexů](csharp-6.md#extension-add-methods-in-collection-initializers)

Mezi další nové funkce patří:

- Očekává se v blocích catch/finally
- Výchozí hodnoty pro vlastnosti jen pro funkci getter

Každá z těchto funkcí je zajímavá a má své právo. Pokud se ale zcela podíváte, zobrazí se zajímavý vzor. V této verzi eliminoval často používaný kód jazyka, C# aby bylo možné zvýšit stručný a čitelnost kódu. Takže pro ventilátory čistého, jednoduchého kódu se jednalo o obrovský soubor Win verze.

Spolu s touto verzí existovaly ještě jiné, ale nejedná se o tradiční jazykovou funkci. Vydali [Roslyn kompilátor jako službu](https://github.com/dotnet/roslyn). C# Kompilátor je nyní napsán v C#a můžete použít kompilátor jako součást snahy o programování.

## <a name="c-version-70"></a>C#verze 7,0

Nejnovější hlavní verze je verze 7,0 C# , která byla vydaná se sadou Visual Studio 2017. Tato verze obsahuje několik vývojových a studených věcí v příplatku C# 6,0, ale bez kompilátoru jako služby. Tady jsou některé nové funkce:

- [Proměnné out](./csharp-7.md#out-variables)
- [Řazené kolekce členů a dekonstrukce](./csharp-7.md#tuples)
- [Porovnávání vzorů](./csharp-7.md#pattern-matching)
- [Lokální funkce](./csharp-7.md#local-functions)
- [Členové rozbaleného výrazu těle](./csharp-7.md#more-expression-bodied-members)
- [Místní a návratové hodnoty REF](./csharp-7.md#ref-locals-and-returns)

K dispozici jsou další funkce:

- [Zahození](./csharp-7.md#discards)
- [Binární literály a oddělovače číslic](./csharp-7.md#numeric-literal-syntax-improvements)
- [Výrazy throw](./csharp-7.md#throw-expressions)

Všechny tyto funkce nabízejí skvělé nové možnosti pro vývojáře a možnost psát ještě čisticí kód než kdy dřív. Zvýraznění je zúžení deklarace proměnných pro použití s klíčovým slovem `out` a povolením více návratových hodnot prostřednictvím řazené kolekce členů.

Ale C# přichází se k ještě širšímu použití. .NET Core teď cílí na libovolný operační systém a jeho oči je pevně na cloudu a na přenositelnosti.  Tyto nové funkce si určitě zabírají myšlenky a čas pro návrháře jazyka, a to i s využitím nových funkcí.

_Článek_ [_původně publikovaný na blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/) _, Erik Dietrich a Smacchia._
