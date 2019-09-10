---
title: Provádění řetězcových operací nezávislých na jazykové verzi v polích
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b52ff8d72132c1076dfdece5e1ce47bbece37b81
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855991"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Provádění řetězcových operací nezávislých na jazykové verzi v polích

Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> metod a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> provádějí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> řazení zohledňující jazykovou verzi ve výchozím nastavení pomocí vlastnosti. Výsledky závislé na jazykové verzi vracené těmito metodami se mohou v důsledku rozdílů v pořadí řazení lišit podle jazykové verze. Chcete-li eliminovat chování zohledňující jazykovou verzi, použijte jedno z přetížení této metody, která `comparer` přijímá parametr. `comparer` Parametr<xref:System.Collections.IComparer> určuje implementaci, která se má použít při porovnávání prvků v poli. Pro parametr zadejte vlastní třídu pro invariantní porovnávání, která používá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Příklad vlastní invariantní třídy porovnávání je k dispozici v tématu "použití třídy SortedList" [v tématu provádění řetězcových operací nezávislých na jazykové verzi v tématu kolekce](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) .

> [!NOTE]
> Předávání **CultureInfo. InvariantCulture** metodě porovnání provádí porovnání nezávislé na jazykové verzi. Nezpůsobuje ale nelingvistické porovnání, například pro cesty k souboru, klíče registru a proměnné prostředí. Ani to nepodporuje rozhodnutí o zabezpečení na základě výsledku porovnání. Pro nelingvistické porovnání nebo podporu pro rozhodování o zabezpečení na základě výsledků by aplikace měla používat metodu porovnání, která přijímá <xref:System.StringComparison> hodnotu. Aplikace by se měla předat <xref:System.StringComparison.Ordinal>.

## <a name="see-also"></a>Viz také:

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
