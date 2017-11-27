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
ms.openlocfilehash: e703e9adc531b7d1695d3e9bbed61a2c0f62ad31
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="e67fe-102">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="e67fe-102">Performing Culture-Insensitive String Operations</span></span>
<span data-ttu-id="e67fe-103">Přetížení metody, které vám umožní explicitně zadat jazykovou verzi předáním poskytovat většinu metod rozhraní .NET Framework, které ve výchozím nastavení provádět operace s řetězci zohledňující jazykovou verzi <xref:System.Globalization.CultureInfo> parametr.</span><span class="sxs-lookup"><span data-stu-id="e67fe-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="e67fe-104">Tato přetížení umožňují odstranění v případě, že mapování a řazení pravidel a zaručit výsledky na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="e67fe-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="e67fe-105">Tato část obsahuje následující témata, které ukazují, jak provést operace s řetězci nezávislé na jazykových pomocí metod rozhraní .NET Framework, které jsou závislé na jazykové verzi ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="e67fe-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e67fe-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e67fe-106">In This Section</span></span>  
 [<span data-ttu-id="e67fe-107">Provádění porovnávání řetězců nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="e67fe-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="e67fe-108">Popisuje postup použití <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody k provádění porovnávání řetězců nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="e67fe-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="e67fe-109">Provádění nezávislé na jazykových změny velikosti písmen</span><span class="sxs-lookup"><span data-stu-id="e67fe-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="e67fe-110">Popisuje postup použití <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody k provedení změny velikosti písmen na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="e67fe-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="e67fe-111">Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích</span><span class="sxs-lookup"><span data-stu-id="e67fe-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="e67fe-112">Popisuje postup použití <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> a <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> k provádění operací nezávislých na jazykové verzi v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="e67fe-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="e67fe-113">Provádění řetězcových operací nezávislých na jazykové verzi v polích</span><span class="sxs-lookup"><span data-stu-id="e67fe-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="e67fe-114">Popisuje postup použití <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody k provádění operací nezávislých na jazykové verzi v polích.</span><span class="sxs-lookup"><span data-stu-id="e67fe-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="e67fe-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e67fe-115">Related Sections</span></span>  
 [<span data-ttu-id="e67fe-116">Operace s řetězci nezávislé na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="e67fe-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="e67fe-117">Popisuje, proč byste měli vědět jazykové verze při provádění operace s řetězci a poskytuje pokyny pro čas provádění operace zohledňující jazykovou verzi a kdy k provádění operací nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="e67fe-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>
