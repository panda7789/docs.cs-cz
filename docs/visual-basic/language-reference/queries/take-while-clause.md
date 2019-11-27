---
title: Take While – klauzule
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: 23b7c84a9f896161a66059fcb1f30753d3b863d5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74347102"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="0ed50-102">Take While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="0ed50-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="0ed50-103">Obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="0ed50-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="0ed50-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="0ed50-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="0ed50-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="0ed50-105">Parts</span></span>  
  
|<span data-ttu-id="0ed50-106">Termín</span><span class="sxs-lookup"><span data-stu-id="0ed50-106">Term</span></span>|<span data-ttu-id="0ed50-107">Definice</span><span class="sxs-lookup"><span data-stu-id="0ed50-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="0ed50-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="0ed50-108">Required.</span></span> <span data-ttu-id="0ed50-109">Výraz, který představuje podmínku pro testování prvků pro.</span><span class="sxs-lookup"><span data-stu-id="0ed50-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="0ed50-110">Výraz musí vracet `Boolean` hodnotu nebo funkční ekvivalent, jako je například `Integer` pro vyhodnocení jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="0ed50-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="0ed50-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="0ed50-111">Remarks</span></span>  
 <span data-ttu-id="0ed50-112">Klauzule `Take While` obsahuje prvky z začátek výsledku dotazu, dokud zadaný `expression` nevrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="0ed50-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="0ed50-113">Po `expression` vrátí `false`, dotaz vynechá všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="0ed50-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="0ed50-114">`expression` se u zbývajících výsledků ignoruje.</span><span class="sxs-lookup"><span data-stu-id="0ed50-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="0ed50-115">Klauzule `Take While` se liší od klauzule `Where` v tom, že klauzuli `Where` lze použít k zahrnutí všech prvků z dotazu, který splňuje určitou podmínku.</span><span class="sxs-lookup"><span data-stu-id="0ed50-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="0ed50-116">Klauzule `Take While` obsahuje prvky pouze do doby, než první podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="0ed50-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="0ed50-117">Klauzule `Take While` je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="0ed50-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0ed50-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="0ed50-118">Example</span></span>  
 <span data-ttu-id="0ed50-119">Následující příklad kódu používá klauzuli `Take While` k načtení výsledků, dokud se nenajde první zákazník bez jakýchkoli objednávek.</span><span class="sxs-lookup"><span data-stu-id="0ed50-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="0ed50-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="0ed50-120">See also</span></span>

- [<span data-ttu-id="0ed50-121">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="0ed50-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="0ed50-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="0ed50-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="0ed50-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="0ed50-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="0ed50-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="0ed50-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="0ed50-125">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="0ed50-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="0ed50-126">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="0ed50-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="0ed50-127">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="0ed50-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
