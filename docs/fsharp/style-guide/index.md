---
title: 'Průvodci správným stylem F #'
description: 'Přečtěte si pět zásady dobrý F # – kód.'
ms.date: 05/14/2018
ms.openlocfilehash: 6d8c1336ca991040a8f6e13290d209cb3b70054d
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/17/2018
ms.locfileid: "34235902"
---
# <a name="f-style-guide"></a>Průvodci správným stylem F #

Následující články popisují pokyny pro formátování F # – kód a užitečná pokyny pro funkce jazyka a jak mají být použity.

V tomto návodu se vydá na základě pomocí jazyka F # ve velkých základy kódu pomocí různých skupina programátorů. V tomto návodu obvykle vede k úspěšné použití F # a minimalizuje frustrations při změně požadavků programů v průběhu času.

## <a name="five-principles-of-good-f-code"></a>Pět principů dobrý F # – kód

Tyto zásady měli mít na paměti, když napíšete F # – kód, zejména v systémech, které se časem změnit. Každá část pokyny v další články vyplývá z těchto pět bodů.

1. **Dobrý F # – kód je stručného a výrazové**

    F # obsahuje mnoho funkcí, které vám umožní express akce méně řádků kódu a opakovaně používat obecné funkce. Základní knihovny F # také obsahuje mnoho funkcí pro práci s běžné kolekcí dat a užitečné typy. Obecně platí Pokud lze vyjádřit řešení problému v méně řádků kódu, jinými vývojáři (nebo vaše budoucí samoobslužné) bude zásadní. Také důrazně doporučujeme používat knihovnu, jako je například FSharp.Core, [velká knihovny .NET](https://docs.microsoft.com/dotnet/api/) F # kompatibilní, nebo jiných výrobců balíčku na [NuGet](https://www.nuget.org/) když potřebujete provést úlohu triviální.

2. **Dobrý F # – kód je umožňuje vzájemnou spolupráci**

    Vzájemná spolupráce může trvat více formulářů, včetně použití kódu v různých jazycích. Hranice vaší kód, který jiných volající spolupracovat s jsou kritické části získat správné. Při zápisu F #, jste měli vždy přemýšlíte o tom, jak jiný kód zavolá do kódu, který vytváříte, včetně, pokud k tomu mohou z jiný jazyk, jako je C#. [F # součást pokynů pro návrh](component-design-guidelines.md) interoperabilita podrobně popisují.

3. **Dobrý F # – kód umožňuje použít objekt programování, není objekt orientace**

    F # má plnou podporu pro programování s objekty v rozhraní .NET, včetně [třídy](../language-reference/classes.md), [rozhraní](../language-reference/interfaces.md), [přístup modifikátory](../language-reference/access-control.md), [abstraktní třídy](../language-reference/abstract-classes.md)a tak dále. Pro složitější funkční kód, jako je například funkce, které musí kontext myslet objekty zapouzdřují snadno kontextové informace způsoby, které nelze funkce. Funkce, jako [volitelné parametry](../language-reference/members/methods.md#optional-arguments) a [přetížení](../language-reference/members/methods.md#overloaded-methods) také pomáhají energie tuto funkčnost pro volající.

4. **Dobrý F # – kód provede i bez vystavení mutace**

    Je žádné tajný klíč, že napsat kód, vysoce výkonné, je nutné použít mutace. Je, jak počítače fungují, po všech. Takový kód, je často náchylné a obtížně se získat správné. Vyhněte se vystavení mutace pro volající. Hledat přes implementací na základě mutace rozhraní je funkční.

5. **Dobrý F # – kód je jazyk**

    Pro práci v velké základy kódu jsou neocenitelnou pomocí nástroje, můžete napsat kód F # tak, aby se dá použít efektivněji s nástrojů jazyka F #. Jedním z příkladů je Ujistěte se, že jste nemáte by ho s styl bez bodu programování, tak, aby mohly být zkontrolovány pomocných hodnot s ladicí program. Dalším příkladem je pomocí [dokumentační komentáře XML](../language-reference/xml-documentation.md) popisující konstrukce tak, aby popisů tlačítek v editory můžete zobrazit tyto komentáře v lokalitě volání. Vždy vezměte v úvahu jak váš kód bude číst, navigaci, ladit a s nimi manipulovat, jinými programátory jejich nástroje.

## <a name="next-steps"></a>Další kroky

[F # – kód formátování pokyny](formatting.md) poskytovat pokyny k formátování kódu tak, aby se snadno čitelný.

[F # – konvence kódování](conventions.md) poskytuje pokyny pro programovací idioms, které vám pomůžou dlouhodobé údržby větší F # F # základy kódu.

[F # součást pokynů pro návrh](component-design-guidelines.md) obsahují pokyny pro vytváření F # komponenty, například knihovny.
