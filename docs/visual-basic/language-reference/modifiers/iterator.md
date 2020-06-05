---
title: Iterátor
ms.date: 07/20/2015
f1_keywords:
- vb.Iterator
helpviewer_keywords:
- Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
ms.openlocfilehash: bb19289c69f4c523363e88e91a58f37d232b07df
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396230"
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="597e5-102">Iterátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="597e5-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="597e5-103">Určuje, že funkce nebo `Get` přistupující objekt je iterátor.</span><span class="sxs-lookup"><span data-stu-id="597e5-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="597e5-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="597e5-104">Remarks</span></span>  
 <span data-ttu-id="597e5-105">*Iterátor* provádí vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="597e5-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="597e5-106">Iterátor používá příkaz [yield](../statements/yield-statement.md) k vrácení každého prvku v kolekci v jednom okamžiku.</span><span class="sxs-lookup"><span data-stu-id="597e5-106">An iterator uses the [Yield](../statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="597e5-107">Při `Yield` dosažení příkazu se zachová aktuální poloha v kódu.</span><span class="sxs-lookup"><span data-stu-id="597e5-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="597e5-108">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="597e5-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="597e5-109">Iterátor lze implementovat jako funkci nebo jako `Get` přistupující objekt definice vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="597e5-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="597e5-110">`Iterator`Modifikátor se zobrazí v deklaraci funkce iterátoru nebo `Get` přístupového objektu.</span><span class="sxs-lookup"><span data-stu-id="597e5-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="597e5-111">Můžete zavolat iterátor z klientského kódu s použitím [pro každý... Další příkaz](../statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="597e5-111">You call an iterator from client code by using a [For Each...Next Statement](../statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="597e5-112">Návratový typ funkce iterátoru nebo `Get` přístupového objektu může být <xref:System.Collections.IEnumerable> , <xref:System.Collections.Generic.IEnumerable%601> , <xref:System.Collections.IEnumerator> nebo <xref:System.Collections.Generic.IEnumerator%601> .</span><span class="sxs-lookup"><span data-stu-id="597e5-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="597e5-113">Iterátor nemůže mít žádné `ByRef` parametry.</span><span class="sxs-lookup"><span data-stu-id="597e5-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="597e5-114">Iterátor nemůže být v události, konstruktoru instance, statickém konstruktoru nebo statickém destruktoru.</span><span class="sxs-lookup"><span data-stu-id="597e5-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="597e5-115">Iterátor může být anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="597e5-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="597e5-116">Další informace najdete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="597e5-116">For more information, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="597e5-117">Využití</span><span class="sxs-lookup"><span data-stu-id="597e5-117">Usage</span></span>  
 <span data-ttu-id="597e5-118">`Iterator`V těchto kontextech lze použít modifikátor:</span><span class="sxs-lookup"><span data-stu-id="597e5-118">The `Iterator` modifier can be used in these contexts:</span></span>  
  
- [<span data-ttu-id="597e5-119">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="597e5-119">Function Statement</span></span>](../statements/function-statement.md)  
  
- [<span data-ttu-id="597e5-120">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="597e5-120">Property Statement</span></span>](../statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="597e5-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="597e5-121">Example</span></span>  
 <span data-ttu-id="597e5-122">Následující příklad ukazuje funkci iterátoru.</span><span class="sxs-lookup"><span data-stu-id="597e5-122">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="597e5-123">Funkce iterátoru má `Yield` příkaz, který je uvnitř [... Další](../statements/for-next-statement.md) smyčka</span><span class="sxs-lookup"><span data-stu-id="597e5-123">The iterator function has a `Yield` statement that is inside a [For…Next](../statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="597e5-124">Každá iterace [pro každý](../statements/for-each-next-statement.md) text příkazu v `Main` vytvoří volání `Power` funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="597e5-124">Each iteration of the [For Each](../statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="597e5-125">Každé volání funkce iterátoru pokračuje k dalšímu provedení `Yield` příkazu, ke kterému dojde během další iterace `For…Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="597e5-125">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#98)]  
  
## <a name="example"></a><span data-ttu-id="597e5-126">Příklad</span><span class="sxs-lookup"><span data-stu-id="597e5-126">Example</span></span>  
 <span data-ttu-id="597e5-127">Následující příklad ukazuje `Get` přistupující objekt, který je iterátorem.</span><span class="sxs-lookup"><span data-stu-id="597e5-127">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="597e5-128">`Iterator`Modifikátor je v deklaraci vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="597e5-128">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrStatements/VB/Class2.vb#99)]  
  
 <span data-ttu-id="597e5-129">Další příklady naleznete v tématu [iterátory](../../programming-guide/concepts/iterators.md).</span><span class="sxs-lookup"><span data-stu-id="597e5-129">For additional examples, see [Iterators](../../programming-guide/concepts/iterators.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="597e5-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="597e5-130">See also</span></span>

- <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>
- [<span data-ttu-id="597e5-131">Iterátory</span><span class="sxs-lookup"><span data-stu-id="597e5-131">Iterators</span></span>](../../programming-guide/concepts/iterators.md)
- [<span data-ttu-id="597e5-132">Yield – příkaz</span><span class="sxs-lookup"><span data-stu-id="597e5-132">Yield Statement</span></span>](../statements/yield-statement.md)
