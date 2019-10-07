---
title: Skip While – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QuerySkipWhile
helpviewer_keywords:
- Skip While statement [Visual Basic]
- Skip While clause [Visual Basic]
- queries [Visual Basic], Skip While
ms.assetid: 5dee8350-7520-4f1a-b00d-590cacd572d6
ms.openlocfilehash: 7f37a6fa1c9ba7fdf7978ac6853e4c2985bf72e7
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004709"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="03681-102">Skip While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="03681-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="03681-103">Vynechá prvky v kolekci, pokud je zadaná podmínka `true` a potom vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="03681-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="03681-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="03681-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="03681-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="03681-105">Parts</span></span>  
  
|<span data-ttu-id="03681-106">Termín</span><span class="sxs-lookup"><span data-stu-id="03681-106">Term</span></span>|<span data-ttu-id="03681-107">Definice</span><span class="sxs-lookup"><span data-stu-id="03681-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="03681-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="03681-108">Required.</span></span> <span data-ttu-id="03681-109">Výraz, který představuje podmínku pro testování prvků pro.</span><span class="sxs-lookup"><span data-stu-id="03681-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="03681-110">Výraz musí vracet hodnotu `Boolean` nebo funkční ekvivalent, jako je například `Integer` pro vyhodnocení jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="03681-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="03681-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="03681-111">Remarks</span></span>  
 <span data-ttu-id="03681-112">Klauzule `Skip While` obchází prvky od začátku výsledku dotazu, dokud zadaná `expression` nevrátí hodnotu `false`.</span><span class="sxs-lookup"><span data-stu-id="03681-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="03681-113">Po `expression` vrátí `false`, dotaz vrátí všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="03681-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="03681-114">@No__t-0 se u zbývajících výsledků ignoruje.</span><span class="sxs-lookup"><span data-stu-id="03681-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="03681-115">Klauzule `Skip While` se liší od klauzule `Where` v tom, že klauzuli `Where` lze použít k vyloučení všech prvků z dotazu, který nesplňuje určitou podmínku.</span><span class="sxs-lookup"><span data-stu-id="03681-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="03681-116">Klauzule `Skip While` vyloučí prvky pouze do prvního okamžiku, kdy podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="03681-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="03681-117">Klauzule `Skip While` je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="03681-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="03681-118">Můžete obejít určitý počet výsledků od začátku výsledku dotazu pomocí klauzule `Skip`.</span><span class="sxs-lookup"><span data-stu-id="03681-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="03681-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="03681-119">Example</span></span>  
 <span data-ttu-id="03681-120">Následující příklad kódu používá klauzuli `Skip While` pro obejití výsledků, dokud se nenajde první zákazník z USA.</span><span class="sxs-lookup"><span data-stu-id="03681-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="03681-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="03681-121">See also</span></span>

- [<span data-ttu-id="03681-122">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="03681-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="03681-123">Dotazy</span><span class="sxs-lookup"><span data-stu-id="03681-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="03681-124">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="03681-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="03681-125">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="03681-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="03681-126">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="03681-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="03681-127">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="03681-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="03681-128">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="03681-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
