---
title: Operace kvantifikátoru (C#)
description: Přečtěte si o operacích kvantifikátoru. Tyto operace vrátí logickou hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: ce06f887d3ad7b10cbdedf9e33072df2c0819ef1
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87299146"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="7c2f7-104">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="7c2f7-104">Quantifier Operations (C#)</span></span>
<span data-ttu-id="7c2f7-105">Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-105">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="7c2f7-106">Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-106">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="7c2f7-107">První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true` .</span><span class="sxs-lookup"><span data-stu-id="7c2f7-107">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="7c2f7-108">Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true` .</span><span class="sxs-lookup"><span data-stu-id="7c2f7-108">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="7c2f7-110">Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-110">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="7c2f7-111">Metody</span><span class="sxs-lookup"><span data-stu-id="7c2f7-111">Methods</span></span>  
  
|<span data-ttu-id="7c2f7-112">Název metody</span><span class="sxs-lookup"><span data-stu-id="7c2f7-112">Method Name</span></span>|<span data-ttu-id="7c2f7-113">Popis</span><span class="sxs-lookup"><span data-stu-id="7c2f7-113">Description</span></span>|<span data-ttu-id="7c2f7-114">Syntaxe výrazu dotazu v jazyce C#</span><span class="sxs-lookup"><span data-stu-id="7c2f7-114">C# Query Expression Syntax</span></span>|<span data-ttu-id="7c2f7-115">Další informace</span><span class="sxs-lookup"><span data-stu-id="7c2f7-115">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="7c2f7-116">Vše</span><span class="sxs-lookup"><span data-stu-id="7c2f7-116">All</span></span>|<span data-ttu-id="7c2f7-117">Určuje, zda všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-117">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="7c2f7-118">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-118">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7c2f7-119">Libovolný</span><span class="sxs-lookup"><span data-stu-id="7c2f7-119">Any</span></span>|<span data-ttu-id="7c2f7-120">Určuje, zda některé prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-120">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="7c2f7-121">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-121">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="7c2f7-122">Contains</span><span class="sxs-lookup"><span data-stu-id="7c2f7-122">Contains</span></span>|<span data-ttu-id="7c2f7-123">Určuje, zda sekvence obsahuje zadaný element.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-123">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="7c2f7-124">Neužívá se.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-124">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="7c2f7-125">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="7c2f7-125">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="7c2f7-126">Vše</span><span class="sxs-lookup"><span data-stu-id="7c2f7-126">All</span></span>  
<span data-ttu-id="7c2f7-127">Následující příklad používá `All` ke kontrole, zda mají všechny řetězce určitou délku.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-127">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="7c2f7-128">Libovolný</span><span class="sxs-lookup"><span data-stu-id="7c2f7-128">Any</span></span>  
<span data-ttu-id="7c2f7-129">Následující příklad používá `Any` ke kontrole, zda jsou všechny řetězce začínat na "o".</span><span class="sxs-lookup"><span data-stu-id="7c2f7-129">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="7c2f7-130">Contains</span><span class="sxs-lookup"><span data-stu-id="7c2f7-130">Contains</span></span>  
<span data-ttu-id="7c2f7-131">Následující příklad používá `Contains` ke kontrole, zda pole má určitý element.</span><span class="sxs-lookup"><span data-stu-id="7c2f7-131">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="7c2f7-132">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7c2f7-132">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="7c2f7-133">Přehled standardních operátorů dotazů (C#)</span><span class="sxs-lookup"><span data-stu-id="7c2f7-133">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="7c2f7-134">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="7c2f7-134">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="7c2f7-135">Dotazování na věty, které obsahují zadanou sadu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="7c2f7-135">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
