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
ms.openlocfilehash: b357320a92ace1b7a261991737ed653d54d0eeab
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359642"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="aae4e-102">Skip While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="aae4e-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="aae4e-103">Vynechá prvky v kolekci, pokud je zadaná podmínka `true` a vrátí zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="aae4e-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="aae4e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="aae4e-104">Syntax</span></span>  
  
```vb  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="aae4e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="aae4e-105">Parts</span></span>  
  
|<span data-ttu-id="aae4e-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="aae4e-106">Term</span></span>|<span data-ttu-id="aae4e-107">Definice</span><span class="sxs-lookup"><span data-stu-id="aae4e-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="aae4e-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="aae4e-108">Required.</span></span> <span data-ttu-id="aae4e-109">Výraz, který představuje podmínku pro testování prvků pro.</span><span class="sxs-lookup"><span data-stu-id="aae4e-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="aae4e-110">Výraz musí vracet `Boolean` hodnotu nebo funkční ekvivalent, jako je například, aby se `Integer` vyhodnotil jako `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="aae4e-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="aae4e-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="aae4e-111">Remarks</span></span>  
 <span data-ttu-id="aae4e-112">`Skip While`Klauzule vynechává prvky od začátku výsledku dotazu, dokud se nevrátí zadané výsledky `expression` `false` .</span><span class="sxs-lookup"><span data-stu-id="aae4e-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="aae4e-113">Po `expression` návratu `false` dotaz vrátí všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="aae4e-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="aae4e-114">U `expression` zbývajících výsledků se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="aae4e-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="aae4e-115">`Skip While`Klauzule se liší od `Where` klauzule v tom, že `Where` klauzuli lze použít k vyloučení všech prvků z dotazu, který nesplňuje určitou podmínku.</span><span class="sxs-lookup"><span data-stu-id="aae4e-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="aae4e-116">`Skip While`Klauzule vyloučí prvky pouze do prvního okamžiku, kdy podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="aae4e-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="aae4e-117">`Skip While`Klauzule je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="aae4e-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="aae4e-118">Můžete obejít určitý počet výsledků od začátku výsledku dotazu pomocí `Skip` klauzule.</span><span class="sxs-lookup"><span data-stu-id="aae4e-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aae4e-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="aae4e-119">Example</span></span>  
 <span data-ttu-id="aae4e-120">Následující příklad kódu používá `Skip While` klauzuli pro obejití výsledků, dokud se nenajde první zákazník z USA.</span><span class="sxs-lookup"><span data-stu-id="aae4e-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="aae4e-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="aae4e-121">See also</span></span>

- [<span data-ttu-id="aae4e-122">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aae4e-122">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="aae4e-123">Dotazy</span><span class="sxs-lookup"><span data-stu-id="aae4e-123">Queries</span></span>](index.md)
- [<span data-ttu-id="aae4e-124">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="aae4e-124">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="aae4e-125">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="aae4e-125">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="aae4e-126">Skip – klauzule</span><span class="sxs-lookup"><span data-stu-id="aae4e-126">Skip Clause</span></span>](skip-clause.md)
- [<span data-ttu-id="aae4e-127">Take While – klauzule</span><span class="sxs-lookup"><span data-stu-id="aae4e-127">Take While Clause</span></span>](take-while-clause.md)
- [<span data-ttu-id="aae4e-128">Klauzule WHERE</span><span class="sxs-lookup"><span data-stu-id="aae4e-128">Where Clause</span></span>](where-clause.md)
