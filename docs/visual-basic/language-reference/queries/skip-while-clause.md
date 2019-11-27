---
title: Skip While – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 47703e445865435f5bf5312c3fe41833ac21aa3f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74333142"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="c4d99-102">Skip While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c4d99-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="c4d99-103">Vynechá prvky v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="c4d99-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c4d99-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c4d99-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="c4d99-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c4d99-105">Parts</span></span>  
  
|<span data-ttu-id="c4d99-106">Termín</span><span class="sxs-lookup"><span data-stu-id="c4d99-106">Term</span></span>|<span data-ttu-id="c4d99-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c4d99-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="c4d99-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="c4d99-108">Required.</span></span> <span data-ttu-id="c4d99-109">Výraz, který představuje podmínku pro testování prvků pro.</span><span class="sxs-lookup"><span data-stu-id="c4d99-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="c4d99-110">Výraz musí vracet `Boolean` hodnotu nebo funkční ekvivalent, jako je například `Integer` pro vyhodnocení jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="c4d99-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c4d99-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c4d99-111">Remarks</span></span>  
 <span data-ttu-id="c4d99-112">Klauzule `Skip While` obchází prvky od začátku výsledku dotazu, dokud zadaný `expression` nevrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="c4d99-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="c4d99-113">Po `expression` vrátí `false`, dotaz vrátí všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="c4d99-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="c4d99-114">`expression` se u zbývajících výsledků ignoruje.</span><span class="sxs-lookup"><span data-stu-id="c4d99-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="c4d99-115">Klauzule `Skip While` se liší od klauzule `Where` v tom, že klauzuli `Where` lze použít k vyloučení všech prvků z dotazu, který nesplňuje určitou podmínku.</span><span class="sxs-lookup"><span data-stu-id="c4d99-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="c4d99-116">Klauzule `Skip While` vyloučí prvky pouze do doby, než první podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="c4d99-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="c4d99-117">Klauzule `Skip While` je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="c4d99-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="c4d99-118">Můžete obejít určitý počet výsledků od začátku výsledku dotazu pomocí klauzule `Skip`.</span><span class="sxs-lookup"><span data-stu-id="c4d99-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c4d99-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="c4d99-119">Example</span></span>  
 <span data-ttu-id="c4d99-120">Následující příklad kódu používá klauzuli `Skip While` pro obejití výsledků, dokud se nenajde první zákazník z USA.</span><span class="sxs-lookup"><span data-stu-id="c4d99-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="c4d99-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c4d99-121">See also</span></span>

- [<span data-ttu-id="c4d99-122">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="c4d99-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="c4d99-123">Dotazy</span><span class="sxs-lookup"><span data-stu-id="c4d99-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="c4d99-124">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="c4d99-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="c4d99-125">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="c4d99-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="c4d99-126">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="c4d99-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="c4d99-127">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="c4d99-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="c4d99-128">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="c4d99-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
