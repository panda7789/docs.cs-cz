---
title: Iterátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 565508046b3fa2dc52acf8c5204153beffc15d9e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33599509"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="81f14-102">Iterátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="81f14-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="81f14-103">Určuje, že funkce nebo `Get` přistupujícího objektu je iterátor.</span><span class="sxs-lookup"><span data-stu-id="81f14-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="81f14-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="81f14-104">Remarks</span></span>  
 <span data-ttu-id="81f14-105">*Iterator* provede vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="81f14-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="81f14-106">Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit každý prvek v kolekci, jeden v čase.</span><span class="sxs-lookup"><span data-stu-id="81f14-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="81f14-107">Když `Yield` příkaz je dosaženo, se uchovávají aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="81f14-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="81f14-108">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="81f14-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="81f14-109">Iterátor můžete implementovat, nebo jako funkci `Get` přistupujícího objektu vlastnosti definice.</span><span class="sxs-lookup"><span data-stu-id="81f14-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="81f14-110">`Iterator` Modifikátor se zobrazí v deklaraci funkce iterator nebo `Get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="81f14-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="81f14-111">Volání iterovat z kódu klienta pomocí [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="81f14-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="81f14-112">Návratový typ funkce iterator nebo `Get` přistupujícího objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="81f14-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="81f14-113">Iterator nemají žádné `ByRef` parametry.</span><span class="sxs-lookup"><span data-stu-id="81f14-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="81f14-114">Iterátor nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické destruktor.</span><span class="sxs-lookup"><span data-stu-id="81f14-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="81f14-115">Iterace může být anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="81f14-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="81f14-116">Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="81f14-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="81f14-117">Použití</span><span class="sxs-lookup"><span data-stu-id="81f14-117">Usage</span></span>  
 <span data-ttu-id="81f14-118">`Iterator` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="81f14-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="81f14-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="81f14-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="81f14-120">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="81f14-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="81f14-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="81f14-121">Example</span></span>  
 <span data-ttu-id="81f14-122">Následující příklad ukazuje funkce iterator.</span><span class="sxs-lookup"><span data-stu-id="81f14-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="81f14-123">Funkce iterator má `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="81f14-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="81f14-124">Každé iteraci [pro každou](../../../visual-basic/language-reference/statements/for-each-next-statement.md) těla příkazu v `Main` vytvoří volání `Power` iterator funkce.</span><span class="sxs-lookup"><span data-stu-id="81f14-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="81f14-125">Každé volání funkce iterator pokračuje dalším spuštění `Yield` příkaz, který spadá další iterace `For…Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="81f14-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="81f14-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="81f14-126">Example</span></span>  
 <span data-ttu-id="81f14-127">Následující příklad ukazuje `Get` přistupujícího objektu, který je iterátor.</span><span class="sxs-lookup"><span data-stu-id="81f14-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="81f14-128">`Iterator` Se modifikátor v deklarace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="81f14-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="81f14-129">Další příklady najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="81f14-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="81f14-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="81f14-130">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="81f14-131">Iterátory</span><span class="sxs-lookup"><span data-stu-id="81f14-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)  
 [<span data-ttu-id="81f14-132">Příkaz Yield</span><span class="sxs-lookup"><span data-stu-id="81f14-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
