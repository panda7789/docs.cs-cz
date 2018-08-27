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
ms.openlocfilehash: 181cc641bb12329c898cc3bb226ea49f0836e979
ms.sourcegitcommit: e614e0f3b031293e4107f37f752be43652f3f253
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/26/2018
ms.locfileid: "42932024"
---
# <a name="take-while-clause-visual-basic"></a><span data-ttu-id="9426f-102">Take While – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="9426f-102">Take While Clause (Visual Basic)</span></span>
<span data-ttu-id="9426f-103">Obsahuje elementy v kolekci, tak dlouho, dokud je zadaná podmínka `true` a vynechány zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="9426f-103">Includes elements in a collection as long as a specified condition is `true` and bypasses the remaining elements.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="9426f-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="9426f-104">Syntax</span></span>  
  
```  
Take While expression  
```  
  
## <a name="parts"></a><span data-ttu-id="9426f-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="9426f-105">Parts</span></span>  
  
|<span data-ttu-id="9426f-106">Termín</span><span class="sxs-lookup"><span data-stu-id="9426f-106">Term</span></span>|<span data-ttu-id="9426f-107">Definice</span><span class="sxs-lookup"><span data-stu-id="9426f-107">Definition</span></span>|  
|---|---|  
|`expression`|<span data-ttu-id="9426f-108">Požadováno.</span><span class="sxs-lookup"><span data-stu-id="9426f-108">Required.</span></span> <span data-ttu-id="9426f-109">Výraz, který představuje podmínku pro prvky pro testování.</span><span class="sxs-lookup"><span data-stu-id="9426f-109">An expression that represents a condition to test elements for.</span></span> <span data-ttu-id="9426f-110">Výraz musí vrátit `Boolean` hodnotu nebo funkční ekvivalent, jako `Integer` má být vyhodnocen jako `Boolean`.</span><span class="sxs-lookup"><span data-stu-id="9426f-110">The expression must return a `Boolean` value or a functional equivalent, such as an `Integer` to be evaluated as a `Boolean`.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="9426f-111">Poznámky</span><span class="sxs-lookup"><span data-stu-id="9426f-111">Remarks</span></span>  
 <span data-ttu-id="9426f-112">`Take While` Klauzule obsahuje prvků od začátku výsledek dotazu do zadané `expression` vrátí `false`.</span><span class="sxs-lookup"><span data-stu-id="9426f-112">The `Take While` clause includes elements from the start of a query result until the supplied `expression` returns `false`.</span></span> <span data-ttu-id="9426f-113">Po `expression` vrátí `false`, dotaz bude vynechat všechny zbývající prvky.</span><span class="sxs-lookup"><span data-stu-id="9426f-113">After the `expression` returns `false`, the query will bypass all remaining elements.</span></span> <span data-ttu-id="9426f-114">`expression` Se ignoruje pro zbývající výsledky.</span><span class="sxs-lookup"><span data-stu-id="9426f-114">The `expression` is ignored for the remaining results.</span></span>  
  
 <span data-ttu-id="9426f-115">`Take While` Klauzule se liší od `Where` klauzule in, který `Where` klauzule umožňuje zahrnout všechny prvky z dotazu, které splňují určitou podmínku.</span><span class="sxs-lookup"><span data-stu-id="9426f-115">The `Take While` clause differs from the `Where` clause in that the `Where` clause can be used to include all elements from a query that meet a particular condition.</span></span> <span data-ttu-id="9426f-116">`Take While` Klauzule obsahuje prvky pouze až do první podmínka není splněna.</span><span class="sxs-lookup"><span data-stu-id="9426f-116">The `Take While` clause includes elements only until the first time that the condition is not satisfied.</span></span> <span data-ttu-id="9426f-117">`Take While` Klauzule je nejužitečnější při práci s výsledek seřazených dotazů.</span><span class="sxs-lookup"><span data-stu-id="9426f-117">The `Take While` clause is most useful when you are working with an ordered query result.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9426f-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="9426f-118">Example</span></span>  
 <span data-ttu-id="9426f-119">Následující příklad kódu používá `Take While` klauzule k načtení výsledků, dokud nebude nalezen první zákazníků bez všech objednávek.</span><span class="sxs-lookup"><span data-stu-id="9426f-119">The following code example uses the `Take While` clause to retrieve results until the first customer without any orders is found.</span></span>  
  
 [!code-vb[VbSimpleQuerySamples#2](../../../visual-basic/language-reference/queries/codesnippet/VisualBasic/take-while-clause_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="9426f-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="9426f-120">See Also</span></span>  
 [<span data-ttu-id="9426f-121">Úvod do LINQ v JAZYKU Visual Basic</span><span class="sxs-lookup"><span data-stu-id="9426f-121">Introduction to LINQ in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/linq/introduction-to-linq.md)  
 [<span data-ttu-id="9426f-122">Dotazy</span><span class="sxs-lookup"><span data-stu-id="9426f-122">Queries</span></span>](../../../visual-basic/language-reference/queries/index.md)  
 [<span data-ttu-id="9426f-123">Klauzule Select</span><span class="sxs-lookup"><span data-stu-id="9426f-123">Select Clause</span></span>](../../../visual-basic/language-reference/queries/select-clause.md)  
 [<span data-ttu-id="9426f-124">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="9426f-124">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
 [<span data-ttu-id="9426f-125">Klauzule Take</span><span class="sxs-lookup"><span data-stu-id="9426f-125">Take Clause</span></span>](../../../visual-basic/language-reference/queries/take-clause.md)  
 [<span data-ttu-id="9426f-126">Klauzule Skip While</span><span class="sxs-lookup"><span data-stu-id="9426f-126">Skip While Clause</span></span>](../../../visual-basic/language-reference/queries/skip-while-clause.md)  
 [<span data-ttu-id="9426f-127">Klauzule Where</span><span class="sxs-lookup"><span data-stu-id="9426f-127">Where Clause</span></span>](../../../visual-basic/language-reference/queries/where-clause.md)
