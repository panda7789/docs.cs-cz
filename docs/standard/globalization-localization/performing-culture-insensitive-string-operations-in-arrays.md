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
ms.openlocfilehash: f4d732d64eecff72403c455c14b68c3aec1b5407
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33572057"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Provádění řetězcových operací nezávislých na jazykové verzi v polích
Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody provedení řazení zohledňující jazykovou verzi pomocí výchozí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost. Jazykovou výsledky vrácené tyto metody se může lišit podle jazykové verze kvůli rozdílům v pořadí řazení. Vyloučit chování zohledňující jazykovou verzi, použijte jednu z přetížení této metody, které přijímá `comparer` parametr. `comparer` Parametr určuje <xref:System.Collections.IComparer> implementaci má být použita při porovnání prvků v poli. Pro parametr, zadejte vlastní invariantní porovnávání třídu, která využívá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Příklad vlastní invariantní porovnávání třídy je součástí "Pomocí SortedList Class" v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tématu.  
  
 **Poznámka:** předávání **CultureInfo.InvariantCulture** k porovnání metoda provést porovnání na jazykové verzi. Však nevytváří-lingvistické porovnání, například cesty k souborům, klíčů registru a proměnných prostředí. Ani podporuje rozhodnutí o zabezpečení na základě výsledku porovnání. Lingvistické porovnání nebo podporu pro zabezpečení na základě výsledku rozhodnutí, by aplikace měla používat porovnání metodu, která přijímá <xref:System.StringComparison> hodnotu. Aplikace by pak předat <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
