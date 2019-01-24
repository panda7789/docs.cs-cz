---
title: As – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.as
helpviewer_keywords:
- constraints, Visual Basic generic types
- As keyword [Visual Basic], statement syntax
- As keyword [Visual Basic]
ms.assetid: b4281ec8-2be5-49f7-aae8-ae0a96265b0d
ms.openlocfilehash: 893df117ce6ead444ef1da262782cc271102f4d7
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54672263"
---
# <a name="as-clause-visual-basic"></a><span data-ttu-id="7ab57-102">As – klauzule (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="7ab57-102">As Clause (Visual Basic)</span></span>
<span data-ttu-id="7ab57-103">Zavádí `As` klauzuli, která určuje datový typ v příkazu deklarace nebo v seznamu omezení na parametr obecného typu.</span><span class="sxs-lookup"><span data-stu-id="7ab57-103">Introduces an `As` clause, which identifies a data type in a declaration statement or a constraint list on a generic type parameter.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="7ab57-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7ab57-104">Remarks</span></span>  
 <span data-ttu-id="7ab57-105">`As` – Klíčové slovo lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="7ab57-105">The `As` keyword can be used in these contexts:</span></span>  
  
 [<span data-ttu-id="7ab57-106">Klauzule Aggregate</span><span class="sxs-lookup"><span data-stu-id="7ab57-106">Aggregate Clause</span></span>](../../../visual-basic/language-reference/queries/aggregate-clause.md)  
  
 [<span data-ttu-id="7ab57-107">Příkaz Class</span><span class="sxs-lookup"><span data-stu-id="7ab57-107">Class Statement</span></span>](../../../visual-basic/language-reference/statements/class-statement.md)  
  
 [<span data-ttu-id="7ab57-108">Příkaz Const</span><span class="sxs-lookup"><span data-stu-id="7ab57-108">Const Statement</span></span>](../../../visual-basic/language-reference/statements/const-statement.md)  
  
 [<span data-ttu-id="7ab57-109">Příkaz Declare</span><span class="sxs-lookup"><span data-stu-id="7ab57-109">Declare Statement</span></span>](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [<span data-ttu-id="7ab57-110">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="7ab57-110">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)  
  
 [<span data-ttu-id="7ab57-111">Příkaz Dim</span><span class="sxs-lookup"><span data-stu-id="7ab57-111">Dim Statement</span></span>](../../../visual-basic/language-reference/statements/dim-statement.md)  
  
 [<span data-ttu-id="7ab57-112">Příkaz Enum</span><span class="sxs-lookup"><span data-stu-id="7ab57-112">Enum Statement</span></span>](../../../visual-basic/language-reference/statements/enum-statement.md)  
  
 [<span data-ttu-id="7ab57-113">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="7ab57-113">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
  
 [<span data-ttu-id="7ab57-114">Pro... Next – příkazy</span><span class="sxs-lookup"><span data-stu-id="7ab57-114">For...Next Statements</span></span>](../../../visual-basic/language-reference/statements/for-next-statement.md)  
  
 [<span data-ttu-id="7ab57-115">Pro každý... Next – příkazy</span><span class="sxs-lookup"><span data-stu-id="7ab57-115">For Each...Next Statements</span></span>](../../../visual-basic/language-reference/statements/for-each-next-statement.md)  
  
 [<span data-ttu-id="7ab57-116">Klauzule From</span><span class="sxs-lookup"><span data-stu-id="7ab57-116">From Clause</span></span>](../../../visual-basic/language-reference/queries/from-clause.md)  
  
 [<span data-ttu-id="7ab57-117">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="7ab57-117">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [<span data-ttu-id="7ab57-118">Klauzule Group Join</span><span class="sxs-lookup"><span data-stu-id="7ab57-118">Group Join Clause</span></span>](../../../visual-basic/language-reference/queries/group-join-clause.md)  
  
 [<span data-ttu-id="7ab57-119">Příkaz Interface</span><span class="sxs-lookup"><span data-stu-id="7ab57-119">Interface Statement</span></span>](../../../visual-basic/language-reference/statements/interface-statement.md)  
  
 [<span data-ttu-id="7ab57-120">Příkaz Operator</span><span class="sxs-lookup"><span data-stu-id="7ab57-120">Operator Statement</span></span>](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [<span data-ttu-id="7ab57-121">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="7ab57-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [<span data-ttu-id="7ab57-122">Příkaz Structure</span><span class="sxs-lookup"><span data-stu-id="7ab57-122">Structure Statement</span></span>](../../../visual-basic/language-reference/statements/structure-statement.md)  
  
 [<span data-ttu-id="7ab57-123">Příkaz Sub</span><span class="sxs-lookup"><span data-stu-id="7ab57-123">Sub Statement</span></span>](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
 [<span data-ttu-id="7ab57-124">Try... Catch... Finally – příkazy</span><span class="sxs-lookup"><span data-stu-id="7ab57-124">Try...Catch...Finally Statements</span></span>](../../../visual-basic/language-reference/statements/try-catch-finally-statement.md)  
  
## <a name="see-also"></a><span data-ttu-id="7ab57-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7ab57-125">See also</span></span>
- [<span data-ttu-id="7ab57-126">Postupy: Vytvoření nové proměnné</span><span class="sxs-lookup"><span data-stu-id="7ab57-126">How to: Create a New Variable</span></span>](../../../visual-basic/programming-guide/language-features/variables/how-to-create-a-new-variable.md)
- [<span data-ttu-id="7ab57-127">Datové typy</span><span class="sxs-lookup"><span data-stu-id="7ab57-127">Data Types</span></span>](../../../visual-basic/programming-guide/language-features/data-types/index.md)
- [<span data-ttu-id="7ab57-128">Deklarace proměnné</span><span class="sxs-lookup"><span data-stu-id="7ab57-128">Variable Declaration</span></span>](../../../visual-basic/programming-guide/language-features/variables/variable-declaration.md)
- [<span data-ttu-id="7ab57-129">Seznam typů</span><span class="sxs-lookup"><span data-stu-id="7ab57-129">Type List</span></span>](../../../visual-basic/language-reference/statements/type-list.md)
- [<span data-ttu-id="7ab57-130">Obecné typy v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="7ab57-130">Generic Types in Visual Basic</span></span>](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [<span data-ttu-id="7ab57-131">Klíčová slova</span><span class="sxs-lookup"><span data-stu-id="7ab57-131">Keywords</span></span>](../../../visual-basic/language-reference/keywords/index.md)
