---
title: Obecný systém typů a specifikace CLS (Common Language Specification)
description: Zjistěte, jak společný typový systém (CTS) a specifikace společného jazyka (CLS) umožňují rozhraní .NET podporovat více jazyků.
ms.date: 06/20/2016
ms.technology: dotnet-standard
ms.assetid: 3b1f5725-ac94-4f17-8e5f-244442438a4d
ms.openlocfilehash: 8983e456b051ace434fda9f6ed9cf9028c2ec2d7
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "79187669"
---
# <a name="common-type-system--common-language-specification"></a>Obecný systém typů a specifikace CLS (Common Language Specification)

Opět platí, že dva termíny, které jsou volně používány ve světě .NET, jsou ve skutečnosti důležité pochopit, jak implementace .NET umožňuje vývoj více jazyků a pochopit, jak to funguje.

## <a name="common-type-system"></a>Obecný systém typů

Chcete-li začít od začátku, nezapomeňte, že implementace .NET je _jazyk agnostik_. To neznamená jen, že programátor může napsat svůj kód v libovolném jazyce, který lze zkompilovat do IL. To také znamená, že musí být schopen pracovat s kódem napsaným v jiných jazycích, které lze použít na implementaci .NET.

Aby to bylo transparentní, musí existovat společný způsob, jak popsat všechny podporované typy. To je to, co společný typ systému (CTS) je zodpovědný za to. To bylo děláno dělat několik věcí:

* Vytvořte rámec pro provádění mezi jazyky.
* Poskytněte objektově orientovaný model pro podporu implementace různých jazyků v implementaci rozhraní .NET.
* Definujte sadu pravidel, která musí dodržovat všechny jazyky, pokud jde o práci s typy.
* Zadejte knihovnu, která obsahuje základní primitivní typy, které `Boolean` `Byte`se `Char` používají při vývoji aplikací (například , , atd.)

CTS definuje dva hlavní typy typů, které by měly být podporovány: reference a typy hodnot. Jejich jména ukazují na jejich definice.

Objekty typů odkazů jsou reprezentovány odkazem na skutečnou hodnotu objektu; odkaz zde je podobný ukazatel v C/C++. Jednoduše odkazuje na umístění paměti, kde jsou hodnoty objektů. To má hluboký dopad na způsob použití těchto typů. Pokud proměnné přiřadíte typ odkazu a poté tuto proměnnou předáte metodě, například všechny změny objektu se projeví na hlavním objektu; nedochází ke kopírování.

Typy hodnot jsou opačné, kde jsou objekty reprezentovány jejich hodnotami. Pokud proměnné přiřadíte typ hodnoty, v podstatě kopírujete hodnotu objektu.

CTS definuje několik kategorií typů, z nichž každý má jejich specifickou sémantiku a použití:

* Třídy
* Struktury
* Výčty
* Rozhraní
* Delegáty

CTS také definuje všechny ostatní vlastnosti typů, jako jsou modifikátory přístupu, jaké jsou platné členy typu, jak funguje dědičnost a přetížení a tak dále. Bohužel, jít hluboko do některého z nich je nad rámec úvodního článku, jako je tento, ale můžete konzultovat [další zdroje](#more-resources) sekce na konci pro odkazy na podrobnější obsah, který pokrývá tato témata.

## <a name="common-language-specification"></a>CLS (Common Language Specification)

Chcete-li povolit scénáře úplné interoperability, všechny objekty, které jsou vytvořeny v kódu musí spoléhat na některé shodnosti v jazycích, které jsou jejich náročné (jsou jejich _volající_). Vzhledem k tomu, že existuje mnoho různých jazyků, .NET určiltyto společné rysy v něco, co nazývá **specifikace společného jazyka** (CLS). ClS definuje sadu funkcí, které jsou potřebné pro mnoho běžných aplikací. Poskytuje také jakýsi recept pro jakýkoli jazyk, který je implementován nad .NET na co potřebuje podporu.

CLS je podmnožinou CTS. To znamená, že všechna pravidla v CTS platí také pro CLS, pokud pravidla CLS nejsou přísnější. Pokud je komponenta vytvořena pouze pomocí pravidel v cls, to znamená, že zveřejňuje pouze funkce CLS v jeho rozhraní API, říká se, že je **kompatibilní se souborem CLS**. Například `<framework-librares>` jsou kompatibilní se systémem CLS právě proto, že je třeba pracovat ve všech jazycích, které jsou podporovány na rozhraní .NET.

Můžete se podívat do dokumentů v části [Další zdroje](#more-resources) níže získat přehled o všech funkcích v CLS.

## <a name="more-resources"></a>Další zdroje informací

* [Obecný systém typů](./base-types/common-type-system.md)
* [CLS (Common Language Specification)](language-independence-and-language-independent-components.md)
