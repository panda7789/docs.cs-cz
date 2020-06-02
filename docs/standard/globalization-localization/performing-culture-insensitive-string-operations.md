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
ms.openlocfilehash: 79ff899e2964ae2c1e90b7178616c612dddf6d86
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84287503"
---
# <a name="performing-culture-insensitive-string-operations"></a>Provádění řetězcových operací nezávislých na jazykové verzi
Většina .NET Framework metod, které provádějí operace s řetězci závislé na jazykové verzi, ve výchozím nastavení poskytují přetížení metod, které umožňují explicitně zadat jazykovou verzi, která se má použít, předáním <xref:System.Globalization.CultureInfo> parametru. Tato přetížení umožňují eliminovat kulturní variace v případě mapování a pravidel řazení a záruku výsledků nezávislých na jazykové verzi.  
  
 Tato část poskytuje následující témata, která ukazují, jak provádět řetězcové operace nezávislé na jazykové verzi pomocí .NET Framework metod, které jsou ve výchozím nastavení závislé na jazykové verzi.  
  
## <a name="in-this-section"></a>V této části  
 [Provádění porovnávání řetězců nezávislých na jazykové verzi](performing-culture-insensitive-string-comparisons.md)  
 Popisuje, jak používat <xref:System.String.Compare%2A?displayProperty=nameWithType> metody a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> k provádění porovnávání řetězců nezávislých na jazykové verzi.  
  
 [Provádění změn velikosti písmen nezávisle na jazykové verzi](performing-culture-insensitive-case-changes.md)  
 Popisuje, jak použít <xref:System.String.ToUpper%2A?displayProperty=nameWithType> metody, <xref:System.String.ToLower%2A?displayProperty=nameWithType> , a <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> <xref:System.Char.ToLower%2A?displayProperty=nameWithType> k provádění změn velikosti písmen nezávisle na jazykové verzi.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](performing-culture-insensitive-string-operations-in-collections.md)  
 Popisuje, jak použít <xref:System.Collections.CaseInsensitiveComparer> třídy,, <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.SortedList> <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> a <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> k provádění operací nezávislých na jazykové verzi v kolekcích.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v polích](performing-culture-insensitive-string-operations-in-arrays.md)  
 Popisuje způsob použití <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metod a k provádění operací nezávislých na jazykové verzi v polích.  
  
## <a name="related-sections"></a>Související oddíly  
 [Operace s řetězci nezávislé na jazykové verzi](culture-insensitive-string-operations.md)  
 Popisuje, proč byste měli být vědomi jazykové verze při provádění operací s řetězci a poskytuje pokyny pro provedení operací závislých na jazykové verzi a kdy provádět operace nezávislé na jazykové verzi.

## <a name="see-also"></a>Viz také

- [Řazení tabulek váhy (pro .NET v systémech Windows)](https://www.microsoft.com/download/details.aspx?id=10921)
- [Výchozí tabulka prvků kolace Unicode (pro .NET Core v systémech Linux a macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
