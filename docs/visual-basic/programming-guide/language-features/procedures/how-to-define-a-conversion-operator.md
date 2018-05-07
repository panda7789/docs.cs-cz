---
title: 'Postupy: Definice operátora převodu (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 24bbe41af67f757cae661a78d482a423ff0ffd85
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Postupy: Definice operátora převodu (Visual Basic)
Pokud jste definovali třídu nebo strukturu, můžete definovat operátor převodu typu mezi typ třídu nebo strukturu a jiný datový typ (například `Integer`, `Double`, nebo `String`).  
  
 Převod typů jako definovat [CType – funkce](../../../../visual-basic/language-reference/functions/ctype-function.md) postup v rámci třídu nebo strukturu. Musí být všechny postupy převod `Public Shared`, a každé z nich musí být buď [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) nebo [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definování operátor na třídu nebo strukturu je také označován *přetížení* operátor.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje operátory převodu mezi strukturu s názvem `digit` a `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 Můžete otestovat strukturu `digit` následujícím kódem.  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Procedury operátoru](./operator-procedures.md)  
 [Postupy: Definice operátoru](./how-to-define-an-operator.md)  
 [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)  
 [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)  
 [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)  
 [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)  
 [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)  
 [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)  
 [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
