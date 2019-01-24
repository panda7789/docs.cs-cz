---
title: 'Postupy: Vytvoření kolekce používané Inicializátorem kolekce (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: c858db10-424d-47e0-92cd-e08087cc5ebc
ms.openlocfilehash: aaa367e5a1739f26e9b0458d8f2fc44462b73b7b
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54631721"
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Postupy: Vytvoření kolekce používané Inicializátorem kolekce (Visual Basic)
Při vytvoření kolekce pomocí inicializátoru kolekce, hledá kompilátor jazyka Visual Basic `Add` metoda typu kolekce, pro kterou parametry `Add` metoda shodovat s typy hodnot v inicializátoru kolekce. To `Add` metoda se používá k naplnění kolekce s hodnotami z inicializátoru kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `OrderCollection` kolekce, která obsahuje veřejnou `Add` metodou, chcete-li přidat objekty typu můžete použít inicializátor kolekce `Order`. `Add` Metoda vám umožní použít syntaxi inicializátoru kolekce zkrácený.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Inicializátory kolekcí](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Postupy: Vytvoření metody přidání rozšíření používané Inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
