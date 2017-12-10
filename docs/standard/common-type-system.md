---
title: "Obecný systém typů & Common Language Specification"
description: "Zjistěte, jak běžné typ systému (CTS) a specifikace CLS (Common Language) umožňují pro .NET pro podporu více jazyků."
keywords: "Rozhraní .NET, .NET core"
author: blackdwarf
ms.author: mairaw
ms.date: 06/20/2016
ms.topic: article
ms.prod: .net
ms.technology: dotnet-standard
ms.devlang: dotnet
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: 7f92dd26def56deacb24de37fb7f23f79799d20a
ms.sourcegitcommit: 685143b62385500f59bc36274b8adb191f573a16
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/09/2017
---
# <a name="common-type-system--common-language-specification"></a>Obecný systém typů & Common Language Specification

Znovu dva termíny, které jsou volně používat na světě .NET ve skutečnosti jsou velmi důležité, abyste pochopili, jak implementace rozhraní .NET umožňuje vývoj vícejazyčné a pochopit, jak funguje.

## <a name="common-type-system"></a>Obecný systém typů

Chcete-li začít od začátku, mějte na paměti, že je implementace rozhraní .NET _bez ohledu na jazyk_. Právě to však neznamená, že může být z programátorem zapsat v libovolném jazyce, který může být sestaven svůj kód do IL. Taky to znamená, že uživatel musí být moci pracovat s kód napsaný v jiných jazycích, které jsou možné na implementaci rozhraní .NET.

Pokud to chcete provést transparentně, musí být běžný způsob popisují všechny podporované typy. Toto je co běžné typ systému (CTS) má na starosti dělat. Došlo k několika způsoby:

*   Vytvořte rozhraní pro provádění mezi jazyky.
*   Zadejte model objektově orientované na podporu implementace různé jazyky na implementaci rozhraní .NET.
*   Definujte sadu pravidel, která řídí všechny jazyky při rozhodování o práci s typy.
*   Zadejte knihovnu, která obsahuje základní primitivní typy, které se používají při vývoji aplikace (jako je třeba `Boolean`, `Byte`, `Char` atd.)

Definuje dva hlavní typy typy, které by mělo podporovat CTS: typy odkazu a hodnotu. Jejich názvy přejděte na jejich definice.

Odkazové typy objektů jsou reprezentované pomocí odkaz na skutečnou hodnotu objektu; odkaz na tady je podobná ukazatel v jazyce C/C++. Jednoduše odkazuje umístění paměti, kde jsou hodnoty objektu. Tato akce nemá velký dopad na tom, jak se používají tyto typy. Pokud přiřadit typu odkazu na proměnnou a pak předejte tuto proměnnou na metodu, například všechny změny do objektu se projeví na hlavním objektem; není žádný kopírování.

Typy hodnot jsou opak, kde jsou objekty reprezentované pomocí jejich hodnot. Chcete-li přiřadit typ hodnoty proměnné, jsou v podstatě kopírování hodnotu objektu.

CTS definuje několik kategorií typů, které mají své specifické sémantiku a využití:

*   Třídy
*   Struktury
*   Výčty
*   Rozhraní
*   Delegáty

CTS definuje také všechny ostatní vlastnosti z typů, jako je například modifikátory přístupu, co jsou členy platný typ, jak dědičnosti a přetížení funguje a tak dále. Bohužel přejdete přímým do jakéhokoli z nich je nad rámec úvodní článek jako je tato, ale můžete obrátit [více prostředků](#more-resources) na konci odkazy na další podrobné obsah, který obsahuje tato témata.

## <a name="common-language-specification"></a>CLS (Common Language Specification)

Pokud chcete povolit scénáře plnou interoperabilitu, musí všechny objekty, které jsou vytvořené v kódu spoléhat na některé funkcím v jazycích, které spotřebovávají je (jsou jejich _volající_). Vzhledem k tomu, že existuje mnoho různých jazyků, rozhraní .NET byla zadána těchto commonalities v takzvaný **Common Language Specification** (CLS). Specifikace CLS definuje sadu funkcí, které jsou vyžadovány mnoho běžných aplikací. Nabízí taky řazení recept na jakýkoli jazyk, který se implementuje nad .NET na vše potřebné pro podporu.

Specifikací CLS je podmnožinou CTS. To znamená, že všechna pravidla v CTS platí také pro specifikaci CLS pouze v případě jsou více striktní pravidla se specifikací CLS. Pokud součást je sestaven pomocí pouze pravidla ve specifikaci CLS, tedy zpřístupňuje pouze funkce specifikací CLS v jeho rozhraní API, je označováno jako **kompatibilní se specifikací CLS**. Například `<framework-librares>` jsou kompatibilní se specifikací CLS právě proto potřebují k práci ve všech jazycích, které jsou podporovány v rozhraní .NET.

Lze najít dokumenty v [více prostředků](#more-resources) části níže získat přehled o všech funkcí ve specifikaci CLS.

## <a name="more-resources"></a>Další prostředky

*   [Obecný systém typů](./base-types/common-type-system.md)
*   [Common Language Specification](language-independence-and-language-independent-components.md)
