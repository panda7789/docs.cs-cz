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
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="97306-102">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="97306-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="97306-103">Většina .NET Framework metod, které provádějí operace s řetězci závislé na jazykové verzi, ve výchozím nastavení poskytují přetížení metod, které umožňují explicitně zadat jazykovou verzi, která se má použít, předáním <xref:System.Globalization.CultureInfo> parametru.</span><span class="sxs-lookup"><span data-stu-id="97306-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="97306-104">Tato přetížení umožňují eliminovat kulturní variace v případě mapování a pravidel řazení a záruku výsledků nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="97306-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="97306-105">Tato část poskytuje následující témata, která ukazují, jak provádět řetězcové operace nezávislé na jazykové verzi pomocí .NET Framework metod, které jsou ve výchozím nastavení závislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="97306-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="97306-106">V této části</span><span class="sxs-lookup"><span data-stu-id="97306-106">In this section</span></span>  
 [<span data-ttu-id="97306-107">Provádění porovnávání řetězců nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="97306-107">Performing Culture-Insensitive String Comparisons</span></span>](performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="97306-108">Popisuje, jak používat <xref:System.String.Compare%2A?displayProperty=nameWithType> metody a <xref:System.String.CompareTo%2A?displayProperty=nameWithType> k provádění porovnávání řetězců nezávislých na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="97306-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="97306-109">Provádění změn velikosti písmen nezávisle na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="97306-109">Performing Culture-Insensitive Case Changes</span></span>](performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="97306-110">Popisuje, jak použít <xref:System.String.ToUpper%2A?displayProperty=nameWithType> metody, <xref:System.String.ToLower%2A?displayProperty=nameWithType> , a <xref:System.Char.ToUpper%2A?displayProperty=nameWithType> <xref:System.Char.ToLower%2A?displayProperty=nameWithType> k provádění změn velikosti písmen nezávisle na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="97306-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="97306-111">Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích</span><span class="sxs-lookup"><span data-stu-id="97306-111">Performing Culture-Insensitive String Operations in Collections</span></span>](performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="97306-112">Popisuje, jak použít <xref:System.Collections.CaseInsensitiveComparer> třídy,, <xref:System.Collections.CaseInsensitiveHashCodeProvider> <xref:System.Collections.SortedList> <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> a <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> k provádění operací nezávislých na jazykové verzi v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="97306-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="97306-113">Provádění řetězcových operací nezávislých na jazykové verzi v polích</span><span class="sxs-lookup"><span data-stu-id="97306-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="97306-114">Popisuje způsob použití <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metod a k provádění operací nezávislých na jazykové verzi v polích.</span><span class="sxs-lookup"><span data-stu-id="97306-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="97306-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="97306-115">Related sections</span></span>  
 [<span data-ttu-id="97306-116">Operace s řetězci nezávislé na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="97306-116">Culture-Insensitive String Operations</span></span>](culture-insensitive-string-operations.md)  
 <span data-ttu-id="97306-117">Popisuje, proč byste měli být vědomi jazykové verze při provádění operací s řetězci a poskytuje pokyny pro provedení operací závislých na jazykové verzi a kdy provádět operace nezávislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="97306-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="97306-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="97306-118">See also</span></span>

- [<span data-ttu-id="97306-119">Řazení tabulek váhy (pro .NET v systémech Windows)</span><span class="sxs-lookup"><span data-stu-id="97306-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="97306-120">Výchozí tabulka prvků kolace Unicode (pro .NET Core v systémech Linux a macOS)</span><span class="sxs-lookup"><span data-stu-id="97306-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
