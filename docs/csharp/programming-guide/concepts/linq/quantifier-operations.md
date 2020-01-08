---
title: Operace kvantifikátoru (C#)
ms.date: 07/20/2015
ms.assetid: 84ac2ac2-7a63-4581-bc4c-14e34be1493b
ms.openlocfilehash: 5c931e0971a2ae7970415905be8772a64a82ee39
ms.sourcegitcommit: 7bc6887ab658550baa78f1520ea735838249345e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/03/2020
ms.locfileid: "75635480"
---
# <a name="quantifier-operations-c"></a><span data-ttu-id="1a679-102">Operace kvantifikátoru (C#)</span><span class="sxs-lookup"><span data-stu-id="1a679-102">Quantifier Operations (C#)</span></span>
<span data-ttu-id="1a679-103">Operace kvantifikátoru vrací <xref:System.Boolean> hodnotu, která označuje, zda některé nebo všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="1a679-103">Quantifier operations return a <xref:System.Boolean> value that indicates whether some or all of the elements in a sequence satisfy a condition.</span></span>  
  
 <span data-ttu-id="1a679-104">Následující ilustrace znázorňuje dvě různé operace kvantifikátoru ve dvou různých zdrojových sekvencích.</span><span class="sxs-lookup"><span data-stu-id="1a679-104">The following illustration depicts two different quantifier operations on two different source sequences.</span></span> <span data-ttu-id="1a679-105">První operace se zeptá, zda je jeden nebo více prvků znaku A a výsledek je `true`.</span><span class="sxs-lookup"><span data-stu-id="1a679-105">The first operation asks if one or more of the elements are the character 'A', and the result is `true`.</span></span> <span data-ttu-id="1a679-106">Druhá operace se zeptá, jestli jsou všechny prvky znakem A a výsledek je `true`.</span><span class="sxs-lookup"><span data-stu-id="1a679-106">The second operation asks if all the elements are the character 'A', and the result is `true`.</span></span>  
  
 ![Operace kvantifikátoru LINQ](./media/quantifier-operations/linq-quantifier-operations.png)  
  
 <span data-ttu-id="1a679-108">Standardní metody operátoru dotazu, které provádějí operace kvantifikátoru, jsou uvedeny v následující části.</span><span class="sxs-lookup"><span data-stu-id="1a679-108">The standard query operator methods that perform quantifier operations are listed in the following section.</span></span>  
  
## <a name="methods"></a><span data-ttu-id="1a679-109">Metody</span><span class="sxs-lookup"><span data-stu-id="1a679-109">Methods</span></span>  
  
|<span data-ttu-id="1a679-110">Název metody</span><span class="sxs-lookup"><span data-stu-id="1a679-110">Method Name</span></span>|<span data-ttu-id="1a679-111">Popis</span><span class="sxs-lookup"><span data-stu-id="1a679-111">Description</span></span>|<span data-ttu-id="1a679-112">C#Syntaxe výrazu dotazu</span><span class="sxs-lookup"><span data-stu-id="1a679-112">C# Query Expression Syntax</span></span>|<span data-ttu-id="1a679-113">Další informace</span><span class="sxs-lookup"><span data-stu-id="1a679-113">More Information</span></span>|  
|-----------------|-----------------|---------------------------------|----------------------|  
|<span data-ttu-id="1a679-114">Všechny</span><span class="sxs-lookup"><span data-stu-id="1a679-114">All</span></span>|<span data-ttu-id="1a679-115">Určuje, zda všechny prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="1a679-115">Determines whether all the elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="1a679-116">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1a679-116">Not applicable.</span></span>|<xref:System.Linq.Enumerable.All%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.All%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1a679-117">Libovolné</span><span class="sxs-lookup"><span data-stu-id="1a679-117">Any</span></span>|<span data-ttu-id="1a679-118">Určuje, zda některé prvky v sekvenci splní podmínku.</span><span class="sxs-lookup"><span data-stu-id="1a679-118">Determines whether any elements in a sequence satisfy a condition.</span></span>|<span data-ttu-id="1a679-119">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1a679-119">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Any%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Any%2A?displayProperty=nameWithType>|  
|<span data-ttu-id="1a679-120">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="1a679-120">Contains</span></span>|<span data-ttu-id="1a679-121">Určuje, zda sekvence obsahuje zadaný element.</span><span class="sxs-lookup"><span data-stu-id="1a679-121">Determines whether a sequence contains a specified element.</span></span>|<span data-ttu-id="1a679-122">Nelze použít.</span><span class="sxs-lookup"><span data-stu-id="1a679-122">Not applicable.</span></span>|<xref:System.Linq.Enumerable.Contains%2A?displayProperty=nameWithType><br /><br /> <xref:System.Linq.Queryable.Contains%2A?displayProperty=nameWithType>|  

## <a name="query-expression-syntax-examples"></a><span data-ttu-id="1a679-123">Příklady syntaxe výrazů dotazů</span><span class="sxs-lookup"><span data-stu-id="1a679-123">Query Expression Syntax Examples</span></span>  
  
### <a name="all"></a><span data-ttu-id="1a679-124">Všechny</span><span class="sxs-lookup"><span data-stu-id="1a679-124">All</span></span>  
<span data-ttu-id="1a679-125">Následující příklad používá `All` ke kontrole, zda mají všechny řetězce určitou délku.</span><span class="sxs-lookup"><span data-stu-id="1a679-125">The following example uses the `All` to check that all strings are of a specific length.</span></span>
  
[!code-csharp[All](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#All)]  
  
### <a name="any"></a><span data-ttu-id="1a679-126">Libovolné</span><span class="sxs-lookup"><span data-stu-id="1a679-126">Any</span></span>  
<span data-ttu-id="1a679-127">Následující příklad používá `Any` ke kontrole, zda jsou všechny řetězce začínat na "o".</span><span class="sxs-lookup"><span data-stu-id="1a679-127">The following example uses the `Any` to check that any strings are start with 'o'.</span></span>  
  
[!code-csharp[Any](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Any)]  
  
### <a name="contains"></a><span data-ttu-id="1a679-128">Obsahuje</span><span class="sxs-lookup"><span data-stu-id="1a679-128">Contains</span></span>  
<span data-ttu-id="1a679-129">Následující příklad používá `Contains` ke kontrole, zda má pole určitý element.</span><span class="sxs-lookup"><span data-stu-id="1a679-129">The following example uses the `Contains` to check an array have a specific element.</span></span>  
  
[!code-csharp[Contains](~/samples/snippets/csharp/VS_Snippets_VBCSharp/CsLINQQuantifier/CS/Quantifier.cs#Contains)]  
  
## <a name="see-also"></a><span data-ttu-id="1a679-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1a679-130">See also</span></span>

- <xref:System.Linq>
- [<span data-ttu-id="1a679-131">Přehled standardních operátorů dotazůC#()</span><span class="sxs-lookup"><span data-stu-id="1a679-131">Standard Query Operators Overview (C#)</span></span>](./standard-query-operators-overview.md)
- [<span data-ttu-id="1a679-132">Dynamické určování filtrů predikátů při běhu</span><span class="sxs-lookup"><span data-stu-id="1a679-132">Dynamically specify predicate filters at runtime</span></span>](../../../linq/dynamically-specify-predicate-filters-at-runtime.md)
- [<span data-ttu-id="1a679-133">Dotazování na věty, které obsahují zadanou sadu slov (LINQ) (C#)</span><span class="sxs-lookup"><span data-stu-id="1a679-133">How to query for sentences that contain a specified set of words (LINQ) (C#)</span></span>](./how-to-query-for-sentences-that-contain-a-specified-set-of-words-linq.md)
