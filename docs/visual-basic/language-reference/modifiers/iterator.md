---
title: Iterátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 499949d1f4c20e1f465355bd076ba39f1496779b
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822697"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="6ef77-102">Iterátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="6ef77-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="6ef77-103">Určuje, že funkce nebo `Get` přístupový objekt je iterátor.</span><span class="sxs-lookup"><span data-stu-id="6ef77-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="6ef77-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="6ef77-104">Remarks</span></span>  
 <span data-ttu-id="6ef77-105">*Iterátoru* provádí vlastní iterace nad kolekcí.</span><span class="sxs-lookup"><span data-stu-id="6ef77-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="6ef77-106">Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz k vrácení každého prvku v kolekci, jeden po druhém.</span><span class="sxs-lookup"><span data-stu-id="6ef77-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="6ef77-107">Když `Yield` je dosažen příkaz, je zachováno aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="6ef77-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="6ef77-108">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="6ef77-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="6ef77-109">Iterátor je možné implementovat jako funkci nebo `Get` přístupový objekt pro definici vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ef77-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="6ef77-110">`Iterator` Modifikátor se zobrazí v deklaraci funkce iterátoru nebo `Get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="6ef77-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="6ef77-111">Můžete volat iterátor z klientského kódu s použitím [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="6ef77-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="6ef77-112">Návratový typ funkce iterátoru nebo `Get` přistupující objekt může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="6ef77-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="6ef77-113">Iterátor nesmí obsahovat žádné `ByRef` parametry.</span><span class="sxs-lookup"><span data-stu-id="6ef77-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="6ef77-114">V události, konstruktor instance, statický konstruktor nebo statická destruktor nemůže dojít k iterátoru.</span><span class="sxs-lookup"><span data-stu-id="6ef77-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="6ef77-115">Iterátor může být anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="6ef77-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="6ef77-116">Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="6ef77-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="6ef77-117">Použití</span><span class="sxs-lookup"><span data-stu-id="6ef77-117">Usage</span></span>  
 <span data-ttu-id="6ef77-118">`Iterator` Modifikátor lze použít v těchto kontextech:</span><span class="sxs-lookup"><span data-stu-id="6ef77-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="6ef77-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="6ef77-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="6ef77-120">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="6ef77-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="6ef77-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ef77-121">Example</span></span>  
 <span data-ttu-id="6ef77-122">Následující příklad ukazuje funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="6ef77-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="6ef77-123">Má funkce iterátoru `Yield` , který se nachází uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ef77-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="6ef77-124">Každá iterace [pro každou](../../../visual-basic/language-reference/statements/for-each-next-statement.md) tělo s příkazy v `Main` vytváří volání `Power` funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="6ef77-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="6ef77-125">Každé volání funkce iterátoru pokračuje do dalšího provedení příkazu `Yield` prohlášení, které nastane při další iteraci `For…Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="6ef77-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="6ef77-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ef77-126">Example</span></span>  
 <span data-ttu-id="6ef77-127">Následující příklad ukazuje `Get` přístupovou metodu iterátoru.</span><span class="sxs-lookup"><span data-stu-id="6ef77-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="6ef77-128">`Iterator` Modifikátor je v deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="6ef77-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="6ef77-129">Další příklady najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="6ef77-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="6ef77-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ef77-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="6ef77-131">Iterátory</span><span class="sxs-lookup"><span data-stu-id="6ef77-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="6ef77-132">Příkaz Yield</span><span class="sxs-lookup"><span data-stu-id="6ef77-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
