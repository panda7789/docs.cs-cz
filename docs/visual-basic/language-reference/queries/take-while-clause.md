---
title: Take While – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.QueryTakeWhile
helpviewer_keywords:
- queries [Visual Basic], Take While
- Take While clause [Visual Basic]
- Take While statement [Visual Basic]
ms.assetid: db8f9f2f-fc9f-4a6c-b0b8-1bf048147e11
ms.openlocfilehash: fe6ee470698504bc0434930cc9aa6de712e04254
ms.sourcegitcommit: eff6adb61852369ab690f3f047818c90580e7eb1
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/07/2019
ms.locfileid: "72004671"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="d6893-102">Take While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="d6893-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="d6893-103">Obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="d6893-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d6893-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d6893-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="d6893-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d6893-105">Parts</span></span>  
  
|<span data-ttu-id="d6893-106">Termín</span><span class="sxs-lookup"><span data-stu-id="d6893-106">Term</span></span>|<span data-ttu-id="d6893-107">Definice</span><span class="sxs-lookup"><span data-stu-id="d6893-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="d6893-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="d6893-108">Required.</span></span> <span data-ttu-id="d6893-109">Výraz, který představuje podmínku pro testování prvků pro.</span><span class="sxs-lookup"><span data-stu-id="d6893-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="d6893-110">Výraz musí vracet hodnotu `Boolean` nebo funkční ekvivalent, jako je například `Integer` pro vyhodnocení jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="d6893-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="d6893-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d6893-111">Remarks</span></span>  
 <span data-ttu-id="d6893-112">Klauzule `Take While` obsahuje prvky od začátku výsledku dotazu, dokud zadaná `expression` nevrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="d6893-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="d6893-113">Po `expression` vrátí `false`, dotaz vynechá všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="d6893-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="d6893-114">@No__t-0 se u zbývajících výsledků ignoruje.</span><span class="sxs-lookup"><span data-stu-id="d6893-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="d6893-115">Klauzule `Take While` se liší od klauzule `Where` v tom, že klauzuli `Where` lze použít k zahrnutí všech prvků z dotazu, který splňuje určitou podmínku.</span><span class="sxs-lookup"><span data-stu-id="d6893-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="d6893-116">Klauzule `Take While` obsahuje prvky pouze do doby, než první podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="d6893-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="d6893-117">Klauzule `Take While` je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="d6893-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d6893-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d6893-118">Example</span></span>  
 <span data-ttu-id="d6893-119">Následující příklad kódu používá klauzuli `Take While` pro načtení výsledků, dokud se nenajde první zákazník bez jakýchkoli objednávek.</span><span class="sxs-lookup"><span data-stu-id="d6893-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="d6893-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6893-120">See also</span></span>

- [<span data-ttu-id="d6893-121">Úvod do jazyka LINQ v Visual Basic</span><span class="sxs-lookup"><span data-stu-id="d6893-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="d6893-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="d6893-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="d6893-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="d6893-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="d6893-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="d6893-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="d6893-125">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="d6893-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="d6893-126">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="d6893-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="d6893-127">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="d6893-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
