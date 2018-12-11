---
title: F#Průvodce správným stylem
description: Další pět zásadami dobrého F# kódu.
ms.date: 12/10/2018
ms.openlocfilehash: 7718df596bde9004fb9ba6143146f1f475d25683
ms.sourcegitcommit: e6ad58812807937b03f5c581a219dcd7d1726b1d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/10/2018
ms.locfileid: "53168951"
---
# <a name="f-style-guide"></a>F#Průvodce správným stylem

Následující články popisují pokyny pro formátování F# kódu a užitečná pokyny pro funkce jazyka, a způsob jejich použití.

Tento návod byl vydá podle použití F# ve velké základy kódu s různými skupiny programátorů. Tyto pokyny jsou zpravidla vede k úspěšné využívání F# a minimalizuje frustrations při požadavky pro programy v průběhu času měnit.

## <a name="five-principles-of-good-f-code"></a>Pět zásadami dobrého F# kódu

Mějte tyto zásady kdykoli napíšete F# kódu, zejména v systémech, které se v průběhu času měnit. Každá část podle pokynů uvedených v dalších článcích vyplývá z těchto pět bodů.

1. **Dobrý F# kód je stručné, výrazový a sestavitelný**

    F#má řadu funkcí, které vám umožní express akce v míň řádků kódu a opětovné použití obecné funkce. F# Základní knihovna také obsahuje mnoho funkcí pro práci s common kolekce dat a užitečné typy. Složení vašich vlastních funkcích a těm F# základní knihovna (nebo jiných knihovnách) je součástí rutina idiomatickou F# programování. Obecně platí Pokud řešení problému v míň řádků kódu, můžete vyjádřit ostatním vývojářům (nebo budoucí self) bude appreciative. Také důrazně doporučujeme použít knihovnu, jako je například FSharp.Core, [rozsáhlé knihovny .NET](https://docs.microsoft.com/dotnet/api/) , který F# spuštěný, nebo pomocí balíčku třetí strany na [NuGet](https://www.nuget.org/) když potřebujete provést úlohu triviální.

2. **Dobrý F# kód je interoperabilní**

    Vzájemná spolupráce grafického subsystému může trvat více podobách, například používání kódu v různých jazycích. Hranice kódu, které další volající spolupracovat s jsou zásadní pro získání správné, i když volající jsou také v F#. Při zápisu F#, je vždy být uvažujete, o jak jiný kód zavolá do kódu, který píšete, včetně pokud z jiného jazyka, jako je C#. [ F# Pokyny k návrhu komponenty](component-design-guidelines.md) interoperability podrobně popisují.

3. **Dobrý F# kód provede pomocí objektu programování, není objekt orientace**

    F#obsahuje plnou podporu pro programování s objekty v .NET, včetně [třídy](../language-reference/classes.md), [rozhraní](../language-reference/interfaces.md), [modifikátorů přístupu](../language-reference/access-control.md), [abstraktní třídy](../language-reference/abstract-classes.md), a tak dále. Pro složitější funkční kód, jako je například funkce, které musí být kontextově objekty zapouzdřují snadno kontextové informace takovým způsobem, který nelze funkce. Funkce, jako [volitelné parametry](../language-reference/members/methods.md#optional-arguments) a pečlivé použití [přetížení](../language-reference/members/methods.md#overloaded-methods) můžete usnadnit využití této funkce pro volající.

4. **Dobrý F# kód provede správně bez vystavení mutace**

    Není žádný tajný klíč musí používat k psaní kódu, výkonné, mutace. Je počítače fungování, všechny. Takový kód je často náchylné a obtížně získat správný. Vyhněte se vystavení mutace volajícím. Místo toho [vytvoření funkční rozhraní, která skrývá na základě mutace implementace](conventions.md#performance) když je nejdůležitější výkon.

5. **Dobrý F# je jazyk kódu**

    Nástroje jsou nedocenitelné pro práci v velké základy kódu a můžete napsat F# kódu tak, aby ji lze efektivněji s F# nástroje jazyka. Jedním z příkladů je zajistit, že jste nepřežeňte to stylem bodu bez programování, tak, aby mohly být zkontrolovány hodnoty, ležící se ladicí program. Další příklad používá [dokumentační komentáře XML](../language-reference/xml-documentation.md) popisující konstrukce tak, že popisy v editorech může zobrazit tyto komentáře na lokalitu volání. Vždy uvažovat o jak váš kód bude číst, přejde, ladit a manipulovat s jejich nástroje jinými programátory.

## <a name="next-steps"></a>Další kroky

[ F# Pokyny k formátování kódu](formatting.md) pokyny o tom, jak formátovat kód tak, aby byl snadno čitelný.

[ F# Konvence kódování](conventions.md) poskytují pokyny pro F# programovací idiomy, které vám pomůžou dlouhodobou údržbu větší F# základů kódu.

[ F# Pokyny k návrhu komponenty](component-design-guidelines.md) poskytují pokyny k vytváření F# součásti, jako jsou knihovny.
