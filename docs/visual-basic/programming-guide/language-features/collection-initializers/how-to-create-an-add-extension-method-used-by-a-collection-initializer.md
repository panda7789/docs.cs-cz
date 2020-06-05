---
title: 'Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 4dbe6146b70181864a6717146071f9b93a1f583e
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84414566"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="60fc7-102">Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="60fc7-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="60fc7-103">Při použití inicializátoru kolekce k vytvoření kolekce Visual Basic kompilátor vyhledá `Add` metodu typu kolekce, pro kterou parametry `Add` metody odpovídají typům hodnot v inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="60fc7-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="60fc7-104">Tato `Add` Metoda slouží k naplnění kolekce hodnotami z inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="60fc7-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="60fc7-105">Pokud neexistuje žádná odpovídající `Add` Metoda a nemůžete upravovat kód pro kolekci, můžete přidat rozšiřující metodu `Add` s názvem, která přebírá parametry vyžadované inicializátorem kolekce.</span><span class="sxs-lookup"><span data-stu-id="60fc7-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="60fc7-106">To je obvykle to, co je potřeba udělat při použití inicializátorů kolekcí pro obecné kolekce.</span><span class="sxs-lookup"><span data-stu-id="60fc7-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="60fc7-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="60fc7-107">Example</span></span>  
 <span data-ttu-id="60fc7-108">Následující příklad ukazuje, jak přidat rozšiřující metodu do obecného <xref:System.Collections.Generic.List%601> typu tak, že inicializátor kolekce lze použít k přidání objektů typu `Employee` .</span><span class="sxs-lookup"><span data-stu-id="60fc7-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="60fc7-109">Metoda rozšíření umožňuje použít zkrácenou syntaxi inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="60fc7-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a><span data-ttu-id="60fc7-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="60fc7-110">See also</span></span>

- [<span data-ttu-id="60fc7-111">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="60fc7-111">Collection Initializers</span></span>](index.md)
- [<span data-ttu-id="60fc7-112">Postupy: Vytvoření kolekce používané inicializátorem kolekce</span><span class="sxs-lookup"><span data-stu-id="60fc7-112">How to: Create a Collection Used by a Collection Initializer</span></span>](how-to-create-a-collection-used-by-a-collection-initializer.md)
