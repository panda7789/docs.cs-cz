---
title: Dotazování klíčová slova - C# odkaz
ms.custom: seodec18
ms.date: 07/20/2015
helpviewer_keywords:
- query keywords [C#]
- LINQ [C#], query keywords
ms.assetid: 6c9bec16-dbd7-4a7c-a060-fe4600b2021f
ms.openlocfilehash: e5010c7e9f3550c79c86c6cab4579a0fb15eef10
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61660876"
---
# <a name="query-keywords-c-reference"></a><span data-ttu-id="d3daf-102">Klíčová slova dotazu (referenční dokumentace jazyka C#)</span><span class="sxs-lookup"><span data-stu-id="d3daf-102">Query keywords (C# Reference)</span></span>

<span data-ttu-id="d3daf-103">Tato část obsahuje kontextová klíčová slova používat ve výrazech dotazů.</span><span class="sxs-lookup"><span data-stu-id="d3daf-103">This section contains the contextual keywords used in query expressions.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="d3daf-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="d3daf-104">In this section</span></span>

|<span data-ttu-id="d3daf-105">Klauzule</span><span class="sxs-lookup"><span data-stu-id="d3daf-105">Clause</span></span>|<span data-ttu-id="d3daf-106">Popis</span><span class="sxs-lookup"><span data-stu-id="d3daf-106">Description</span></span>|
|------------|-----------------|
|[<span data-ttu-id="d3daf-107">z</span><span class="sxs-lookup"><span data-stu-id="d3daf-107">from</span></span>](from-clause.md)|<span data-ttu-id="d3daf-108">Určuje zdroj dat a proměnnou rozsahu (podobně jako na proměnnou iterace).</span><span class="sxs-lookup"><span data-stu-id="d3daf-108">Specifies a data source and a range variable (similar to an iteration variable).</span></span>|
|[<span data-ttu-id="d3daf-109">kde</span><span class="sxs-lookup"><span data-stu-id="d3daf-109">where</span></span>](where-clause.md)|<span data-ttu-id="d3daf-110">Filtry zdrojové prvky založené na jeden nebo více logických výrazů, které jsou odděleny a logický operátor AND nebo operátorů ( `&&` nebo <code>&#124;&#124;</code> ).</span><span class="sxs-lookup"><span data-stu-id="d3daf-110">Filters source elements based on one or more Boolean expressions separated by logical AND and OR operators ( `&&` or <code>&#124;&#124;</code> ).</span></span>|
|[<span data-ttu-id="d3daf-111">select</span><span class="sxs-lookup"><span data-stu-id="d3daf-111">select</span></span>](select-clause.md)|<span data-ttu-id="d3daf-112">Určuje typ a tvar, který prvky ve vrácené posloupnosti budou mít při spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="d3daf-112">Specifies the type and shape that the elements in the returned sequence will have when the query is executed.</span></span>|
|[<span data-ttu-id="d3daf-113">group</span><span class="sxs-lookup"><span data-stu-id="d3daf-113">group</span></span>](group-clause.md)|<span data-ttu-id="d3daf-114">Výsledky dotazu skupin podle zadanou hodnotou klíče.</span><span class="sxs-lookup"><span data-stu-id="d3daf-114">Groups query results according to a specified key value.</span></span>|
|[<span data-ttu-id="d3daf-115">into</span><span class="sxs-lookup"><span data-stu-id="d3daf-115">into</span></span>](into.md)|<span data-ttu-id="d3daf-116">Poskytuje identifikátor, který může sloužit jako odkaz na výsledky spojení, skupiny nebo klauzule select.</span><span class="sxs-lookup"><span data-stu-id="d3daf-116">Provides an identifier that can serve as a reference to the results of a join, group or select clause.</span></span>|
|[<span data-ttu-id="d3daf-117">Řadit podle</span><span class="sxs-lookup"><span data-stu-id="d3daf-117">orderby</span></span>](orderby-clause.md)|<span data-ttu-id="d3daf-118">Výsledky dotazu řazení ve vzestupném nebo sestupném pořadí podle výchozí porovnávací metody pro typ elementu.</span><span class="sxs-lookup"><span data-stu-id="d3daf-118">Sorts query results in ascending or descending order based on the default comparer for the element type.</span></span>|
|[<span data-ttu-id="d3daf-119">join</span><span class="sxs-lookup"><span data-stu-id="d3daf-119">join</span></span>](join-clause.md)|<span data-ttu-id="d3daf-120">Spojí dva zdroje dat založené na porovnání rovnosti mezi dvěma zadaným odpovídající kritériím.</span><span class="sxs-lookup"><span data-stu-id="d3daf-120">Joins two data sources based on an equality comparison between two specified matching criteria.</span></span>|
|[<span data-ttu-id="d3daf-121">let</span><span class="sxs-lookup"><span data-stu-id="d3daf-121">let</span></span>](let-clause.md)|<span data-ttu-id="d3daf-122">Představuje proměnnou rozsahu pro ukládání výsledků dílčí výraz ve výrazu dotazu.</span><span class="sxs-lookup"><span data-stu-id="d3daf-122">Introduces a range variable to store sub-expression results in a query expression.</span></span>|
|[<span data-ttu-id="d3daf-123">in</span><span class="sxs-lookup"><span data-stu-id="d3daf-123">in</span></span>](in.md)|<span data-ttu-id="d3daf-124">Kontextové klíčové slovo v [spojení](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3daf-124">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="d3daf-125">on</span><span class="sxs-lookup"><span data-stu-id="d3daf-125">on</span></span>](on.md)|<span data-ttu-id="d3daf-126">Kontextové klíčové slovo v [spojení](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3daf-126">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="d3daf-127">equals</span><span class="sxs-lookup"><span data-stu-id="d3daf-127">equals</span></span>](equals.md)|<span data-ttu-id="d3daf-128">Kontextové klíčové slovo v [spojení](join-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3daf-128">Contextual keyword in a [join](join-clause.md) clause.</span></span>|
|[<span data-ttu-id="d3daf-129">by</span><span class="sxs-lookup"><span data-stu-id="d3daf-129">by</span></span>](by.md)|<span data-ttu-id="d3daf-130">Kontextové klíčové slovo v [skupiny](group-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3daf-130">Contextual keyword in a [group](group-clause.md) clause.</span></span>|
|[<span data-ttu-id="d3daf-131">ascending</span><span class="sxs-lookup"><span data-stu-id="d3daf-131">ascending</span></span>](ascending.md)|<span data-ttu-id="d3daf-132">Kontextové klíčové slovo v [orderby](orderby-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3daf-132">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|
|[<span data-ttu-id="d3daf-133">descending</span><span class="sxs-lookup"><span data-stu-id="d3daf-133">descending</span></span>](descending.md)|<span data-ttu-id="d3daf-134">Kontextové klíčové slovo v [orderby](orderby-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="d3daf-134">Contextual keyword in an [orderby](orderby-clause.md) clause.</span></span>|

## <a name="see-also"></a><span data-ttu-id="d3daf-135">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d3daf-135">See also</span></span>

- [<span data-ttu-id="d3daf-136">Klíčová slova jazyka C#</span><span class="sxs-lookup"><span data-stu-id="d3daf-136">C# Keywords</span></span>](index.md)
- [<span data-ttu-id="d3daf-137">LINQ (Language-Integrated Query)</span><span class="sxs-lookup"><span data-stu-id="d3daf-137">LINQ (Language-Integrated Query)</span></span>](../../programming-guide/concepts/linq/index.md)
- [<span data-ttu-id="d3daf-138">LINQ – výrazy dotazů</span><span class="sxs-lookup"><span data-stu-id="d3daf-138">LINQ Query Expressions</span></span>](../../../csharp/programming-guide/linq-query-expressions/index.md)
- [<span data-ttu-id="d3daf-139">Začínáme s dotazy LINQ v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="d3daf-139">Getting Started with LINQ in C#</span></span>](../../../csharp/programming-guide/concepts/linq/getting-started-with-linq.md)