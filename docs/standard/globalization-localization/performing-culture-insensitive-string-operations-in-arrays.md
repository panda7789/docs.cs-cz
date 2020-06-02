---
title: Provádění řetězcových operací nezávislých na jazykové verzi v polích
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
ms.openlocfilehash: 02690f78184ca4f216df7346a84f0266c2dcec99
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84288599"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Provádění řetězcových operací nezávislých na jazykové verzi v polích

Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metod a provádějí řazení zohledňující jazykovou verzi ve výchozím nastavení pomocí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> Vlastnosti. Výsledky závislé na jazykové verzi vracené těmito metodami se mohou v důsledku rozdílů v pořadí řazení lišit podle jazykové verze. Chcete-li eliminovat chování zohledňující jazykovou verzi, použijte jedno z přetížení této metody, která přijímá `comparer` parametr. `comparer`Parametr určuje implementaci, <xref:System.Collections.IComparer> která se má použít při porovnávání prvků v poli. Pro parametr zadejte vlastní třídu pro invariantní porovnávání, která používá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType> . Příklad vlastní invariantní třídy porovnávání je k dispozici v tématu "použití třídy SortedList" [v tématu provádění řetězcových operací nezávislých na jazykové verzi v tématu kolekce](performing-culture-insensitive-string-operations-in-collections.md) .

> [!NOTE]
> Předávání **CultureInfo. InvariantCulture** metodě porovnání provádí porovnání nezávislé na jazykové verzi. Nezpůsobuje ale nelingvistické porovnání, například pro cesty k souboru, klíče registru a proměnné prostředí. Ani to nepodporuje rozhodnutí o zabezpečení na základě výsledku porovnání. Pro nelingvistické porovnání nebo podporu pro rozhodování o zabezpečení na základě výsledků by aplikace měla používat metodu porovnání, která přijímá <xref:System.StringComparison> hodnotu. Aplikace by se měla předat <xref:System.StringComparison.Ordinal> .

## <a name="see-also"></a>Viz také

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Provádění řetězcových operací nezávislých na jazykové verzi](performing-culture-insensitive-string-operations.md)
