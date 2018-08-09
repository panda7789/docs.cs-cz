---
title: 'Průvodce správným stylem F #'
description: 'Dozvíte se pět zásady dobré kódu jazyka F #.'
ms.date: 05/14/2018
ms.openlocfilehash: 6d8c1336ca991040a8f6e13290d209cb3b70054d
ms.sourcegitcommit: 78bcb629abdbdbde0e295b4e81f350a477864aba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/08/2018
ms.locfileid: "34235902"
---
# <a name="f-style-guide"></a>Průvodce správným stylem F #

Následující články popisují pokyny pro formátování kódu jazyka F # a užitečná doprovodné materiály pro funkce jazyka, a způsob jejich použití.

Tento návod byl vydá na základě použití jazyka F # ve velkých základů kódu se skupinou různorodé programátorů. Tyto doprovodné materiály obvykle vede k úspěšné použití jazyka F # a minimalizuje frustrations při požadavky pro programy v průběhu času měnit.

## <a name="five-principles-of-good-f-code"></a>Pět zásady dobré kódu jazyka F #

Byste měli zachovat těchto zásad v úvahu pokaždé, když napíšete kód F #, zejména v systémech, které se v průběhu času měnit. Každá část podle pokynů uvedených v dalších článcích vyplývá z těchto pět bodů.

1. **Dobré kódu jazyka F # je stručné a expresivní**

    F # obsahuje mnoho funkcí, které vám umožní express akce v míň řádků kódu a opětovné použití obecné funkce. Základní knihovny F # obsahuje také mnoho funkcí pro práci s common kolekce dat a užitečné typy. Obecně platí Pokud řešení problému v míň řádků kódu, můžete vyjádřit ostatním vývojářům (nebo budoucí self) bude appreciative. Také důrazně doporučujeme použít knihovnu, jako je například FSharp.Core, [rozsáhlé knihovny .NET](https://docs.microsoft.com/dotnet/api/) používající F #, nebo pomocí balíčku třetí strany na [NuGet](https://www.nuget.org/) když potřebujete provést úlohu triviální.

2. **Interoperabilní je dobré kódu jazyka F #**

    Vzájemná spolupráce grafického subsystému může trvat více podobách, například používání kódu v různých jazycích. Hranice kódu, které další volající spolupracovat s jsou zásadní pro získání správné. Při zápisu F #, jste by měla vždy vás napadne, o jak jiný kód zavolá do kódu, který vytváříte, včetně pokud z jiného jazyka, jako je C#. [Pokyny pro návrh komponentu F #](component-design-guidelines.md) interoperability podrobně popisují.

3. **Dobré F # kód provede pomocí objektu programování, není objekt orientace**

    F # obsahuje plnou podporu pro programování s objekty v .NET, včetně [třídy](../language-reference/classes.md), [rozhraní](../language-reference/interfaces.md), [modifikátorů přístupu](../language-reference/access-control.md), [abstraktní třídy](../language-reference/abstract-classes.md), a tak dále. Pro složitější funkční kód, jako je například funkce, které musí být kontextově objekty zapouzdřují snadno kontextové informace takovým způsobem, který nelze funkce. Funkce, jako [volitelné parametry](../language-reference/members/methods.md#optional-arguments) a pečlivé použití [přetížení](../language-reference/members/methods.md#overloaded-methods) můžete usnadnit využití této funkce pro volající.

4. **Dobré kódu jazyka F # provede i bez vystavení mutace**

    Není žádný tajný klíč musí používat k psaní kódu, výkonné, mutace. Je počítače fungování, všechny. Takový kód je často náchylné a obtížně získat správný. Vyhněte se vystavení mutace volajícím. Místo toho [vytvoření funkční rozhraní, která skrývá na základě mutace implementace](conventions.md#performance) když je nejdůležitější výkon.

5. **Dobré kódu jazyka F # je jazyk**

    Nástroje jsou nedocenitelné pro práci v velkých základů kódu, a tak, aby ji lze efektivněji pomocí nástrojů jazyka F # můžete napsat kód F #. Jedním z příkladů je zajistit, že jste nepřežeňte to stylem bodu bez programování, tak, aby mohly být zkontrolovány hodnoty, ležící se ladicí program. Další příklad používá [dokumentační komentáře XML](../language-reference/xml-documentation.md) popisující konstrukce tak, že popisy v editorech může zobrazit tyto komentáře na lokalitu volání. Vždy uvažovat o jak váš kód bude číst, přejde, ladit a manipulovat s jejich nástroje jinými programátory.

## <a name="next-steps"></a>Další kroky

[Kódu jazyka F # pokyny k formátování](formatting.md) pokyny o tom, jak formátovat kód tak, aby byl snadno čitelný.

[F # konvence kódování](conventions.md) obsahují pokyny pro F # programovací idiomy, které vám pomůžou dlouhodobé údržby větší F # základů kódu.

[Pokyny pro návrh komponentu F #](component-design-guidelines.md) poskytují pokyny k vytváření F # součásti, jako jsou knihovny.
