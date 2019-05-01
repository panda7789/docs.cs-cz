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
ms.openlocfilehash: 3d6caeb1938e8e53e8ec2575f740cd5e49496f62
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054416"
---
# <a name="skip-while-clause-visual-basic"></a><span data-ttu-id="ea983-102">Skip While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="ea983-102">Skip While Clause (Visual Basic)</span></span>
<span data-ttu-id="ea983-103">Vynechává prvky v kolekci, tak dlouho, dokud je zadaná podmínka `true` a vrací zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="ea983-103">Bypasses elements in a collection as long as a specified condition is `true` and then returns the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="ea983-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="ea983-104">Syntax</span></span>  
  
```  
Skip While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="ea983-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="ea983-105">Parts</span></span>  
  
|<span data-ttu-id="ea983-106">Termín</span><span class="sxs-lookup"><span data-stu-id="ea983-106">Term</span></span>|<span data-ttu-id="ea983-107">Definice</span><span class="sxs-lookup"><span data-stu-id="ea983-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="ea983-108">Povinný parametr.</span><span class="sxs-lookup"><span data-stu-id="ea983-108">Required.</span></span> <span data-ttu-id="ea983-109">Výraz, který představuje podmínku pro prvky pro testování.</span><span class="sxs-lookup"><span data-stu-id="ea983-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="ea983-110">Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, jako `Integer` má být vyhodnocen jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="ea983-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="ea983-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="ea983-111">Remarks</span></span>  
 <span data-ttu-id="ea983-112">`Skip While` Klauzule vynechává prvky od začátku výsledek dotazu do zadané `expression` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="ea983-112">The `Skip While` clause bypasses elements from the beginning of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="ea983-113">Po `expression` vrátí `false`, dotaz vrátí všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="ea983-113">After `expression` returns `false`, the query returns all the remaining elements.</span></span> <span data-ttu-id="ea983-114">`expression` Se ignoruje pro zbývající výsledky.</span><span class="sxs-lookup"><span data-stu-id="ea983-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="ea983-115">`Skip While` Klauzule se liší od `Where` klauzule in, který `Where` klauzuli lze použít k vyloučení všechny prvky z dotazu, které nesplňují určité podmínky.</span><span class="sxs-lookup"><span data-stu-id="ea983-115">The `Skip While` clause differs from the `Where` clause in that the `Where` clause can be used to exclude all elements from a query that do not meet a particular condition.</span></span> <span data-ttu-id="ea983-116">`Skip While` Klauzule vyloučí prvky pouze až do první podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="ea983-116">The `Skip While` clause excludes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="ea983-117">`Skip While` Klauzule je nejužitečnější při práci s výsledek seřazených dotazů.</span><span class="sxs-lookup"><span data-stu-id="ea983-117">The `Skip While` clause is most useful when you are working with an ordered query result.</span></span>  
  
 <span data-ttu-id="ea983-118">Můžete obejít určitý počet výsledků od začátku výsledku dotazu pomocí `Skip` klauzuli.</span><span class="sxs-lookup"><span data-stu-id="ea983-118">You can bypass a specific number of results from the beginning of a query result by using the `Skip` clause.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea983-119">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea983-119">Example</span></span>  
 <span data-ttu-id="ea983-120">Následující příklad kódu používá `Skip While` klauzule pro vyřazení výsledků, dokud nebude nalezen první zákazníků z USA.</span><span class="sxs-lookup"><span data-stu-id="ea983-120">The following code example uses the `Skip While` clause to bypass results until the first customer from the United States is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbSimpleQuerySamples/VB/QuerySamples1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="ea983-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea983-121">See also</span></span>

- [<span data-ttu-id="ea983-122">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="ea983-122">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)
- [<span data-ttu-id="ea983-123">Dotazy</span><span class="sxs-lookup"><span data-stu-id="ea983-123">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)
- [<span data-ttu-id="ea983-124">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="ea983-124">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)
- [<span data-ttu-id="ea983-125">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="ea983-125">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)
- [<span data-ttu-id="ea983-126">Klauzule Skip</span><span class="sxs-lookup"><span data-stu-id="ea983-126">Skip Clause</span></span>](../../../visual-basic/language-reference/queries/skip-clause.md)
- [<span data-ttu-id="ea983-127">Klauzule Take While</span><span class="sxs-lookup"><span data-stu-id="ea983-127">Take While Clause</span></span>](../../../visual-basic/language-reference/queries/take-while-clause.md)
- [<span data-ttu-id="ea983-128">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="ea983-128">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
