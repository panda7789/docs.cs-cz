---
title: Provádění řetězcových operací nezávislých na jazykové verzi v polích
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
ms.openlocfilehash: 051ee77ae5d6552e26e0216d58734d90188475f9
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120810"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Provádění řetězcových operací nezávislých na jazykové verzi v polích

Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody provádějí řazení zohledňující jazykovou verzi ve výchozím nastavení pomocí vlastnosti <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType>. Výsledky závislé na jazykové verzi vracené těmito metodami se mohou v důsledku rozdílů v pořadí řazení lišit podle jazykové verze. Chcete-li eliminovat chování zohledňující jazykovou verzi, použijte jedno z přetížení této metody, které přijímá parametr `comparer`. Parametr `comparer` určuje <xref:System.Collections.IComparer> implementaci, která se má použít při porovnávání prvků v poli. Pro parametr zadejte vlastní třídu pro invariantní porovnávání, která používá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Příklad vlastní invariantní třídy porovnávání je k dispozici v tématu "použití třídy SortedList" [v tématu provádění řetězcových operací nezávislých na jazykové verzi v tématu kolekce](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) .

> [!NOTE]
> Předávání **CultureInfo. InvariantCulture** metodě porovnání provádí porovnání nezávislé na jazykové verzi. Nezpůsobuje ale nelingvistické porovnání, například pro cesty k souboru, klíče registru a proměnné prostředí. Ani to nepodporuje rozhodnutí o zabezpečení na základě výsledku porovnání. Pro nelingvistické porovnání nebo podporu pro rozhodování o zabezpečení na základě výsledků by aplikace měla používat metodu porovnání, která přijímá <xref:System.StringComparison>ou hodnotu. Aplikace by pak měla předat <xref:System.StringComparison.Ordinal>.

## <a name="see-also"></a>Viz také:

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
