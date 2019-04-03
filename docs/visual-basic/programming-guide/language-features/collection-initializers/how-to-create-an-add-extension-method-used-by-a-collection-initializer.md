---
title: 'Postupy: Vytvoření metody přidání rozšíření používané Inicializátorem kolekce (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: a5af41e25b8f82aa173e2df28cc41b313c8d68dd
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58825401"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="226d3-102">Postupy: Vytvoření metody přidání rozšíření používané Inicializátorem kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="226d3-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="226d3-103">Při vytvoření kolekce pomocí inicializátoru kolekce, hledá kompilátor jazyka Visual Basic `Add` metoda typu kolekce, pro kterou parametry `Add` metoda shodovat s typy hodnot v inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="226d3-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="226d3-104">To `Add` metoda se používá k naplnění kolekce s hodnotami z inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="226d3-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="226d3-105">Pokud neexistuje odpovídající `Add` metoda existuje a nelze upravit kód pro kolekci, můžete přidat rozšiřující metoda volá `Add` , která přebírá parametry, které jsou vyžadované inicializátor kolekce.</span><span class="sxs-lookup"><span data-stu-id="226d3-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="226d3-106">To je obvykle potřeba udělat, když použijete inicializátory kolekce pro obecné kolekce.</span><span class="sxs-lookup"><span data-stu-id="226d3-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="226d3-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="226d3-107">Example</span></span>  
 <span data-ttu-id="226d3-108">Následující příklad ukazuje, jak přidat do obecné metody rozšíření <xref:System.Collections.Generic.List%601> tak, aby inicializátoru kolekce je možné přidat objekty typu `Employee`.</span><span class="sxs-lookup"><span data-stu-id="226d3-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="226d3-109">Metody rozšíření umožňuje použít syntaxi inicializátoru kolekce zkrácené.</span><span class="sxs-lookup"><span data-stu-id="226d3-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="226d3-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="226d3-110">See also</span></span>

- [<span data-ttu-id="226d3-111">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="226d3-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [<span data-ttu-id="226d3-112">Postupy: Vytvoření kolekce používané Inicializátorem kolekce</span><span class="sxs-lookup"><span data-stu-id="226d3-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
