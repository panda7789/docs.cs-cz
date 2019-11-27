---
title: 'Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce'
ms.date: 07/20/2015
helpviewer_keywords:
- collection initializers [Visual Basic]
ms.assetid: f64b52c7-8b11-4410-93a6-cb3aeebcc772
ms.openlocfilehash: 6d5f9d38b413b79f111a14ec3829c57a9797ce54
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74346710"
---
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce (Visual Basic)
Použijete-li inicializátor kolekce k vytvoření kolekce, Visual Basic kompilátor vyhledá metodu `Add` typu kolekce, pro kterou parametry `Add` metody odpovídají typům hodnot v inicializátoru kolekce. Tato metoda `Add` slouží k naplnění kolekce hodnotami z inicializátoru kolekce.  
  
 Pokud neexistuje žádná odpovídající metoda `Add` a nelze upravit kód pro kolekci, můžete přidat metodu rozšíření nazvanou `Add`, která převezme parametry vyžadované inicializátorem kolekce. To je obvykle to, co je potřeba udělat při použití inicializátorů kolekcí pro obecné kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat rozšiřující metodu do obecného typu <xref:System.Collections.Generic.List%601> tak, že inicializátor kolekce lze použít k přidání objektů typu `Employee`. Metoda rozšíření umožňuje použít zkrácenou syntaxi inicializátoru kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [Inicializátory kolekcí](../../../../visual-basic/programming-guide/language-features/collection-initializers/index.md)
- [Postupy: Vytvoření kolekce používané inicializátorem kolekce](../../../../visual-basic/programming-guide/language-features/collection-initializers/how-to-create-a-collection-used-by-a-collection-initializer.md)
