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
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: 77269cd9cdb922c1f9576afa93d6599ec7a834e4
ms.sourcegitcommit: 2350a091ef6459f0fcfd894301242400374d8558
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/21/2018
ms.locfileid: "46562119"
---
# <a name="performing-culture-insensitive-string-operations"></a>Provádění řetězcových operací nezávislých na jazykové verzi
Většina metod rozhraní .NET Framework, které provádějí operace s řetězci zohledňující jazykovou verzi ve výchozím nastavení poskytovat přetížení metod, které umožňuje explicitně určit jazyková verze použitá předáním <xref:System.Globalization.CultureInfo> parametru. Tato přetížení umožňují odstranění v případě mapování a řazení pravidel a zaručit výsledků nezávislých na jazykové verzi.  
  
 Tato část obsahuje následující témata ukazují, jak provádět operace s řetězci nezávislé na jazykové verzi pomocí metod rozhraní .NET Framework, které jsou závislé na jazykové verzi ve výchozím nastavení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Provádění porovnávání řetězců nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Popisuje způsob použití <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody pro provádění porovnávání řetězců nezávislých na jazykové verzi.  
  
 [Provádění změn velikosti písmen nezávisle na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Popisuje způsob použití <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody k provedení změn nezávislých na jazykové verzi.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Popisuje způsob použití <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> a <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> k provádění operací nezávislých na jazykové verzi v kolekcích.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Popisuje způsob použití <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> provádět operace nezávislé na jazykové verzi v polích.  
  
## <a name="related-sections"></a>Související oddíly  
 [Řetězcové operace nezávislé na jazykové verzi](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Popisuje, proč byste měli vědět jazykové verze při provádění operací na řetězce a poskytuje pokyny, kdy se má provést operace zohledňující jazykovou verzi a kdy k provádění operací nezávislých na jazykové verzi.

## <a name="see-also"></a>Viz také:

- [Řazení váhy tabulky (pro .NET v systémech Windows)](https://www.microsoft.com/en-us/download/details.aspx?id=10921)
- [Výchozí kódování Unicode kolace Element tabulky (pro .NET Core v Linuxu a macOS)](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
