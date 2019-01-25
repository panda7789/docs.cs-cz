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
ms.openlocfilehash: 3dfb70066d88683e60f3bf4199441ab3024ef36c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54565105"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="b559d-102">Take While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b559d-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="b559d-103">Obsahuje elementy v kolekci, tak dlouho, dokud je zadaná podmínka `true` a vynechány zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="b559d-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="b559d-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="b559d-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="b559d-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="b559d-105">Parts</span></span>  
  
|<span data-ttu-id="b559d-106">Termín</span><span class="sxs-lookup"><span data-stu-id="b559d-106">Term</span></span>|<span data-ttu-id="b559d-107">Definice</span><span class="sxs-lookup"><span data-stu-id="b559d-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="b559d-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="b559d-108">Required.</span></span> <span data-ttu-id="b559d-109">Výraz, který představuje podmínku pro prvky pro testování.</span><span class="sxs-lookup"><span data-stu-id="b559d-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="b559d-110">Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, jako `Integer` má být vyhodnocen jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="b559d-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="b559d-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="b559d-111">Remarks</span></span>  
 <span data-ttu-id="b559d-112">`Take While` Klauzule obsahuje prvků od začátku výsledek dotazu do zadané `expression` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="b559d-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="b559d-113">Po `expression` vrátí `false`, dotaz bude vynechat všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="b559d-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="b559d-114">`expression` Se ignoruje pro zbývající výsledky.</span><span class="sxs-lookup"><span data-stu-id="b559d-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="b559d-115">`Take While` Klauzule se liší od `Where` klauzule in, který `Where` klauzule umožňuje zahrnout všechny prvky z dotazu, které splňují určitou podmínku.</span><span class="sxs-lookup"><span data-stu-id="b559d-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="b559d-116">`Take While` Klauzule obsahuje prvky pouze až do první podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="b559d-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="b559d-117">`Take While` Klauzule je nejužitečnější při práci s výsledek seřazených dotazů.</span><span class="sxs-lookup"><span data-stu-id="b559d-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b559d-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="b559d-118">Example</span></span>  
 <span data-ttu-id="b559d-119">Následující příklad kódu používá `Take While` klauzule k načtení výsledků, dokud nebude nalezen první zákazníků bez všech objednávek.</span><span class="sxs-lookup"><span data-stu-id="b559d-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="b559d-120">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b559d-120">See also</span></span>
- [<span data-ttu-id="b559d-121">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="b559d-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="b559d-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="b559d-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="b559d-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="b559d-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="b559d-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="b559d-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="b559d-125">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="b559d-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)
- [<span data-ttu-id="b559d-126">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="b559d-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)
- [<span data-ttu-id="b559d-127">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="b559d-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
