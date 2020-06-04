---
title: 'Postupy: Vytvoření kolekce používané inicializátorem kolekce'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 7cba290b92f41125a93d1ed022e4db5ef62da789
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414553"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="08a48-102">Postupy: Vytvoření kolekce používané inicializátorem kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="08a48-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="08a48-103">Při použití inicializátoru kolekce k vytvoření kolekce Visual Basic kompilátor vyhledá `Add` metodu typu kolekce, pro kterou parametry `Add` metody odpovídají typům hodnot v inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="08a48-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="08a48-104">Tato `Add` Metoda slouží k naplnění kolekce hodnotami z inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="08a48-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="08a48-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="08a48-105">Example</span></span>  
 <span data-ttu-id="08a48-106">Následující příklad ukazuje `OrderCollection` kolekci, která obsahuje veřejnou `Add` metodu, kterou může inicializátor kolekce použít k přidání objektů typu `Order` .</span><span class="sxs-lookup"><span data-stu-id="08a48-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="08a48-107">`Add`Metoda umožňuje použít zkrácenou syntaxi inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="08a48-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="08a48-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="08a48-108">See also</span></span>

- [<span data-ttu-id="08a48-109">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="08a48-109">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="08a48-110">Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce</span><span class="sxs-lookup"><span data-stu-id="08a48-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
