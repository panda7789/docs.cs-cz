---
title: Iterátor
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: 9d7eaf186bae544031487ce027505e1e0d4ae0f3
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351527"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="793e8-102">Iterátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="793e8-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="793e8-103">Určuje, že se jedná o iterátor funkce nebo `Get` přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="793e8-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="793e8-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="793e8-104">Remarks</span></span>  
 <span data-ttu-id="793e8-105">*Iterátor* provádí vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="793e8-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="793e8-106">Iterátor používá příkaz [yield](../../../visual-basic/language-reference/statements/yield-statement.md) k vrácení každého prvku v kolekci v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="793e8-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="793e8-107">Když je dosaženo příkazu `Yield`, je zachováno aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="793e8-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="793e8-108">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="793e8-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="793e8-109">Iterátor lze implementovat jako funkci nebo jako přistupující objekt `Get` definice vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="793e8-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="793e8-110">V deklaraci funkce iterátoru nebo přístupového objektu `Get` se objeví modifikátor `Iterator`.</span><span class="sxs-lookup"><span data-stu-id="793e8-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="793e8-111">Můžete zavolat iterátor z klientského kódu s použitím [pro každý... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="793e8-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="793e8-112">Návratový typ funkce iterátoru nebo přístupového objektu `Get` může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="793e8-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="793e8-113">Iterátor nemůže mít žádné parametry `ByRef`.</span><span class="sxs-lookup"><span data-stu-id="793e8-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="793e8-114">Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.</span><span class="sxs-lookup"><span data-stu-id="793e8-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="793e8-115">Iterátor může být anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="793e8-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="793e8-116">Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="793e8-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="793e8-117">Využití</span><span class="sxs-lookup"><span data-stu-id="793e8-117">Usage</span></span>  
 <span data-ttu-id="793e8-118">V těchto kontextech lze použít modifikátor `Iterator`:</span><span class="sxs-lookup"><span data-stu-id="793e8-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="793e8-119">Příkaz Function</span><span class="sxs-lookup"><span data-stu-id="793e8-119">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
- [<span data-ttu-id="793e8-120">Příkaz Property</span><span class="sxs-lookup"><span data-stu-id="793e8-120">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="793e8-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="793e8-121">Example</span></span>  
 <span data-ttu-id="793e8-122">Následující příklad ukazuje funkci iterátoru.</span><span class="sxs-lookup"><span data-stu-id="793e8-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="793e8-123">Funkce iterátoru má příkaz `Yield`, který je uvnitř [... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčka</span><span class="sxs-lookup"><span data-stu-id="793e8-123">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="793e8-124">Každá iterace [pro každý](../../../visual-basic/language-reference/statements/for-each-next-statement.md) text příkazu v `Main` vytvoří volání funkce `Power` iterátoru.</span><span class="sxs-lookup"><span data-stu-id="793e8-124">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="793e8-125">Každé volání funkce iterátoru pokračuje na další provedení příkazu `Yield`, ke kterému dojde během další iterace `For…Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="793e8-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="793e8-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="793e8-126">Example</span></span>  
 <span data-ttu-id="793e8-127">Následující příklad ukazuje přistupující objekt `Get`, který je iterátorem.</span><span class="sxs-lookup"><span data-stu-id="793e8-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="793e8-128">Modifikátor `Iterator` je v deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="793e8-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="793e8-129">Další příklady naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="793e8-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="793e8-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="793e8-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="793e8-131">Iterátory</span><span class="sxs-lookup"><span data-stu-id="793e8-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="793e8-132">Příkaz Yield</span><span class="sxs-lookup"><span data-stu-id="793e8-132">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
