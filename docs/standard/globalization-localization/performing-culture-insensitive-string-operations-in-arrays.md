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
ms.openlocfilehash: 1b4e040ed379cdbf43fbe8b2c4379fdd4dc781f2
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="56130-102">Provádění řetězcových operací nezávislých na jazykové verzi v polích</span><span class="sxs-lookup"><span data-stu-id="56130-102">Performing Culture-Insensitive String Operations in Arrays</span></span>
<span data-ttu-id="56130-103">Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> metody provedení řazení zohledňující jazykovou verzi pomocí výchozí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="56130-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="56130-104">Jazykovou výsledky vrácené tyto metody se může lišit podle jazykové verze kvůli rozdílům v pořadí řazení.</span><span class="sxs-lookup"><span data-stu-id="56130-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="56130-105">Vyloučit chování zohledňující jazykovou verzi, použijte jednu z přetížení této metody, které přijímá `comparer` parametr.</span><span class="sxs-lookup"><span data-stu-id="56130-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="56130-106">`comparer` Parametr určuje <xref:System.Collections.IComparer> implementaci má být použita při porovnání prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="56130-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="56130-107">Pro parametr, zadejte vlastní invariantní porovnávání třídu, která využívá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="56130-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="56130-108">Příklad vlastní invariantní porovnávání třídy je součástí "Pomocí SortedList Class" v tématu [provádění řetězcových operací nezávislých na jazykové verzi v kolekcích](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) tématu.</span><span class="sxs-lookup"><span data-stu-id="56130-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>  
  
 <span data-ttu-id="56130-109">**Poznámka:** předávání **CultureInfo.InvariantCulture** k porovnání metoda provést porovnání na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="56130-109">**Note** Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="56130-110">Však nevytváří-lingvistické porovnání, například cesty k souborům, klíčů registru a proměnných prostředí.</span><span class="sxs-lookup"><span data-stu-id="56130-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="56130-111">Ani podporuje rozhodnutí o zabezpečení na základě výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="56130-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="56130-112">Lingvistické porovnání nebo podporu pro zabezpečení na základě výsledku rozhodnutí, by aplikace měla používat porovnání metodu, která přijímá <xref:System.StringComparison> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="56130-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="56130-113">Aplikace by pak předat <xref:System.StringComparison.Ordinal>.</span><span class="sxs-lookup"><span data-stu-id="56130-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="56130-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="56130-114">See Also</span></span>  
 <xref:System.Array.Sort%2A?displayProperty=nameWithType>  
 <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>  
 <xref:System.Collections.IComparer>  
 [<span data-ttu-id="56130-115">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="56130-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
