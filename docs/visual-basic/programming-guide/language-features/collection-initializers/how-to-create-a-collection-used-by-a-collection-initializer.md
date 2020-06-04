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
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Postupy: Vytvoření kolekce používané inicializátorem kolekce (Visual Basic)
Při použití inicializátoru kolekce k vytvoření kolekce Visual Basic kompilátor vyhledá `Add` metodu typu kolekce, pro kterou parametry `Add` metody odpovídají typům hodnot v inicializátoru kolekce. Tato `Add` Metoda slouží k naplnění kolekce hodnotami z inicializátoru kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `OrderCollection` kolekci, která obsahuje veřejnou `Add` metodu, kterou může inicializátor kolekce použít k přidání objektů typu `Order` . `Add`Metoda umožňuje použít zkrácenou syntaxi inicializátoru kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#4)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo2/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Inicializátory kolekcí](index.md)
- [Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce](how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
