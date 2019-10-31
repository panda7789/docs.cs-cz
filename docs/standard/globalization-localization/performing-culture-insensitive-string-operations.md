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
ms.sourcegitcommit: 559fcfbe4871636494870a8b716bf7325df34ac5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/30/2019
ms.locfileid: "73120788"
---
# <a name="performing-culture-insensitive-string-operations"></a>Provádění řetězcových operací nezávislých na jazykové verzi
Většina .NET Framework metod, které provádějí operace s řetězci závislé na jazykové verzi, ve výchozím nastavení poskytují přetížení metod, které umožňují explicitně zadat jazykovou verzi, která se má použít, předáním parametru <xref:System.Globalization.CultureInfo>. Tato přetížení umožňují eliminovat kulturní variace v případě mapování a pravidel řazení a záruku výsledků nezávislých na jazykové verzi.  
  
 Tato část poskytuje následující témata, která ukazují, jak provádět řetězcové operace nezávislé na jazykové verzi pomocí .NET Framework metod, které jsou ve výchozím nastavení závislé na jazykové verzi.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Provádění porovnávání řetězců nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Popisuje, jak používat metody <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> k provádění porovnávání řetězců nezávislých na jazykové verzi.  
  
 [Provádění změn velikosti písmen nezávisle na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Popisuje, jak použít metody <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> k provádění změn velikosti písmen nezávisle na jazykové verzi.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Popisuje způsob použití <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> a <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> k provádění operací nezávislých na jazykové verzi v kolekcích.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Popisuje, jak používat metody <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> k provádění operací nezávislých na jazykové verzi v polích.  
  
## <a name="related-sections"></a>Související oddíly  
 [Řetězcové operace nezávislé na jazykové verzi](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Popisuje, proč byste měli být vědomi jazykové verze při provádění operací s řetězci a poskytuje pokyny pro provedení operací závislých na jazykové verzi a kdy provádět operace nezávislé na jazykové verzi.

## <a name="see-also"></a>Viz také:

- [Řazení tabulek váhy (pro .NET v systémech Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Výchozí tabulka prvků kolace Unicode (pro .NET Core v systémech Linux a macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
