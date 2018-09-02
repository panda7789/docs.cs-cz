---
title: 'Postupy: Do proměnné umístit více než jednu hodnotu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- classes [Visual Basic], composite data types
- composite types [Visual Basic]
- composite data types [Visual Basic]
- data types [Visual Basic], composite
- arrays [Visual Basic], composite data types
- structures [Visual Basic], composite data types
- arrays [Visual Basic], compilation errors
- types [Visual Basic], composite
ms.assetid: 5fe0e558-aac2-4a40-b7f2-7cfea7336917
ms.openlocfilehash: 781f56c7e710f5130d821ca4796398379dfa4c6e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43456487"
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Postupy: Do proměnné umístit více než jednu hodnotu (Visual Basic)
Proměnná obsahuje více než jednu hodnotu, pokud deklarujete jej bude *složené datový typ*.  
  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) zahrnují třídy, struktury a pole. Proměnné typu složených dat může obsahovat kombinaci základní datové typy a dalších složené typy. Struktury a třídy může obsahovat kód, jakož i data.  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a>Chcete-li do proměnné umístit více než jednu hodnotu  
  
1.  Určete, jaký složené datový typ, který chcete použít pro proměnné.  
  
2.  Pokud již není definován typ. složených dat, definujte ho tak, aby ho může použít vaše proměnná.  
  
    -   Definovat strukturu s [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md).  
  
    -   Definování pole [příkazu Dim](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
    -   Definovat třídu pomocí [Class – příkaz](../../../../visual-basic/language-reference/statements/class-statement.md).  
  
3.  Deklarujte proměnné s `Dim` příkazu.  
  
4.  Použijte název proměnné pomocí `As` klauzuli.  
  
5.  Postupujte podle `As` – klíčové slovo s názvem odpovídající složené datového typu.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/language-reference/data-types/index.md)  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
