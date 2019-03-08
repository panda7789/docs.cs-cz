---
title: Obecný systém typů a Common Language Specification
description: Zjistěte, jak běžné systém typů (CTS) a specifikace CLS (Common Language) umožňují .NET zajistit podporu více jazyků.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: a6704b09a51a509cb7fbd786f9040454f78cc862
ms.sourcegitcommit: 58fc0e6564a37fa1b9b1b140a637e864c4cf696e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/08/2019
ms.locfileid: "57675365"
---
# <a name="common-type-system--common-language-specification"></a>Obecný systém typů a Common Language Specification

Znovu dvě podmínky, které jsou volně používat na světě .NET ve skutečnosti jsou důležité, abyste pochopili, jak implementace .NET umožňuje vývoj pro více jazyků a pochopit, jak to funguje.

## <a name="common-type-system"></a>Obecný systém typů

Chcete-li začít od začátku, mějte na paměti, že je implementace .NET _jazykově nezávislé_. Právě to neznamená, že programátor napsat svůj kód v jakémkoliv jazyce, který může být sestaven IL. Také znamená, že potřebuje, aby mohli pracovat s kódem napsaným v jiných jazycích, které je možné používat v implementaci rozhraní .NET.

Pokud to chcete udělat transparentně, musí být běžný způsob, jak popisují všechny podporované typy. To je, co běžné systém typů (CTS) má na starosti udělat. Byl proveden udělat několik věcí:

*   Vytvoření rozhraní pro provádění různých jazycích.
*   Poskytuje objektově orientovaný model pro podporu implementace různých jazyků v implementaci rozhraní .NET.
*   Definujte sadu pravidel, které musí dodržovat všechny jazyky, při rozhodování o práci s typy.
*   Zadejte knihovnu, která obsahuje základní primitivní typy, které se používají při vývoji aplikace (jako jsou například `Boolean`, `Byte`, `Char` atd.)

Specifikace CTS definuje dva hlavní druhy typů, které by měla podporovat: typy odkazu a hodnotu. Jejich názvy, přejděte na jejich definice.

Odkazové typy objekty jsou reprezentovány s odkazem na skutečnou hodnotu objektu; odkaz zde je podobný ukazatele v jazyce C/C++. Jednoduše odkazuje na umístění paměti, kde jsou hodnoty objektů. To má velký dopad na používání těchto typů. Pokud přiřadit proměnné typu odkazu a pak předejte ji do metody, například všechny změny do objektu se projeví na hlavní objekt. neexistuje žádné kopírování.

Typy hodnot jsou opak, kde jsou reprezentovány objekty podle jejich hodnoty. Pokud přiřadíte typ hodnoty proměnnou, kterou kopírujete v podstatě hodnotu objektu.

Specifikace CTS definuje několik kategorií typů, které mají své specifické sémantiku a využití:

*   Třídy
*   Struktury
*   Výčty
*   Rozhraní
*   Delegáty

Specifikace CTS definuje také všechny ostatní vlastnosti typů, jako je například modifikátory přístupu, jak co jsou členy platný typ, dědičnosti a přetížení funguje a tak dále. Bohužel budete věnovat podrobněji některé z nich je nad rámec úvodní článek takovou situaci, ale můžete konzultovat [více prostředků](#more-resources) na konci odkazy na zájem o podrobný obsah, který obsahuje tato témata.

## <a name="common-language-specification"></a>CLS (Common Language Specification)

Aby se povolily scénáře plnou interoperabilitu, musíte všechny objekty, které jsou vytvořeny v kódu spoléhat na několik společných prvků v jazycích, které jsou jejich používáním (jsou jejich _volající_). Vzhledem k tomu, že existuje mnoho různých jazyků, rozhraní .NET má zadané tyto commonalities v s názvem **Common Language Specification** (CLS). Kompatibilní se Specifikací definuje sadu funkcí, které jsou potřeba řada běžných aplikací. Poskytuje také druh předpisu pro libovolný jazyk, který se implementuje nad .NET na to, co potřebuje pro podporu.

Specifikace CLS je podmnožinou CTS. To znamená, že všechna pravidla v CTS platí také pro specifikace CLS, pokud nejsou přísnější pravidla specifikace CLS. Pokud součást se využívá jenom pravidla ve specifikaci CLS, to znamená, poskytuje pouze funkce kompatibilní se Specifikací v jeho rozhraní API, je označen jako **kompatibilní se Specifikací CLS**. Například `<framework-librares>` jsou kompatibilní se Specifikací CLS, přesně, protože potřebují pracovat ve všech jazycích, které jsou podporovány v rozhraní .NET.

Můžete konzultovat dokumenty v [více prostředků](#more-resources) dole můžete získat přehled o všech funkcí ve specifikaci CLS.

## <a name="more-resources"></a>Další materiály

*   [Obecný systém typů](./base-types/common-type-system.md)
*   [Common Language Specification](language-independence-and-language-independent-components.md)
