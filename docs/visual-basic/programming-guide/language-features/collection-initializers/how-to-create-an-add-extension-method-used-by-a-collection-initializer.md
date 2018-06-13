---
title: 'Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 5e35ad80037e843fd3cbd9caa68dcb2a09d707e1
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33646237"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce (Visual Basic)
Když použijete inicializátoru kolekce k vytvoření kolekce, Visual Basic – kompilátor vyhledá `Add` metoda typu kolekce, pro který parametry `Add` metoda odpovídají typům hodnot v inicializátoru kolekce. To `Add` metoda se používá k naplnění kolekce hodnotami z inicializátoru kolekce.  
  
 Pokud neexistuje odpovídající `Add` metoda existuje a nelze je upravit kód pro kolekci, můžete přidat volat metody rozšíření `Add` parametry, které jsou vyžadované inicializátoru kolekce, která má. To je obvykle co je potřeba udělat, když používáte Inicializátory kolekcí pro obecné kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat do obecné metody rozšíření <xref:System.Collections.Generic.List%601> zadejte tak, aby inicializátoru kolekce můžete použít k přidání objekty typu `Employee`. Metody rozšíření umožňuje pomocí syntaxe inicializátoru zkrácení kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_1.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_2.vb)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](../../../../visual-basic/programming-guide/language-features/collection-initializers/codesnippet/VisualBasic/how-to-create-an-add-extension-method-used-by-a-collection-initializer_3.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Inicializátory kolekcí](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)  
 [Postupy: Vytvoření kolekce používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
