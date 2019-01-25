---
title: 'Postupy: Vytvoření metody přidání rozšíření používané Inicializátorem kolekce (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 3a1db8ede8162b329d546c0e712ef1c2df7d7883
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54661669"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Postupy: Vytvoření metody přidání rozšíření používané Inicializátorem kolekce (Visual Basic)
Při vytvoření kolekce pomocí inicializátoru kolekce, hledá kompilátor jazyka Visual Basic `Add` metoda typu kolekce, pro kterou parametry `Add` metoda shodovat s typy hodnot v inicializátoru kolekce. To `Add` metoda se používá k naplnění kolekce s hodnotami z inicializátoru kolekce.  
  
 Pokud neexistuje odpovídající `Add` metoda existuje a nelze upravit kód pro kolekci, můžete přidat rozšiřující metoda volá `Add` , která přebírá parametry, které jsou vyžadované inicializátor kolekce. To je obvykle potřeba udělat, když použijete inicializátory kolekce pro obecné kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat do obecné metody rozšíření <xref:System.Collections.Generic.List%601> tak, aby inicializátoru kolekce je možné přidat objekty typu `Employee`. Metody rozšíření umožňuje použít syntaxi inicializátoru kolekce zkrácené.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Inicializátory kolekcí](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Postupy: Vytvoření kolekce používané Inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
