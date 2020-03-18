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
# <a name="performing-culture-insensitive-string-operations"></a><span data-ttu-id="a2f5f-102">Provádění řetězcových operací necitlivých na jazykovou verzi</span><span class="sxs-lookup"><span data-stu-id="a2f5f-102">Performing culture-insensitive string operations</span></span>
<span data-ttu-id="a2f5f-103">Většina metod rozhraní .NET Framework, které ve výchozím nastavení provádějí operace řetězce citlivé na <xref:System.Globalization.CultureInfo> jazykovou verzi, poskytuje přetížení metod, která umožňují explicitně určit jazykovou verzi, která má být používána předáním parametru.</span><span class="sxs-lookup"><span data-stu-id="a2f5f-103">Most .NET Framework methods that perform culture-sensitive string operations by default provide method overloads that allow you to explicitly specify the culture to use by passing a <xref:System.Globalization.CultureInfo> parameter.</span></span> <span data-ttu-id="a2f5f-104">Tato přetížení umožňují eliminovat kulturní variace v případě mapování a řazení pravidel a zaručit výsledky necitlivé na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="a2f5f-104">These overloads allow you to eliminate cultural variations in case mappings and sorting rules and guarantee culture-insensitive results.</span></span>  
  
 <span data-ttu-id="a2f5f-105">Tato část obsahuje následující témata, která ukazují, jak provádět operace řetězce necitlivé na jazykové verzi pomocí metod rozhraní .NET Framework, které jsou ve výchozím nastavení citlivé na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="a2f5f-105">This section provides the following topics to demonstrate how to perform culture-insensitive string operations using .NET Framework methods that are culture-sensitive by default.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="a2f5f-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="a2f5f-106">In this section</span></span>  
 [<span data-ttu-id="a2f5f-107">Provádění porovnávání řetězců nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="a2f5f-107">Performing Culture-Insensitive String Comparisons</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-comparisons.md)  
 <span data-ttu-id="a2f5f-108">Popisuje, jak používat <xref:System.String.Compare%2A?displayProperty=nameWithType> <xref:System.String.CompareTo%2A?displayProperty=nameWithType> metody a k provádění porovnávání řetězců necitlivých na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="a2f5f-108">Describes how to use the <xref:System.String.Compare%2A?displayProperty=nameWithType> and <xref:System.String.CompareTo%2A?displayProperty=nameWithType> methods to perform culture-insensitive string comparisons.</span></span>  
  
 [<span data-ttu-id="a2f5f-109">Provádění změn velikosti písmen nezávisle na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="a2f5f-109">Performing Culture-Insensitive Case Changes</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-case-changes.md)  
 <span data-ttu-id="a2f5f-110">Popisuje způsob použití <xref:System.String.ToUpper%2A?displayProperty=nameWithType>metody <xref:System.String.ToLower%2A?displayProperty=nameWithType> <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, <xref:System.Char.ToLower%2A?displayProperty=nameWithType> , a metody k provádění změn bez rozlišování verzí jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="a2f5f-110">Describes how to use the <xref:System.String.ToUpper%2A?displayProperty=nameWithType>, <xref:System.String.ToLower%2A?displayProperty=nameWithType>, <xref:System.Char.ToUpper%2A?displayProperty=nameWithType>, and <xref:System.Char.ToLower%2A?displayProperty=nameWithType> methods to perform culture-insensitive case changes.</span></span>  
  
 [<span data-ttu-id="a2f5f-111">Provádění řetězcových operací nezávislých na jazykové verzi v kolekcích</span><span class="sxs-lookup"><span data-stu-id="a2f5f-111">Performing Culture-Insensitive String Operations in Collections</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md)  
 <span data-ttu-id="a2f5f-112">Popisuje použití <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>a <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> provádět operace necitlivé na jazykové verzi v kolekcích.</span><span class="sxs-lookup"><span data-stu-id="a2f5f-112">Describes how to use the <xref:System.Collections.CaseInsensitiveComparer>, <xref:System.Collections.CaseInsensitiveHashCodeProvider> class, <xref:System.Collections.SortedList>, <xref:System.Collections.ArrayList.Sort%2A?displayProperty=nameWithType> and <xref:System.Collections.Specialized.CollectionsUtil.CreateCaseInsensitiveHashtable%2A?displayProperty=nameWithType> to perform culture-insensitive operations in collections.</span></span>  
  
 [<span data-ttu-id="a2f5f-113">Provádění řetězcových operací nezávislých na jazykové verzi v polích</span><span class="sxs-lookup"><span data-stu-id="a2f5f-113">Performing Culture-Insensitive String Operations in Arrays</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-arrays.md)  
 <span data-ttu-id="a2f5f-114">Popisuje, jak používat <xref:System.Array.Sort%2A?displayProperty=nameWithType> <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody a k provádění operací necitlivých na jazykovou verzi v polích.</span><span class="sxs-lookup"><span data-stu-id="a2f5f-114">Describes how to use the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods to perform culture-insensitive operations in arrays.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="a2f5f-115">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="a2f5f-115">Related sections</span></span>  
 [<span data-ttu-id="a2f5f-116">Řetězcové operace necitlivé na jazykovou verzi</span><span class="sxs-lookup"><span data-stu-id="a2f5f-116">Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/culture-insensitive-string-operations.md)  
 <span data-ttu-id="a2f5f-117">Popisuje, proč byste měli být vědomi jazykové verze při provádění operací na řetězce a poskytuje pokyny pro provádění operací citlivých na jazykovou verzi a kdy provádět operace necitlivé na jazykovou verzi.</span><span class="sxs-lookup"><span data-stu-id="a2f5f-117">Describes why you should be aware of culture when performing operations on strings and provides guidelines for when to perform culture-sensitive operations and when to perform culture-insensitive operations.</span></span>

## <a name="see-also"></a><span data-ttu-id="a2f5f-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="a2f5f-118">See also</span></span>

- [<span data-ttu-id="a2f5f-119">Třídění tabulek hmotnosti (pro rozhraní .NET v systémech Windows)</span><span class="sxs-lookup"><span data-stu-id="a2f5f-119">Sorting Weight Tables (for .NET on Windows systems)</span></span>](https://www.microsoft.com/download/details.aspx?id=10921)
- [<span data-ttu-id="a2f5f-120">Výchozí tabulka prvků řazení unicode (pro .NET Core v Linuxu a macOS)</span><span class="sxs-lookup"><span data-stu-id="a2f5f-120">Default Unicode Collation Element Table (for .NET Core on Linux and macOS)</span></span>](https://www.unicode.org/Public/UCA/latest/allkeys.txt)
