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
# <a name="how-to-create-an-add-extension-method-used-by-a-collection-initializer-visual-basic"></a>Postupy: Vytvoření metody přidání rozšíření používané inicializátorem kolekce (Visual Basic)
Při použití inicializátoru kolekce k vytvoření kolekce Visual Basic kompilátor vyhledá `Add` metodu typu kolekce, pro kterou parametry `Add` metody odpovídají typům hodnot v inicializátoru kolekce. Tato `Add` Metoda slouží k naplnění kolekce hodnotami z inicializátoru kolekce.  
  
 Pokud neexistuje žádná odpovídající `Add` Metoda a nemůžete upravovat kód pro kolekci, můžete přidat rozšiřující metodu `Add` s názvem, která přebírá parametry vyžadované inicializátorem kolekce. To je obvykle to, co je potřeba udělat při použití inicializátorů kolekcí pro obecné kolekce.  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak přidat rozšiřující metodu do obecného <xref:System.Collections.Generic.List%601> typu tak, že inicializátor kolekce lze použít k přidání objektů typu `Employee` . Metoda rozšíření umožňuje použít zkrácenou syntaxi inicializátoru kolekce.  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#1](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#1)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#2)]  
  
 [!code-vb[VbVbalrCollectionInitializersHowTo1#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrCollectionInitializersHowTo1/VB/Module1.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Inicializátory kolekcí](index.md)
- [Postupy: Vytvoření kolekce používané inicializátorem kolekce](how-to-create-a-collection-used-by-a-collection-initializer.md)
