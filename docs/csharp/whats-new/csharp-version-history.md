---
title: Historie příručky C#-C#
description: Co jazyk vypadal jako v jeho dřívějších verzích a jak se vyvinulo od verze?
author: erikdietrich
ms.date: 04/08/2020
ms.openlocfilehash: 96d6e07d5553d65e95144a0cede7cab86b4c5ef7
ms.sourcegitcommit: b7a8b09828bab4e90f66af8d495ecd7024c45042
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/04/2020
ms.locfileid: "87556850"
---
# <a name="the-history-of-c"></a>Historie jazyka C\#

Tento článek poskytuje historii všech hlavních vydání jazyka C#. Tým C# pokračuje v inovacích a přidává nové funkce. Podrobný stav funkcí jazyka, včetně funkcí, které se považují za nadcházející verze, najdete [v úložišti dotnet/Roslyn](https://github.com/dotnet/roslyn/blob/master/docs/Language%20Feature%20Status.md) na GitHubu.

> [!IMPORTANT]
> Jazyk C# spoléhá na typy a metody v tom, co specifikace jazyka C# definuje jako *standardní knihovnu* pro některé funkce. Platforma .NET poskytuje tyto typy a metody v několika balíčcích. Jedním z příkladů je zpracování výjimek. Každý `throw` příkaz nebo výraz je zkontrolován, aby bylo zajištěno, že objekt, který je vyvolán, je odvozen z <xref:System.Exception> . Podobně každé je zaškrtnuto, aby byl `catch` zachycený typ odvozen od <xref:System.Exception> . Každá verze může přidat nové požadavky. Pokud chcete používat nejnovější funkce jazyka ve starších prostředích, budete možná muset nainstalovat konkrétní knihovny. Tyto závislosti jsou zdokumentovány na stránce pro každou konkrétní verzi. Můžete si přečíst další informace o [relacích mezi jazykem a knihovnou](relationships-between-language-and-library.md) pro pozadí na této závislosti.

Nástroje pro sestavení v jazyce C# považují nejnovější verzi jazykové verze za nejnovější hlavní jazykovou verzi. V dalších článcích v této části můžou být vydávané body mezi hlavními vydáními, které jsou podrobně popsané. Chcete-li používat nejnovější funkce v bodu vydání, je nutné [nakonfigurovat verzi jazyka kompilátoru](../language-reference/configure-language-version.md) a vybrat verzi. Od verze C# 7,0 byly tři body:

