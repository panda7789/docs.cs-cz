---
title: 'Postupy: Vytvoření kolekce používané inicializátorem kolekce (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 6158b6f02d95260e2955e77d732fae8b8d9d5e04
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33654158"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="038f2-102">Postupy: Vytvoření kolekce používané inicializátorem kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="038f2-102">How to: Create a Collection Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="038f2-103">Když použijete inicializátoru kolekce k vytvoření kolekce, Visual Basic – kompilátor vyhledá `Add` metoda typu kolekce, pro který parametry `Add` metoda odpovídají typům hodnot v inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="038f2-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="038f2-104">To `Add` metoda se používá k naplnění kolekce hodnotami z inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="038f2-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
## <a name="example"></a><span data-ttu-id="038f2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="038f2-105">Example</span></span>  
 <span data-ttu-id="038f2-106">Následující příklad ukazuje `OrderCollection` kolekce, která obsahuje veřejné `Add` metoda, která pomocí inicializátoru kolekce můžete přidat objekty typu `Order`.</span><span class="sxs-lookup"><span data-stu-id="038f2-106">The following example shows an `OrderCollection` collection that contains a public `Add` method that a collection initializer can use to add objects of type `Order`.</span></span> <span data-ttu-id="038f2-107">`Add` Metoda umožňuje pomocí syntaxe inicializátoru zkrácení kolekce.</span><span class="sxs-lookup"><span data-stu-id="038f2-107">The `Add` method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="038f2-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="038f2-108">See Also</span></span>  
 [<span data-ttu-id="038f2-109">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="038f2-109">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="038f2-110">Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce</span><span class="sxs-lookup"><span data-stu-id="038f2-110">How to: Create an Add Extension Method Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
