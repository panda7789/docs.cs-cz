---
title: 'Postupy: Vytvoření kolekce používané inicializátorem kolekce'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: 5eaf9e828455bf2accda86ab52a1ce645f10b9ee
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349052"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Postupy: Vytvoření kolekce používané inicializátorem kolekce (Visual Basic)
Použijete-li inicializátor kolekce k vytvoření kolekce, Visual Basic kompilátor vyhledá metodu `Add` typu kolekce, pro kterou parametry `Add` metody odpovídají typům hodnot v inicializátoru kolekce. Tato metoda `Add` slouží k naplnění kolekce hodnotami z inicializátoru kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `OrderCollection` kolekci, která obsahuje veřejnou `Add` metodu, kterou může inicializátor kolekce použít k přidání objektů typu `Order`. Metoda `Add` umožňuje použít zkrácenou syntaxi inicializátoru kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Inicializátory kolekcí](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
