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
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120810"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Provádění řetězcových operací nezávislých na jazykové verzi v polích

Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody provádět jazykové verze citlivé řazení <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> ve výchozím nastavení pomocí vlastnosti. Výsledky citlivé na jazykovou verzi vrácené těmito metodami se mohou lišit podle jazykové verze z důvodu rozdílů v pořadí řazení. Chcete-li eliminovat chování citlivé na jazykovou verzi, použijte `comparer` jeden z přetížení této metody, která přijímá parametr. Parametr `comparer` určuje implementaci, která <xref:System.Collections.IComparer> se má použít při porovnávání prvků v poli. Pro parametr zadejte vlastní invariantní třídu porovnávače, která používá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Příklad vlastní třídy invariantního porovnávání je uveden v podtématu "Using the SortedList Class" v tématu [Provádění řetězcových operací necitlivých na jazykovou verzi v kolekcích.](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)

> [!NOTE]
> Předávání **CultureInfo.InvariantCulture** na metodu porovnání provést porovnání necitlivé z jazykové verze. Nezpůsobuje však nejazykové porovnání, například pro cesty k souborům, klíče registru a proměnné prostředí. Nepodporuje ani rozhodnutí o zabezpečení založená na výsledku porovnání. Pro nejazykové porovnání nebo podporu pro rozhodnutí o zabezpečení založené na výsledcích aplikace <xref:System.StringComparison> by měla použít metodu porovnání, která přijímá hodnotu. Aplikace by pak <xref:System.StringComparison.Ordinal>měla projít .

## <a name="see-also"></a>Viz také

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
