---
title: Operace s řetězci nezávislé na jazykových verzích
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture, culture-insensitive string operations
- case-sensitive comparisons
- globalization [.NET Framework], culture-insensitive string operations
- strings [.NET Framework], culture-insensitive string operations
- localization [.NET Framework], culture-insensitive string operations
- world-ready applications, culture-insensitive string operations
- culture-sensitive string operations
- culture-insensitive string operations
ms.assetid: e6e2bb94-a95d-44e2-b68c-cfdd1db77784
ms.openlocfilehash: 0db77f3e11542bb920df1e45312a72decc2a34fd
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84279786"
---
# <a name="culture-insensitive-string-operations"></a>Řetězcové operace nezávislé na jazykové verzi

Operace s řetězci závislé na jazykové verzi mohou být vhodné v případě, že vytváříte aplikace, které jsou navrhovány tak, aby uživatelům zobrazovaly výsledky na základě jazykové verze. Ve výchozím nastavení metody zohledňující jazykovou verzi získají jazykovou verzi pro použití z <xref:System.Globalization.CultureInfo.CurrentCulture%2A> vlastnosti pro aktuální vlákno.

Pamatujte, že operace s řetězci závislé na jazykové verzi nemusí vždy představovat požadované chování. Používání operací závislých na jazykové verzi v případě, že výsledky by měly být na jazykové verzi nezávislé, může způsobit selhání kódu aplikace v jazykových verzích s vlastními pravidly mapování a řazení. Příklad naleznete v části ["porovnání řetězců, které používají aktuální jazykovou verzi"](../base-types/best-practices-strings.md#string-comparisons-that-use-the-current-culture) v článku [osvědčené postupy pro použití řetězců](../base-types/best-practices-strings.md) .

Skutečnost, zda operace s řetězci mají být závislé nebo nezávislé na jazykové verzi, závisí na tom, jakým způsobem aplikace pracuje s výsledky. Operace s řetězci, které zobrazují výsledky uživateli, by měly být většinou závislé na jazykové verzi. Pokud například konkrétní aplikace zobrazuje seřazený seznam lokalizovaných řetězců v seznamu, měla by aplikace provést řazení závislé na jazykové verzi.

Výsledky operací s řetězci, které se používají interně, by měly být většinou nezávislé na jazykové verzi. Obecně platí, že pokud aplikace pracuje s názvy souborů, formáty persistence nebo symbolickými informacemi, které se uživateli nezobrazují, neměly by se výsledky operací s řetězci lišit podle jazykové verze. Pokud aplikace například porovnává řetězec a chce určit, zda se jedná o rozpoznanou značku XML, porovnání by nemělo být závislé na jazykové verzi. Kromě toho, pokud je rozhodnutí o zabezpečení založeno na výsledku porovnání řetězců nebo operaci změny velikosti písmen, operace by měla být nezávislá na jazykové verzi, aby se zajistilo, že výsledek není ovlivněn hodnotou <xref:System.Globalization.CultureInfo.CurrentCulture%2A> .

Bez ohledu na to, zda vyvíjíte aplikaci, která obsahuje kód pro zpracování problémů lokalizace a globalizace, měli byste si být vědomi metod rozhraní .NET Framework, které automaticky získávají výsledky závislé na jazykové verzi. Účelem tohoto tématu je objasnění správného způsobu používání těchto metod v rámci aplikací pro získávání výsledků nezávislých na jazykové verzi.

## <a name="see-also"></a>Viz také

- [Globalizace a lokalizace](index.md)
