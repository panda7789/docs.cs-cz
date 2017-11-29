---
title: "Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords: collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: d19ac8b03b992eb9b09b5cb45fdcceadad3a822a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a><span data-ttu-id="64d23-102">Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="64d23-102">How to: Create an Add Extension Method Used by a Collection Initializer (Visual Basic)</span></span>
<span data-ttu-id="64d23-103">Když použijete inicializátoru kolekce k vytvoření kolekce, Visual Basic – kompilátor vyhledá `Add` metoda typu kolekce, pro který parametry `Add` metoda odpovídají typům hodnot v inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="64d23-103">When you use a collection initializer to create a collection, the Visual Basic compiler searches for an `Add` method of the collection type for which the parameters for the `Add` method match the types of the values in the collection initializer.</span></span> <span data-ttu-id="64d23-104">To `Add` metoda se používá k naplnění kolekce hodnotami z inicializátoru kolekce.</span><span class="sxs-lookup"><span data-stu-id="64d23-104">This `Add` method is used to populate the collection with the values from the collection initializer.</span></span>  
  
 <span data-ttu-id="64d23-105">Pokud neexistuje odpovídající `Add` metoda existuje a nelze je upravit kód pro kolekci, můžete přidat volat metody rozšíření `Add` parametry, které jsou vyžadované inicializátoru kolekce, která má.</span><span class="sxs-lookup"><span data-stu-id="64d23-105">If no matching `Add` method exists and you cannot modify the code for the collection, you can add an extension method called `Add` that takes the parameters that are required by the collection initializer.</span></span> <span data-ttu-id="64d23-106">To je obvykle co je potřeba udělat, když používáte Inicializátory kolekcí pro obecné kolekce.</span><span class="sxs-lookup"><span data-stu-id="64d23-106">This is typically what you need to do when you use collection initializers for generic collections.</span></span>  
  
## <a name="example"></a><span data-ttu-id="64d23-107">Příklad</span><span class="sxs-lookup"><span data-stu-id="64d23-107">Example</span></span>  
 <span data-ttu-id="64d23-108">Následující příklad ukazuje, jak přidat do obecné metody rozšíření <xref:System.Collections.Generic.List%601> zadejte tak, aby inicializátoru kolekce můžete použít k přidání objekty typu `Employee`.</span><span class="sxs-lookup"><span data-stu-id="64d23-108">The following example shows how to add an extension method to the generic <xref:System.Collections.Generic.List%601> type so that a collection initializer can be used to add objects of type `Employee`.</span></span> <span data-ttu-id="64d23-109">Metody rozšíření umožňuje pomocí syntaxe inicializátoru zkrácení kolekce.</span><span class="sxs-lookup"><span data-stu-id="64d23-109">The extension method enables you to use the shortened collection initializer syntax.</span></span>  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="64d23-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="64d23-110">See Also</span></span>  
 [<span data-ttu-id="64d23-111">Inicializátory kolekcí</span><span class="sxs-lookup"><span data-stu-id="64d23-111">Collection Initializers</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [<span data-ttu-id="64d23-112">Postupy: vytvoření kolekce používané inicializátorem kolekce</span><span class="sxs-lookup"><span data-stu-id="64d23-112">How to: Create a Collection Used by a Collection Initializer</span></span>](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
