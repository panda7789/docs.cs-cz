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
ms.openlocfilehash: 783c75ed4577831b7ca444870c97063e8a057346
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-hold-more-than-one-value-in-a-variable-visual-basic"></a>Postupy: Do proměnné umístit více než jednu hodnotu (Visual Basic)
Proměnné obsahuje více než jednu hodnotu, pokud je deklarovat mohla být *složeného datového typu*.  
  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md) zahrnují struktury, pole a třídy. Proměnná složeného datového typu mohou být uloženy kombinaci základní datové typy a dalších složené typy. Struktury a třídy může obsahovat kód, jakož i data.  
  
### <a name="to-hold-more-than-one-value-in-a-variable"></a>Chcete-li do proměnné umístit více než jednu hodnotu  
  
1.  Určete, jaký typ složené datové, kterou chcete použít pro vaše proměnná.  
  
2.  Pokud již není definován složený datový typ, definujte ho tak, aby vaše proměnná může používat.  
  
    -   Definovat strukturu s [Structure – příkaz](../../../../visual-basic/language-reference/statements/structure-statement.md).  
  
    -   Zadejte pole s [Dim – příkaz](../../../../visual-basic/language-reference/statements/dim-statement.md).  
  
    -   Definice třídy, se [Class – příkaz](../../../../visual-basic/language-reference/statements/class-statement.md).  
  
3.  Deklarovat vaše proměnná s `Dim` příkaz.  
  
4.  Postupujte podle názvu proměnné s `As` klauzule.  
  
5.  Postupujte podle `As` – klíčové slovo s názvem odpovídající složené datového typu.  
  
## <a name="see-also"></a>Viz také  
 [Datové typy](../../../../visual-basic/language-reference/data-types/data-type-summary.md)  
 [Znaky typu](../../../../visual-basic/programming-guide/language-features/data-types/type-characters.md)  
 [Složené datové typy](../../../../visual-basic/programming-guide/language-features/data-types/composite-data-types.md)  
 [Struktury](../../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
 [Pole](../../../../visual-basic/programming-guide/language-features/arrays/index.md)  
 [Objekty a třídy](../../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)  
 [Typy hodnot a odkazové typy](../../../../visual-basic/programming-guide/language-features/data-types/value-types-and-reference-types.md)
