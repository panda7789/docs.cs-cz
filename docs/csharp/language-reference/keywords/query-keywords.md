---
title: Klíčová slova dotazu (referenční dokumentace jazyka C#)
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: 9ec163e1de018bd87348a5b39a1f34654d7d6d84
ms.sourcegitcommit: 3c1c3ba79895335ff3737934e39372555ca7d6d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/06/2018
ms.locfileid: "43859065"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="9a910-102">Klíčová slova dotazu (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="9a910-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="9a910-103">Tato část obsahuje kontextová klíčová slova používat ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="9a910-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="9a910-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9a910-104">In this section</span></span>

|<span data-ttu-id="9a910-105">Klauzule</span><span class="sxs-lookup"><span data-stu-id="9a910-105">Clause</span></span>|<span data-ttu-id="9a910-106">Popis</span><span class="sxs-lookup"><span data-stu-id="9a910-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="9a910-107">z</span><span class="sxs-lookup"><span data-stu-id="9a910-107">from</span></span>](from-clause.md)|<span data-ttu-id="9a910-108">Určuje zdroj dat a proměnnou rozsahu (podobně jako na proměnnou iterace).</span><span class="sxs-lookup"><span data-stu-id="9a910-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="9a910-109">kde</span><span class="sxs-lookup"><span data-stu-id="9a910-109">where</span></span>](where-clause.md)|<span data-ttu-id="9a910-110">Filtry zdrojové prvky založené na jeden nebo více logických výrazů, které jsou odděleny a logický operátor AND nebo operátorů ( `&&` nebo <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="9a910-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="9a910-111">Vyberte</span><span class="sxs-lookup"><span data-stu-id="9a910-111">select</span></span>](select-clause.md)|<span data-ttu-id="9a910-112">Určuje typ a tvar, který prvky ve vrácené posloupnosti budou mít při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="9a910-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="9a910-113">Skupiny</span><span class="sxs-lookup"><span data-stu-id="9a910-113">group</span></span>](group-clause.md)|<span data-ttu-id="9a910-114">Výsledky dotazu skupin podle zadanou hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="9a910-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="9a910-115">into</span><span class="sxs-lookup"><span data-stu-id="9a910-115">into</span></span>](into.md)|<span data-ttu-id="9a910-116">Poskytuje identifikátor, který může sloužit jako odkaz na výsledky spojení, skupiny nebo klauzule select.</span><span class="sxs-lookup"><span data-stu-id="9a910-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="9a910-117">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="9a910-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="9a910-118">Výsledky dotazu řazení ve vzestupném nebo sestupném pořadí podle výchozí porovnávací metody pro typ elementu.</span><span class="sxs-lookup"><span data-stu-id="9a910-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="9a910-119">Připojte se k</span><span class="sxs-lookup"><span data-stu-id="9a910-119">join</span></span>](join-clause.md)|<span data-ttu-id="9a910-120">Spojí dva zdroje dat založené na porovnání rovnosti mezi dvěma zadaným odpovídající kritériím.</span><span class="sxs-lookup"><span data-stu-id="9a910-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="9a910-121">let</span><span class="sxs-lookup"><span data-stu-id="9a910-121">let</span></span>](let-clause.md)|<span data-ttu-id="9a910-122">Představuje proměnnou rozsahu pro ukládání výsledků dílčí výraz ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="9a910-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="9a910-123">in</span><span class="sxs-lookup"><span data-stu-id="9a910-123">in</span></span>](in.md)|<span data-ttu-id="9a910-124">Kontextové klíčové slovo v [spojení](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9a910-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="9a910-125">on</span><span class="sxs-lookup"><span data-stu-id="9a910-125">on</span></span>](on.md)|<span data-ttu-id="9a910-126">Kontextové klíčové slovo v [spojení](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9a910-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="9a910-127">equals</span><span class="sxs-lookup"><span data-stu-id="9a910-127">equals</span></span>](equals.md)|<span data-ttu-id="9a910-128">Kontextové klíčové slovo v [spojení](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9a910-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="9a910-129">by</span><span class="sxs-lookup"><span data-stu-id="9a910-129">by</span></span>](by.md)|<span data-ttu-id="9a910-130">Kontextové klíčové slovo v [skupiny](group-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9a910-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="9a910-131">ascending</span><span class="sxs-lookup"><span data-stu-id="9a910-131">ascending</span></span>](ascending.md)|<span data-ttu-id="9a910-132">Kontextové klíčové slovo v [orderby](orderby-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9a910-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="9a910-133">descending</span><span class="sxs-lookup"><span data-stu-id="9a910-133">descending</span></span>](descending.md)|<span data-ttu-id="9a910-134">Kontextové klíčové slovo v [orderby](orderby-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="9a910-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="9a910-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9a910-135">See also</span></span>

- [<span data-ttu-id="9a910-136">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="9a910-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="9a910-137">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="9a910-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="9a910-138">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="9a910-138">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="9a910-139">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="9a910-139">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)