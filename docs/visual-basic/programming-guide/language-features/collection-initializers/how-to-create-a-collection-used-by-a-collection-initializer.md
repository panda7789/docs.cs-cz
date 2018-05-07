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
---
# <a name="how-to-create-a-collection-used-by-a-collection-initializer-visual-basic"></a>Postupy: Vytvoření kolekce používané inicializátorem kolekce (Visual Basic)
Když použijete inicializátoru kolekce k vytvoření kolekce, Visual Basic – kompilátor vyhledá `Add` metoda typu kolekce, pro který parametry `Add` metoda odpovídají typům hodnot v inicializátoru kolekce. To `Add` metoda se používá k naplnění kolekce hodnotami z inicializátoru kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje `OrderCollection` kolekce, která obsahuje veřejné `Add` metoda, která pomocí inicializátoru kolekce můžete přidat objekty typu `Order`. `Add` Metoda umožňuje pomocí syntaxe inicializátoru zkrácení kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#4](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_3.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo2#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-a-collection-used-by-a-collection-initializer_4.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Inicializátory kolekcí](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-an-add-extension-method-used-by-a-collection-initializer.md)
