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
ms.openlocfilehash: 4b6133efdbd9c46ab85201ad454671e5538b6a81
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84359577"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="62aa0-102">Take While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="62aa0-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="62aa0-103">Obsahuje prvky v kolekci, pokud je zadaná podmínka `true` a obchází zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="62aa0-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="62aa0-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="62aa0-104">Syntax</span></span>  
  
```vb  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="62aa0-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="62aa0-105">Parts</span></span>  
  
|<span data-ttu-id="62aa0-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="62aa0-106">Term</span></span>|<span data-ttu-id="62aa0-107">Definice</span><span class="sxs-lookup"><span data-stu-id="62aa0-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="62aa0-108">Povinná hodnota.</span><span class="sxs-lookup"><span data-stu-id="62aa0-108">Required.</span></span> <span data-ttu-id="62aa0-109">Výraz, který představuje podmínku pro testování prvků pro.</span><span class="sxs-lookup"><span data-stu-id="62aa0-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="62aa0-110">Výraz musí vracet `Boolean` hodnotu nebo funkční ekvivalent, jako je například, aby se `Integer` vyhodnotil jako `Boolean` .</span><span class="sxs-lookup"><span data-stu-id="62aa0-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="62aa0-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="62aa0-111">Remarks</span></span>  
 <span data-ttu-id="62aa0-112">`Take While`Klauzule obsahuje prvky z začátek výsledku dotazu, dokud se nevrátí dodaný `expression` výsledek `false` .</span><span class="sxs-lookup"><span data-stu-id="62aa0-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="62aa0-113">Po `expression` vrácení `false` bude dotaz obejít všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="62aa0-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="62aa0-114">U `expression` zbývajících výsledků se ignoruje.</span><span class="sxs-lookup"><span data-stu-id="62aa0-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="62aa0-115">`Take While`Klauzule se liší od `Where` klauzule v tom, že `Where` klauzuli lze použít k zahrnutí všech prvků z dotazu, který splňuje určitou podmínku.</span><span class="sxs-lookup"><span data-stu-id="62aa0-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="62aa0-116">`Take While`Klauzule obsahuje prvky pouze do doby, než první podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="62aa0-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="62aa0-117">`Take While`Klauzule je nejužitečnější, když pracujete s výsledkem seřazeného dotazu.</span><span class="sxs-lookup"><span data-stu-id="62aa0-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="62aa0-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="62aa0-118">Example</span></span>  
 <span data-ttu-id="62aa0-119">Následující příklad kódu používá `Take While` klauzuli pro načtení výsledků, dokud se nenajde první zákazník bez jakýchkoli objednávek.</span><span class="sxs-lookup"><span data-stu-id="62aa0-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#2)]  
  
## <a name="see-also"></a><span data-ttu-id="62aa0-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="62aa0-120">See also</span></span>

- [<span data-ttu-id="62aa0-121">Představení technologie LINQ v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="62aa0-121">Introduction to LINQ in Visual Basic</span></span>](../../programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="62aa0-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="62aa0-122">Queries</span></span>](index.md)
- [<span data-ttu-id="62aa0-123">Klauzule SELECT</span><span class="sxs-lookup"><span data-stu-id="62aa0-123">Select Clause</span></span>](select-clause.md)
- [<span data-ttu-id="62aa0-124">Klauzule FROM</span><span class="sxs-lookup"><span data-stu-id="62aa0-124">From Clause</span></span>](from-clause.md)
- [<span data-ttu-id="62aa0-125">Take – klauzule</span><span class="sxs-lookup"><span data-stu-id="62aa0-125">Take Clause</span></span>](take-clause.md)
- [<span data-ttu-id="62aa0-126">Skip While – klauzule</span><span class="sxs-lookup"><span data-stu-id="62aa0-126">Skip While Clause</span></span>](skip-while-clause.md)
- [<span data-ttu-id="62aa0-127">Klauzule WHERE</span><span class="sxs-lookup"><span data-stu-id="62aa0-127">Where Clause</span></span>](where-clause.md)
