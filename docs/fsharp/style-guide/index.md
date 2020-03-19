---
title: Příručka stylu jazyka F#
description: Naučte se pět zásad dobrého kódu F#.
ms.date: 12/10/2018
ms.openlocfilehash: 9f47257626e04b09b546de2ae315d48d791678be
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "79400265"
---
# <a name="f-style-guide"></a>Příručka stylu jazyka F#

Následující články popisují pokyny pro formátování kódu F# a aktuální pokyny pro funkce jazyka a jak by měly být použity.

Tento návod byl formulován na základě použití F# ve velkých codebases s různorodou skupinou programátorů. Tento návod obecně vede k úspěšnému použití Jazyka F# a minimalizuje frustrace při změně požadavků na programy v průběhu času.

## <a name="five-principles-of-good-f-code"></a>Pět principů dobrého kódu F#

Mějte na paměti následující zásady při každém psaní kódu F#, zejména v systémech, které se budou v průběhu času měnit. Každý kus návodu v dalších článcích vychází z těchto pěti bodů.

1. **Dobrý kód F# je stručný, expresivní a kompozitelný**

    F# má mnoho funkcí, které umožňují vyjádřit akce v méně řádků kódu a opakovaně používat obecné funkce. Základní knihovna F# také obsahuje mnoho užitečných typů a funkcí pro práci s běžnými kolekcemi dat. Složení vlastních funkcí a funkcí v základní knihovně F# (nebo jiných knihovnách) je součástí rutinního idiomatického programování F#. Obecně platí, že pokud můžete vyjádřit řešení problému v menším počtu řádků kódu, ostatní vývojáři (nebo vaše budoucí já) budou vděčni. Je také důrazně doporučujeme použít knihovnu, jako je FSharp.Core, [rozsáhlé knihovny .NET,](../../../api/index.md) které f# běží na nebo balíček jiného výrobce na [NuGet,](https://www.nuget.org/) když potřebujete provést netriviální úlohu.

2. **Dobrý kód F# je interoperabilní**

    Spolupráce může mít více forem, včetně využití kódu v různých jazycích. Hranice kódu, který ostatní volající spolupracovat s jsou kritické kusy získat správné, i v případě, že volající jsou také v F#. Při psaní F#, měli byste vždy přemýšlet o tom, jak jiný kód bude volat do kódu, který píšete, včetně pokud tak učiní z jiného jazyka, jako je C#. [F# Pokyny pro návrh komponent](component-design-guidelines.md) popisují interoperabilitu podrobně.

3. **Dobrý kód F# využívá programování objektů, nikoli orientaci objektu**

    F# má plnou podporu pro programování s objekty v rozhraní .NET, včetně [tříd](../language-reference/classes.md), [rozhraní](../language-reference/interfaces.md), [modifikátory přístupu](../language-reference/access-control.md), [abstraktní třídy](../language-reference/abstract-classes.md)a tak dále. Pro složitější funkční kód, jako jsou funkce, které musí být kontextové, objekty mohou snadno zapouzdřit kontextové informace způsoby, které funkce nelze. Funkce, jako jsou [volitelné parametry](../language-reference/members/methods.md#optional-arguments) a pečlivé použití [přetížení](../language-reference/members/methods.md#overloaded-methods) může usnadnit spotřebu této funkce pro volající.

4. **Dobrý Kód F# funguje dobře bez vystavení mutace**

    Není žádným tajemstvím, že k napsání vysoce výkonného kódu musíte použít mutaci. Je to o tom, jak počítače fungují, po tom všem. Takový kód je často náchylný k chybám a je obtížné se správně dostat. Vyhněte se vystavení mutace volajícím. Místo toho [vytvořte funkční rozhraní, které skryje implementaci založenou na mutaci,](conventions.md#performance) když je důležitý výkon.

5. **Dobrý kód F# je použitelný pro nástroje**

    Nástroje jsou neocenitelné pro práci ve velkých codebases a můžete napsat F# kód tak, aby jej lze použít efektivněji s nástroji jazyka F#. Jedním z příkladů je ujistěte se, že není přehánět s bezbodový styl programování, tak, aby mezilehlé hodnoty mohou být kontrolovány s ladicím programem. Dalším příkladem je použití [komentáře dokumentace XML](../language-reference/xml-documentation.md) popisující konstrukce tak, že popisky v editorech můžete zobrazit tyto komentáře na webu volání. Vždy přemýšlejte o tom, jak bude váš kód číst, navigovat, ladit a manipulovat s jinými programátory pomocí jejich nástrojů.

## <a name="next-steps"></a>Další kroky

Pokyny [pro formátování kódu Jazyka F#](formatting.md) poskytují pokyny pro formátování kódu tak, aby byl snadno čitelný.

[Konvence kódování F#](conventions.md) poskytují pokyny pro f# programovací idiomy, které pomohou dlouhodobé údržby větší chrápání kódu F#.

[Pokyny pro návrh komponent y F#](component-design-guidelines.md) poskytují pokyny pro vytváření součástí F#, jako jsou například knihovny.
