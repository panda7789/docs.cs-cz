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
ms.openlocfilehash: 22815b5ab993b36bc8bcb91f89f346cb6d812e19
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/09/2018
ms.locfileid: "44251690"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Provádění řetězcových operací nezávislých na jazykové verzi v polích
Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> provedení řazení zohledňující jazykovou verzi pomocí výchozí metody <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost. Zohledňující jazykovou verzi výsledky vrácené tyto metody se může lišit podle jazykové verze kvůli rozdílům v pořadí řazení. Chcete-li odstranit chování závislé na jazykové verzi, použijte jednu z přetížení této metody, které přijímá `comparer` parametru. `comparer` Určuje parametr <xref:System.Collections.IComparer> implementace pro použití při porovnávání prvků v poli. Pro parametr, zadejte vlastní výchozí porovnávací metody třídu, která používá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Příklad vlastní výchozí porovnávací metody třídy je k dispozici v dílčím tématu "Používání SortedList – třída", které se nachází [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tématu.  
  
 **Poznámka:** předávání **CultureInfo.InvariantCulture** k porovnání metoda provést porovnání nezávislá na jazykové verzi. Ale to nezpůsobí nejazykové porovnání, například cesty k souborům, klíče registru a proměnných prostředí. Ani nepodporuje rozhodnutí o zabezpečení založeno na výsledku porovnání. Nejazykové porovnání nebo podporu pro rozhodnutí o zabezpečení na základě výsledku, aplikace by měla použít metodu porovnání, která přijímá <xref:System.StringComparison> hodnotu. Aplikace by měla předat <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
- <xref:System.Collections.IComparer>  
- [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
