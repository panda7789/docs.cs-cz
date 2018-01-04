---
title: "Provádění řetězcových operací nezávislých na jazykové verzi v polích"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: d273fbaa792092f5ea56bfa59392794b6728ed67
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a>Provádění řetězcových operací nezávislých na jazykové verzi v polích
Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody provedení řazení zohledňující jazykovou verzi pomocí výchozí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost. Jazykovou výsledky vrácené tyto metody se může lišit podle jazykové verze kvůli rozdílům v pořadí řazení. Vyloučit chování zohledňující jazykovou verzi, použijte jednu z přetížení této metody, které přijímá `comparer` parametr. `comparer` Parametr určuje <xref:System.Collections.IComparer> implementaci má být použita při porovnání prvků v poli. Pro parametr, zadejte vlastní invariantní porovnávání třídu, která využívá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>. Příklad vlastní invariantní porovnávání třídy je součástí "Pomocí SortedList Class" v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tématu.  
  
 **Poznámka:** předávání **CultureInfo.InvariantCulture** k porovnání metoda provést porovnání na jazykové verzi. Však nevytváří-lingvistické porovnání, například cesty k souborům, klíčů registru a proměnných prostředí. Ani podporuje rozhodnutí o zabezpečení na základě výsledku porovnání. Lingvistické porovnání nebo podporu pro zabezpečení na základě výsledku rozhodnutí, by aplikace měla používat porovnání metodu, která přijímá <xref:System.StringComparison> hodnotu. Aplikace by pak předat <xref:System.StringComparison.Ordinal>.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [Provádění řetězcových operací nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