- [C# 7,3](csharp-7-3.md):
  - C# 7,3 je k dispozici počínaje [verzí Visual Studio 2017 15,7](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2,1 SDK](../../core/whats-new/dotnet-core-2-1.md).
- [C# 7,2](csharp-7-2.md):
  - C# 7,2 je k dispozici počínaje [verzí Visual Studio 2017 15,5](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md).
- [C# 7,1](csharp-7-1.md):
  - C# 7,1 je k dispozici počínaje [verzí Visual Studio 2017 15,3](https://visualstudio.microsoft.com/vs/?utm_medium=microsoft&utm_source=docs.microsoft.com&utm_campaign=inline+link) a [.NET Core 2,0 SDK](../../core/whats-new/dotnet-core-2-0.md).

## <a name="c-version-10"></a>C# verze 1,0

Až se vrátíte zpátky a uvidíte C# verze 1,0, které byly vydány s Visual Studio .NET 2002, vyhledaly spoustu jako Java. Jako [součást uvedených cílů návrhu pro ECMA](https://feeldotneteasy.blogspot.com/2011/01/c-design-goals.html)se snaží být jednoduchý a moderní objektově orientovaný jazyk pro obecné účely.  V takovém případě, jako by jazyk Java chtěl, dosáhly těchto cílů prvotního návrhu.

Pokud se ale teď v C# 1,0 vrátíte, můžete najít trochu Dizzy. Neobsahovaly integrované asynchronní funkce a některé funkce uhlazený kolem generických typů, které udělíte pro udělení. Vzhledem k tomu, že ve skutečnosti zcela chyběly obecné typy.  A [LINQ](../linq/index.md)? Ještě není k dispozici. Tyto dodatky budou trvat několik let.

C# verze 1,0 prohlédla všechny funkce ve srovnání s dnešním datem. Našli jsme, že píšete nějaký podrobný kód. Ale ještě musíte začít někam. C# verze 1,0 byla životaschopná alternativa k jazyku Java na platformě Windows.

K dispozici jsou hlavní funkce C# 1,0:

- [Třídy](../programming-guide/classes-and-structs/classes.md)
- [Struktury](../language-reference/builtin-types/struct.md)
- [Rozhraní](../programming-guide/interfaces/index.md)
- [Události](../events-overview.md)
- [Vlastnosti](../properties.md)
- [Delegáti](../delegates-overview.md)
- [Operátory a výrazy](../language-reference/operators/index.md)
- [Příkazy](../programming-guide/statements-expressions-operators/statements.md)
- [Atributy](../programming-guide/concepts/attributes/index.md)

## <a name="c-version-12"></a>C# verze 1,2

C# verze 1,2 byla dodávána se sadou Visual Studio .NET 2003. Obsahuje několik malých vylepšení jazyka. Nejvýraznější je, že počínaje touto verzí kód vygenerovaný ve smyčce, která je `foreach` volána v <xref:System.IDisposable.Dispose%2A> <xref:System.Collections.IEnumerator> případě, kdy je <xref:System.Collections.IEnumerator> implementován <xref:System.IDisposable> .

## <a name="c-version-20"></a>C# verze 2,0

Teď začít s zajímavou možností. Pojďme se podívat na některé hlavní funkce C# 2,0 vydané v 2005, společně se sadou Visual Studio 2005:

- [Obecné typy](../programming-guide/generics/index.md)
- [Částečné typy](../programming-guide/classes-and-structs/partial-classes-and-methods.md#partial-classes)
- [Anonymní metody](../language-reference/operators/delegate-operator.md)
- [Typy hodnot s povolenou hodnotou Null](../language-reference/builtin-types/nullable-value-types.md)
- [Iterátory](../programming-guide/concepts/iterators.md)
- [Kovariance a kontravariance](../programming-guide/concepts/covariance-contravariance/index.md)

Další funkce C# 2,0 přidávají funkce existujícím funkcím:

- Metody get/set oddělené přístupnosti
- Převody skupin metod (delegáti)
- Statické třídy
- Odvození delegáta

Zatímco C# může být spuštěno jako jazyk orientovaný na obecné objekty (ó), C# verze 2,0 se změnila v Pospěšte si. Po tom, co s nimi mají své nožky, se dostaly po některých vážných problémech pro vývojáře. A zavedly se za ně významnou cestou.

S obecnými typy a metody mohou pracovat s libovolným typem, přičemž stále zachovává bezpečnost typů. Například v případě, že máte na <xref:System.Collections.Generic.List%601> `List<string>` `List<int>` těchto řetězcích nebo celých číslech k dispozici operace bezpečného typu, a při iteraci je provedete. Použití generických typů je lepší než vytváření `ListInt` , které je odvozeno od `ArrayList` nebo přetypování `Object` pro každou operaci.

V jazyce C# verze 2,0 byly vyvolané iterátory. Pro stručné vložení iterátorů vám umožní prošetřit všechny položky v `List` (nebo jiných výčtových typech) `foreach` smyčkou. Máte iterátory jako součást jazyka, ve kterém je první třída výrazně rozšířená čitelnost jazyka a možnosti lidí o kódu.

A v C# ještě dál hraje bit pro zachycení pomocí Java. Java již vydala verze, které obsahovaly generické typy a iterátory. Ale ty by se brzy změnily, protože jazyky se nadále rozvíjejí.

## <a name="c-version-30"></a>C# verze 3,0

Jazyk C# verze 3,0 byl dodán v pozdní 2007 společně se sadou Visual Studio 2008, i když plný člun funkcí v současnosti přináší .NET Framework verze 3,5. Tato verze označila zásadní změnu ve růstu jazyka C#. Navázal C# jako skutečně Formidable programovací jazyk. Pojďme se podívat na některé hlavní funkce v této verzi:

- [Automaticky implementované vlastnosti](../programming-guide/classes-and-structs/auto-implemented-properties.md)
- [Anonymní typy](../programming-guide/classes-and-structs/anonymous-types.md)
- [Výrazy dotazů](../linq/query-expression-basics.md)
- [Výrazy lambda](../programming-guide/statements-expressions-operators/lambda-expressions.md)
- [Stromy výrazů](../expression-trees.md)
- [Metody rozšíření](../programming-guide/classes-and-structs/extension-methods.md)
- [Implicitně typované lokální proměnné](../language-reference/keywords/var.md)
- [Částečné metody](../language-reference/keywords/partial-method.md)
- [Inicializátory objektu a kolekce](../programming-guide/classes-and-structs/object-and-collection-initializers.md)

Mnohé z těchto funkcí se v když zdají být nevyhnutelné i oddělitelné. Všechno se vejdou do společné strategické spolupráce. Obecně se domníváme, že funkce Killer verze C# byla výraz dotazu, označovaný také jako LINQ (Language-Integrated Query).

Další zobrazení odlišit prověřuje stromy výrazů, výrazy lambda a anonymní typy jako základ, na kterém je technologie LINQ vytvořena. V obou případech však C# 3,0 prezentuje koncept revolučního procesu. Jazyk c# 3,0 začal rozvrhnout základy pro převod jazyka C# do hybridního nebo funkčního jazyka.

Konkrétně byste teď mohli zapisovat do stylů SQL, deklarativní dotazy a provádět operace s kolekcemi mimo jiné věci. Místo psaní `for` smyčky pro výpočet průměru seznamu celých čísel byste teď mohli udělat stejně jako `list.Average()` . Kombinace výrazů dotazů a metod rozšíření se zdá, že se v seznamu celých čísel dostalo celé množství karet.

Čas, kdy lidé skutečně poznamenali a integrují koncept, ale postupně udělali. A teď už roky později je kód mnohem výstižnější, jednoduchý a funkční.

## <a name="c-version-40"></a>C# verze 4,0

Jazyk C# verze 4,0, vydaný se sadou Visual Studio 2010, by měl obtížný čas na stav přelomové verze 3,0. S verzí 3,0 C# přesunula jazyk pevně od stínu Java a do význačnost. Jazyk se rychle stal elegantním.

Další verze zavedla zajímavé nové funkce:

- [Dynamická vazba](../language-reference/builtin-types/reference-types.md)
- [Pojmenované/nepovinné argumenty](../programming-guide/classes-and-structs/named-and-optional-arguments.md)
- [Obecné kovariantní a kontravariantní](../../standard/generics/covariance-and-contravariance.md)
- [Vložené typy spolupráce](../../framework/interop/type-equivalence-and-embedded-interop-types.md)

Vložené typy spolupráce zmírnily bolesti nasazení. Obecná kovariance a kontravariance poskytují více možností, jak používat obecné typy, ale jedná se o trochu akademickou a pravděpodobně nejvíc vážíme architekturou a autory knihovny. Pojmenované a volitelné parametry umožňují eliminovat mnoho přetížení metod a poskytovat pohodlí. Ale žádná z těchto funkcí se přesně nemění.

Hlavní funkcí bylo zavedení `dynamic` klíčového slova. Klíčové slovo, které je `dynamic` představeno v jazyce C# verze 4,0, schopnost přepsat kompilátor při psaní v době kompilace. Pomocí klíčového slova Dynamic můžete vytvořit konstrukce podobné dynamickým typovým jazykům, jako je JavaScript. Můžete vytvořit `dynamic x = "a string"` a přidat do něj šest a potom do něj přidat šest, aby bylo možné vyřadit, co by mělo probíhat v dalším kroku.

Dynamická vazba poskytuje potenciál pro chyby, ale také skvělou sílu v rámci jazyka.

## <a name="c-version-50"></a>C# verze 5,0

Verze jazyka C# 5,0, vydaná v rámci sady Visual Studio 2012, byla zaměřená na verzi tohoto jazyka. Skoro veškerá snaha o tuto verzi přešla do jiného přelomové jazyka: `async` `await` model a pro asynchronní programování.  Tady je seznam hlavních funkcí:

- [Asynchronní členové](../async.md)
- [Atributy informací o volajícím](../language-reference/attributes/caller-information.md)

### <a name="see-also"></a>Viz také

- [Code Project: atributy volajících informací v C# 5,0](https://www.codeproject.com/Tips/606379/Caller-Info-Attributes-in-Csharp)

Atribut informace o volajícím umožňuje snadno načíst informace o kontextu, ve kterém je spuštěno bez použití na tunu kódu reflexe. Obsahuje mnoho použití v diagnostice a úlohy protokolování.

Ale `async` `await` jsou to reálné hvězdičky této verze. V případě, že jsou tyto funkce vydány v 2012, C# ji znovu změnila pomocí funkce pečení asynchronii do jazyka jako účastníka první třídy. Pokud jste se už seznámili s dlouhou dobou provozu a implementací webů s zpětným voláním, pravděpodobně byste tuto funkci jazyka chtěli očekávat.

## <a name="c-version-60"></a>C# verze 6,0

V případě verzí 3,0 a 5,0 byly v jazyce C# přidány hlavní nové funkce do objektově orientovaného jazyka. S verzí 6,0, které byly vydány společně se sadou Visual Studio 2015, by nedošlo k tomu, že by se prováděla dominantní funkce Killer a místo toho se využívala spousta menších funkcí, které program C# Tady jsou některé z nich:

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

Každá z těchto funkcí je zajímavá a má své právo. Pokud se ale zcela podíváte, zobrazí se zajímavý vzor. V této verzi neodstraní často používaný kód jazyka C# k tomu, aby se kód stručný a čitelnější. Takže pro ventilátory čistého, jednoduchého kódu se jednalo o obrovský soubor Win verze.

Spolu s touto verzí existovaly ještě jiné, ale nejedná se o tradiční jazykovou funkci. Vydali [Roslyn kompilátor jako službu](https://github.com/dotnet/roslyn). Kompilátor jazyka C# je nyní napsán v jazyce C# a můžete použít kompilátor jako součást snahy o programování.

## <a name="c-version-70"></a>C# verze 7,0

Jazyk C# verze 7,0 byl vydán v rámci sady Visual Studio 2017. Tato verze obsahuje některé z vývoje a studených věcí v případě C# 6,0, ale bez kompilátoru jako služby. Tady jsou některé nové funkce:

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

Všechny tyto funkce nabízejí skvělé nové možnosti pro vývojáře a možnost psát ještě čisticí kód než kdy dřív. Zvýraznění je zúžení deklarace proměnných pro použití s `out` klíčovým slovem a povolením více návratových hodnot prostřednictvím řazené kolekce členů.

Ale jazyk C# se přidávají do stále širšího použití. .NET Core teď cílí na libovolný operační systém a jeho oči je pevně na cloudu a na přenositelnosti.  Tyto nové funkce si určitě zabírají myšlenky a čas pro návrháře jazyka, a to i s využitím nových funkcí.

## <a name="c-version-71"></a>C# verze 7,1

V jazyce c# bylo zahájeno *vydání Release Point* s jazykem C# 7,1. Tato verze přidala prvek konfigurace [výběru jazykové verze](../language-reference/configure-language-version.md) , tři nové funkce jazyka a nové chování kompilátoru.

Nové funkce jazyka v této verzi jsou:

- [`async``Main`Metoda](./csharp-7-1.md#async-main)
  - Vstupní bod aplikace může mít `async` modifikátor.
- [`default`literálové výrazy](./csharp-7-1.md#default-literal-expressions)
  - Můžete použít výchozí literálové výrazy ve výchozích hodnotových výrazech, pokud cílový typ lze odvodit.
- [Odvozené názvy elementů řazené kolekce členů](./csharp-7-1.md#inferred-tuple-element-names)
  - Názvy prvků řazené kolekce členů lze odvodit z inicializace řazené kolekce členů v mnoha případech.
- [Porovnávání vzorů v parametrech obecného typu](./csharp-7-1.md#pattern-matching-on-generic-type-parameters)
  - Můžete použít výrazy porovnávání vzorů u proměnných, jejichž typ je parametr obecného typu.

Nakonec má kompilátor dvě možnosti `-refout` a odkaz na `-refonly` [generování sestavení odkazu](./csharp-7-1.md#reference-assembly-generation).

## <a name="c-version-72"></a>C# verze 7,2

C# 7,2 přidalo několik funkcí malých jazyků:

- [Techniky pro psaní bezpečného efektivního kódu](./csharp-7-2.md#safe-efficient-code-enhancements)
  - Kombinace vylepšení syntaxe, která umožňuje práci s typy hodnot pomocí sémantiky odkazů.
- [Nekoncové pojmenované argumenty](./csharp-7-2.md#non-trailing-named-arguments)
  - Pojmenované argumenty mohou následovat Poziční argumenty.
- [Počáteční podtržítka v numerických literálech](./csharp-7-2.md#leading-underscores-in-numeric-literals)
  - Číselné literály teď můžou mít počáteční podtržítka před všemi vytištěnými číslicemi.
- [`private protected`modifikátor přístupu](./csharp-7-2.md#private-protected-access-modifier)
  - `private protected`Modifikátor přístupu umožňuje přístup pro odvozené třídy ve stejném sestavení.
- [Podmíněné `ref` výrazy](./csharp-7-2.md#conditional-ref-expressions)
  - Výsledek podmíněného výrazu ( `?:` ) nyní může být odkazem.

## <a name="c-version-73"></a>C# verze 7,3

K vydání verze C# 7,3 existují dva hlavní motivy. Jeden motiv nabízí funkce, které umožňují bezpečný kód jako nezabezpečený kód. Druhý motiv nabízí přírůstková vylepšení existujících funkcí. Kromě toho se v této verzi přidaly nové možnosti kompilátoru.

Následující nové funkce podporují motiv s lepším výkonem pro bezpečný kód:

- [Můžete získat přístup k pevným polím bez připnutí.](csharp-7-3.md#indexing-fixed-fields-does-not-require-pinning)
- [Můžete změnit přiřazení `ref` místních proměnných.](csharp-7-3.md#ref-local-variables-may-be-reassigned)
- [Můžete použít inicializátory u `stackalloc` polí.](csharp-7-3.md#stackalloc-arrays-support-initializers)
- [Můžete použít `fixed` příkazy s jakýmkoli typem, který podporuje vzor.](csharp-7-3.md#more-types-support-the-fixed-statement)
- [Můžete použít další obecná omezení.](csharp-7-3.md#enhanced-generic-constraints)

V existujících funkcích byly provedeny následující vylepšení:

- [Můžete testovat `==` a `!=` s typy řazené kolekce členů.](csharp-7-3.md#tuples-support--and-)
- [Proměnné výrazu můžete použít ve více umístěních.](csharp-7-3.md#extend-expression-variables-in-initializers)
- [Můžete přiřazovat atributy k poli pro zálohování s automaticky implementovanými vlastnostmi.](csharp-7-3.md#attach-attributes-to-the-backing-fields-for-auto-implemented-properties)
- [Řešení metody, když se liší argumenty, které `in` byly vylepšeny.](csharp-7-3.md#in-method-overload-resolution-tiebreaker)
- [Řešení přetížení teď má méně dvojznačných případů.](csharp-7-3.md#improved-overload-candidates)

Nové možnosti kompilátoru:

- [`-publicsign`povolení podepisování softwaru open source (OSS) pro sestavení.](csharp-7-3.md#public-or-open-source-signing)
- [`-pathmap`pro poskytnutí mapování pro zdrojové adresáře.](csharp-7-3.md#pathmap)

## <a name="c-version-80"></a>C# verze 8,0

C# 8,0 je první hlavní verze v jazyce C#, která cílí konkrétně na rozhraní .NET Core. Některé funkce spoléhají na nové funkce CLR, ostatní na typech knihoven přidaných pouze v .NET Core. C# 8,0 přidává následující funkce a vylepšení jazyka C#:

- [Členové jen pro čtení](./csharp-8.md#readonly-members)
- [Výchozí metody rozhraní](./csharp-8.md#default-interface-methods)
- [Vylepšení porovnávání vzorů](./csharp-8.md#more-patterns-in-more-places):
  - [Výrazy Switch](./csharp-8.md#switch-expressions)
  - [Vzory vlastností](./csharp-8.md#property-patterns)
  - [Vzory řazené kolekce členů](./csharp-8.md#tuple-patterns)
  - [Poziční vzory](./csharp-8.md#positional-patterns)
- [Používání deklarací](./csharp-8.md#using-declarations)
- [Statické místní funkce](./csharp-8.md#static-local-functions)
- [Struktury odkazů na jedno použití](./csharp-8.md#disposable-ref-structs)
- [Odkazové typy s možnou hodnotou null](../language-reference/builtin-types/nullable-reference-types.md)
- [Asynchronní proudy](./csharp-8.md#asynchronous-streams)
- [Indexy a rozsahy](./csharp-8.md#indices-and-ranges)
- [Přiřazení slučování s hodnotou null](./csharp-8.md#null-coalescing-assignment)
- [Nespravované konstruované typy](./csharp-8.md#unmanaged-constructed-types)
- [Stackalloc ve vnořených výrazech](./csharp-8.md#stackalloc-in-nested-expressions)
- [Vylepšení interpolované doslovného řetězce](./csharp-8.md#enhancement-of-interpolated-verbatim-strings)

Výchozí členové rozhraní vyžadují vylepšení v modulu CLR. Tyto funkce byly přidány v modulu CLR pro .NET Core 3,0. Rozsahy a indexy a asynchronní datové proudy vyžadují nové typy v knihovnách .NET Core 3,0. Odkazové typy s možnou hodnotou null, při implementaci v kompilátoru, jsou mnohem užitečnější, pokud jsou knihovny opatřeny poznámkami, aby poskytovaly sémantické informace týkající se nulového stavu argumentů a vrácených hodnot. Tyto poznámky se přidávají do knihoven .NET Core.

_Článek_ [_původně publikovaný na blogu NDepend_](https://blog.ndepend.com/c-versions-look-language-history/)_, Erik Dietrich a Smacchia._
