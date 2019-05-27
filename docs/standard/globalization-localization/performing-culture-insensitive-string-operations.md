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
ms.openlocfilehash: 6054df642176976db4feb2aba682a20ca6b3dda5
ms.sourcegitcommit: 7e129d879ddb42a8b4334eee35727afe3d437952
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/23/2019
ms.locfileid: "66053128"
---
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="df3fd-102">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="df3fd-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="df3fd-103">Většina metod rozhraní .NET Framework, které provádějí operace s řetězci zohledňující jazykovou verzi ve výchozím nastavení poskytovat přetížení metod, které umožňuje explicitně určit jazyková verze použitá předáním <xref:System.Globalization.CultureInfo> parametru.</span><span class="sxs-lookup"><span data-stu-id="df3fd-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="df3fd-104">Tato přetížení umožňují odstranění v případě mapování a řazení pravidel a zaručit výsledků nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="df3fd-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="df3fd-105">Tato část obsahuje následující témata ukazují, jak provádět operace s řetězci nezávislé na jazykové verzi pomocí metod rozhraní .NET Framework, které jsou závislé na jazykové verzi ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="df3fd-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="df3fd-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="df3fd-106">In this section</span></span>  
 [<span data-ttu-id="df3fd-107">Provádění porovnávání řetězců nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="df3fd-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="df3fd-108">Popisuje způsob použití <xref:System.String.Compare%2A?displayProperty=nameWithType> a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody pro provádění porovnávání řetězců nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="df3fd-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="df3fd-109">Provádění změn velikosti písmen nezávisle na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="df3fd-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="df3fd-110">Popisuje způsob použití <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, a <xref:System.Char.ToLower%2A?displayProperty=nameWithType> metody k provedení změn nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="df3fd-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="df3fd-111">Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích</span><span class="sxs-lookup"><span data-stu-id="df3fd-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="df3fd-112">Popisuje způsob použití <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> třídy <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> a <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> k provádění operací nezávislých na jazykové verzi v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="df3fd-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="df3fd-113">Provádění řetězcových operací nezávislých na jazykové verzi v polích</span><span class="sxs-lookup"><span data-stu-id="df3fd-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="df3fd-114">Popisuje způsob použití <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> provádět operace nezávislé na jazykové verzi v polích.</span><span class="sxs-lookup"><span data-stu-id="df3fd-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="df3fd-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="df3fd-115">Related sections</span></span>  
 [<span data-ttu-id="df3fd-116">Řetězcové operace nezávislé na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="df3fd-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="df3fd-117">Popisuje, proč byste měli vědět jazykové verze při provádění operací na řetězce a poskytuje pokyny, kdy se má provést operace zohledňující jazykovou verzi a kdy k provádění operací nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="df3fd-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="df3fd-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="df3fd-118">See also</span></span>

- [<span data-ttu-id="df3fd-119">Řazení váhy tabulky (pro .NET v systémech Windows)</span><span class="sxs-lookup"><span data-stu-id="df3fd-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="df3fd-120">Výchozí kódování Unicode kolace Element tabulky (pro .NET Core v Linuxu a macOS)</span><span class="sxs-lookup"><span data-stu-id="df3fd-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
