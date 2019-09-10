---
title: Provádění řetězcových operací nezávislých na jazykové verzi v polích
ms.date: 03/30/2017
ms.technology: dotnet-standard
helpviewer_keywords:
- culture-insensitive string operations, in arrays
- arrays [.NET Framework], culture-insensitive string operations
- comparer parameter
ms.assetid: f12922e1-6234-4165-8896-63f0653ab478
author: rpetrusha
ms.author: ronpet
ms.openlocfilehash: b52ff8d72132c1076dfdece5e1ce47bbece37b81
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70855991"
---
# <a name="performing-culture-insensitive-string-operations-in-arrays"></a><span data-ttu-id="349ae-102">Provádění řetězcových operací nezávislých na jazykové verzi v polích</span><span class="sxs-lookup"><span data-stu-id="349ae-102">Performing Culture-Insensitive String Operations in Arrays</span></span>

<span data-ttu-id="349ae-103">Přetížení <xref:System.Array.Sort%2A?displayProperty=nameWithType> metod a <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> provádějí <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> řazení zohledňující jazykovou verzi ve výchozím nastavení pomocí vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="349ae-103">Overloads of the <xref:System.Array.Sort%2A?displayProperty=nameWithType> and <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType> methods perform culture-sensitive sorts by default using the <xref:System.Threading.Thread.CurrentCulture%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="349ae-104">Výsledky závislé na jazykové verzi vracené těmito metodami se mohou v důsledku rozdílů v pořadí řazení lišit podle jazykové verze.</span><span class="sxs-lookup"><span data-stu-id="349ae-104">Culture-sensitive results returned by these methods can vary by culture due to differences in sort orders.</span></span> <span data-ttu-id="349ae-105">Chcete-li eliminovat chování zohledňující jazykovou verzi, použijte jedno z přetížení této metody, která `comparer` přijímá parametr.</span><span class="sxs-lookup"><span data-stu-id="349ae-105">To eliminate culture-sensitive behavior, use one of the overloads of this method that accepts a `comparer` parameter.</span></span> <span data-ttu-id="349ae-106">`comparer` Parametr<xref:System.Collections.IComparer> určuje implementaci, která se má použít při porovnávání prvků v poli.</span><span class="sxs-lookup"><span data-stu-id="349ae-106">The `comparer` parameter specifies the <xref:System.Collections.IComparer> implementation to use when comparing elements in the array.</span></span> <span data-ttu-id="349ae-107">Pro parametr zadejte vlastní třídu pro invariantní porovnávání, která používá <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="349ae-107">For the parameter, specify a custom invariant comparer class that uses <xref:System.Globalization.CultureInfo.InvariantCulture%2A?displayProperty=nameWithType>.</span></span> <span data-ttu-id="349ae-108">Příklad vlastní invariantní třídy porovnávání je k dispozici v tématu "použití třídy SortedList" [v tématu provádění řetězcových operací nezávislých na jazykové verzi v tématu kolekce](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) .</span><span class="sxs-lookup"><span data-stu-id="349ae-108">An example of a custom invariant comparer class is provided in the "Using the SortedList Class" subtopic of the [Performing Culture-Insensitive String Operations in Collections](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations-in-collections.md) topic.</span></span>

> [!NOTE]
> <span data-ttu-id="349ae-109">Předávání **CultureInfo. InvariantCulture** metodě porovnání provádí porovnání nezávislé na jazykové verzi.</span><span class="sxs-lookup"><span data-stu-id="349ae-109">Passing **CultureInfo.InvariantCulture** to a comparison method does perform a culture-insensitive comparison.</span></span> <span data-ttu-id="349ae-110">Nezpůsobuje ale nelingvistické porovnání, například pro cesty k souboru, klíče registru a proměnné prostředí.</span><span class="sxs-lookup"><span data-stu-id="349ae-110">However, it does not cause a non-linguistic comparison, for example, for file paths, registry keys, and environment variables.</span></span> <span data-ttu-id="349ae-111">Ani to nepodporuje rozhodnutí o zabezpečení na základě výsledku porovnání.</span><span class="sxs-lookup"><span data-stu-id="349ae-111">Neither does it support security decisions based on the comparison result.</span></span> <span data-ttu-id="349ae-112">Pro nelingvistické porovnání nebo podporu pro rozhodování o zabezpečení na základě výsledků by aplikace měla používat metodu porovnání, která přijímá <xref:System.StringComparison> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="349ae-112">For a non-linguistic comparison or support for result-based security decisions, the application should use a comparison method that accepts a <xref:System.StringComparison> value.</span></span> <span data-ttu-id="349ae-113">Aplikace by se měla předat <xref:System.StringComparison.Ordinal>.</span><span class="sxs-lookup"><span data-stu-id="349ae-113">The application should then pass <xref:System.StringComparison.Ordinal>.</span></span>

## <a name="see-also"></a><span data-ttu-id="349ae-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="349ae-114">See also</span></span>

- <xref:System.Array.Sort%2A?displayProperty=nameWithType>
- <xref:System.Array.BinarySearch%2A?displayProperty=nameWithType>
- <xref:System.Collections.IComparer>
- [<span data-ttu-id="349ae-115">Provádění řetězcových operací nezávislých na jazykové verzi</span><span class="sxs-lookup"><span data-stu-id="349ae-115">Performing Culture-Insensitive String Operations</span></span>](../../../docs/standard/globalization-localization/performing-culture-insensitive-string-operations.md)
