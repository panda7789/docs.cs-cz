---
title: "Provádění řetězcových operací nezávislých na jazykové verzi"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-standard
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- case mappings
- custom case mappings
- culture, custom sorting rules
- custom sorting rules
- culture-insensitive string operations, options for performing
- culture, custom case mappings
- culture-insensitive string operations, method overloads
ms.assetid: 579ef891-1f83-4c63-9ebd-2f40406b5b91
caps.latest.revision: "13"
author: rpetrusha
ms.author: ronpet
manager: wpickett
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: 62aa839d2dae2f6dc84d529a8abf5061367f221f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="performing-culture-insensitive-string-operations"></a>Provádění řetězcových operací nezávislých na jazykové verzi
Přetížení metody, které vám umožní explicitně zadat jazykovou verzi předáním poskytovat většinu metod rozhraní .NET Framework, které ve výchozím nastavení provádět operace s řetězci zohledňující jazykovou verzi <xref:System.Globalization.CultureInfo> parametr. Tato přetížení umožňují odstranění v případě, že mapování a řazení pravidel a zaručit výsledky na jazykové verzi.  
  
 Tato část obsahuje následující témata, které ukazují, jak provést operace s řetězci nezávislé na jazykových pomocí metod rozhraní .NET Framework, které jsou závislé na jazykové verzi ve výchozím nastavení.  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Provádění porovnávání řetězců nezávislých na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 Popisuje postup použití <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody k provádění porovnávání řetězců nezávislých na jazykové verzi.  
  
 [Provádění změn velikosti písmen nezávisle na jazykové verzi](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 Popisuje postup použití <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody k provedení změny velikosti písmen na jazykové verzi.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 Popisuje postup použití <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> a <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> k provádění operací nezávislých na jazykové verzi v kolekcích.  
  
 [Provádění řetězcových operací nezávislých na jazykové verzi v polích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 Popisuje postup použití <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody k provádění operací nezávislých na jazykové verzi v polích.  
  
## <a name="related-sections"></a>Související oddíly  
 [Řetězcové operace nezávislé na jazykové verzi](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 Popisuje, proč byste měli vědět jazykové verze při provádění operace s řetězci a poskytuje pokyny pro čas provádění operace zohledňující jazykovou verzi a kdy k provádění operací nezávislých na jazykové verzi.
