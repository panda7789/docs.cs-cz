---
title: "Iterátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.Iterator
helpviewer_keywords: Iterator keyword [Visual Basic]
ms.assetid: 69cb0b04-ac87-49d0-bcfe-810c0d60daff
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 503d586c0515b4cb53f8ec5656e5fe765cc094a7
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="iterator-visual-basic"></a><span data-ttu-id="5fb35-102">Iterátor (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="5fb35-102">Iterator (Visual Basic)</span></span>
<span data-ttu-id="5fb35-103">Určuje, že funkce nebo `Get` přistupujícího objektu je iterátor.</span><span class="sxs-lookup"><span data-stu-id="5fb35-103">Specifies that a function or `Get` accessor is an iterator.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="5fb35-104">Poznámky</span><span class="sxs-lookup"><span data-stu-id="5fb35-104">Remarks</span></span>  
 <span data-ttu-id="5fb35-105">*Iterator* provede vlastní iteraci přes kolekci.</span><span class="sxs-lookup"><span data-stu-id="5fb35-105">An *iterator* performs a custom iteration over a collection.</span></span> <span data-ttu-id="5fb35-106">Iterátor používá [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) příkaz vrátit každý prvek v kolekci, jeden v čase.</span><span class="sxs-lookup"><span data-stu-id="5fb35-106">An iterator uses the [Yield](../../../visual-basic/language-reference/statements/yield-statement.md) statement to return each element in the collection one at a time.</span></span> <span data-ttu-id="5fb35-107">Když `Yield` příkaz je dosaženo, se uchovávají aktuální umístění v kódu.</span><span class="sxs-lookup"><span data-stu-id="5fb35-107">When a `Yield` statement is reached, the current location in code is retained.</span></span> <span data-ttu-id="5fb35-108">Provádění je restartováno ze zmíněného umístění pokaždé, když je zavolána funkce iterátoru.</span><span class="sxs-lookup"><span data-stu-id="5fb35-108">Execution is restarted from that location the next time that the iterator function is called.</span></span>  
  
 <span data-ttu-id="5fb35-109">Iterátor můžete implementovat, nebo jako funkci `Get` přistupujícího objektu vlastnosti definice.</span><span class="sxs-lookup"><span data-stu-id="5fb35-109">An iterator can be implemented as a function or as a `Get` accessor of a property definition.</span></span> <span data-ttu-id="5fb35-110">`Iterator` Modifikátor se zobrazí v deklaraci funkce iterator nebo `Get` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="5fb35-110">The `Iterator` modifier appears in the declaration of the iterator function or `Get` accessor.</span></span>  
  
 <span data-ttu-id="5fb35-111">Volání iterovat z kódu klienta pomocí [For Each... Další příkaz](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span><span class="sxs-lookup"><span data-stu-id="5fb35-111">You call an iterator from client code by using a [For Each...Next Statement](../../../visual-basic/language-reference/statements/for-each-next-statement.md).</span></span>  
  
 <span data-ttu-id="5fb35-112">Návratový typ funkce iterator nebo `Get` přistupujícího objektu může být <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, nebo <xref:System.Collections.Generic.IEnumerator%601>.</span><span class="sxs-lookup"><span data-stu-id="5fb35-112">The return type of an iterator function or `Get` accessor can be <xref:System.Collections.IEnumerable>, <xref:System.Collections.Generic.IEnumerable%601>, <xref:System.Collections.IEnumerator>, or <xref:System.Collections.Generic.IEnumerator%601>.</span></span>  
  
 <span data-ttu-id="5fb35-113">Iterator nemají žádné `ByRef` parametry.</span><span class="sxs-lookup"><span data-stu-id="5fb35-113">An iterator cannot have any `ByRef` parameters.</span></span>  
  
 <span data-ttu-id="5fb35-114">Iterátor nemohou být v události, konstruktoru instance, statického konstruktoru nebo statické destruktor.</span><span class="sxs-lookup"><span data-stu-id="5fb35-114">An iterator cannot occur in an event, instance constructor, static constructor, or static destructor.</span></span>  
  
 <span data-ttu-id="5fb35-115">Iterace může být anonymní funkce.</span><span class="sxs-lookup"><span data-stu-id="5fb35-115">An iterator can be an anonymous function.</span></span> <span data-ttu-id="5fb35-116">Další informace najdete v tématu [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="5fb35-116">For more information, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
 <span data-ttu-id="5fb35-117">Další informace o iterátory najdete v tématu [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="5fb35-117">For more information about iterators, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="usage"></a><span data-ttu-id="5fb35-118">Použití</span><span class="sxs-lookup"><span data-stu-id="5fb35-118">Usage</span></span>  
 <span data-ttu-id="5fb35-119">`Iterator` Modifikátor lze použít v těchto kontexty:</span><span class="sxs-lookup"><span data-stu-id="5fb35-119">The `Iterator` modifier can be used in these contexts:</span></span>  
  
-   [<span data-ttu-id="5fb35-120">Function – příkaz</span><span class="sxs-lookup"><span data-stu-id="5fb35-120">Function Statement</span></span>](../../../visual-basic/language-reference/statements/function-statement.md)  
  
-   [<span data-ttu-id="5fb35-121">Property – příkaz</span><span class="sxs-lookup"><span data-stu-id="5fb35-121">Property Statement</span></span>](../../../visual-basic/language-reference/statements/property-statement.md)  
  
## <a name="example"></a><span data-ttu-id="5fb35-122">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fb35-122">Example</span></span>  
 <span data-ttu-id="5fb35-123">Následující příklad ukazuje funkce iterator.</span><span class="sxs-lookup"><span data-stu-id="5fb35-123">The following example demonstrates an iterator function.</span></span> <span data-ttu-id="5fb35-124">Funkce iterator má `Yield` příkaz, který je uvnitř [pro... Další](../../../visual-basic/language-reference/statements/for-next-statement.md) smyčky.</span><span class="sxs-lookup"><span data-stu-id="5fb35-124">The iterator function has a `Yield` statement that is inside a [For…Next](../../../visual-basic/language-reference/statements/for-next-statement.md) loop.</span></span> <span data-ttu-id="5fb35-125">Každé iteraci [pro každou](../../../visual-basic/language-reference/statements/for-each-next-statement.md) těla příkazu v `Main` vytvoří volání `Power` iterator funkce.</span><span class="sxs-lookup"><span data-stu-id="5fb35-125">Each iteration of the [For Each](../../../visual-basic/language-reference/statements/for-each-next-statement.md) statement body in `Main` creates a call to the `Power` iterator function.</span></span> <span data-ttu-id="5fb35-126">Každé volání funkce iterator pokračuje dalším spuštění `Yield` příkaz, který spadá další iterace `For…Next` smyčky.</span><span class="sxs-lookup"><span data-stu-id="5fb35-126">Each call to the iterator function proceeds to the next execution of the `Yield` statement, which occurs during the next iteration of the `For…Next` loop.</span></span>  
  
 [!code-vb[VbVbalrStatements#98](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_1.vb)]  
  
## <a name="example"></a><span data-ttu-id="5fb35-127">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fb35-127">Example</span></span>  
 <span data-ttu-id="5fb35-128">Následující příklad ukazuje `Get` přistupujícího objektu, který je iterátor.</span><span class="sxs-lookup"><span data-stu-id="5fb35-128">The following example demonstrates a `Get` accessor that is an iterator.</span></span> <span data-ttu-id="5fb35-129">`Iterator` Se modifikátor v deklarace vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="5fb35-129">The `Iterator` modifier is in the property declaration.</span></span>  
  
 [!code-vb[VbVbalrStatements#99](../../../visual-basic/language-reference/error-messages/codesnippet/VisualBasic/iterator_2.vb)]  
  
 <span data-ttu-id="5fb35-130">Další příklady najdete v tématu [iterátory](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span><span class="sxs-lookup"><span data-stu-id="5fb35-130">For additional examples, see [Iterators](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5fb35-131">Viz také</span><span class="sxs-lookup"><span data-stu-id="5fb35-131">See Also</span></span>  
 <xref:System.Runtime.CompilerServices.IteratorStateMachineAttribute>  
 [<span data-ttu-id="5fb35-132">Iterátory</span><span class="sxs-lookup"><span data-stu-id="5fb35-132">Iterators</span></span>](http://msdn.microsoft.com/library/f45331db-d595-46ec-9142-551d3d1eb1a7)  
 [<span data-ttu-id="5fb35-133">YIELD – příkaz</span><span class="sxs-lookup"><span data-stu-id="5fb35-133">Yield Statement</span></span>](../../../visual-basic/language-reference/statements/yield-statement.md)
