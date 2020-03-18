---
title: Provádění řetězcových operací nezávislých na jazykové verzi
ms.date: 08/22/2018
ms.technology: dotnet-standard
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
ms.openlocfilehash: 183078b1f7a3eb3530fea8af06dbb59055d7d25d
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/15/2020
ms.locfileid: "73120788"
---
# <a name="performing-culture-insensitive-string-operations"></a>Provádění řetězcových operací necitlivých na jazykovou verzi
Většina metod rozhraní .NET Framework, které ve výchozím nastavení provádějí operace řetězce citlivé na <xref:System.Globalization.CultureInfo> jazykovou verzi, poskytuje přetížení metod, která umožňují explicitně určit jazykovou verzi, která má být používána předáním parametru. Tato přetížení umožňují eliminovat kulturní variace v případě mapování a řazení pravidel a zaručit výsledky necitlivé na jazykovou verzi.  
  
 Tato část obsahuje následující témata, která ukazují, jak provádět operace řetězce necitlivé na jazykové verzi pomocí metod rozhraní .NET Framework, které jsou ve výchozím nastavení citlivé na jazykovou verzi.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Provádění porovnávání řetězců nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Popisuje, jak používat <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody a k provádění porovnávání řetězců necitlivých na jazykovou verzi.  
  
 [Provádění změn velikosti písmen nezávisle na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Popisuje způsob použití <xref:System.String.ToUpper%2A?displayProperty=nameWithType>metody <xref:System.String.ToLower%2A?displayProperty=nameWithType> <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, <xref:System.Char.ToLower%2A?displayProperty=nameWithType> , a metody k provádění změn bez rozlišování verzí jazykové verze.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Popisuje použití <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>a <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> provádět operace necitlivé na jazykové verzi v kolekcích.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Popisuje, jak používat <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody a k provádění operací necitlivých na jazykovou verzi v polích.  
  
## <a name="related-sections"></a>Související oddíly  
 [Řetězcové operace necitlivé na jazykovou verzi](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Popisuje, proč byste měli být vědomi jazykové verze při provádění operací na řetězce a poskytuje pokyny pro provádění operací citlivých na jazykovou verzi a kdy provádět operace necitlivé na jazykovou verzi.

## <a name="see-also"></a>Viz také

- [Třídění tabulek hmotnosti (pro rozhraní .NET v systémech Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Výchozí tabulka prvků řazení unicode (pro .NET Core v Linuxu a macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
