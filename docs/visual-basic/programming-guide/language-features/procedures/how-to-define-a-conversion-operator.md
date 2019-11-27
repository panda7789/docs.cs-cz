---
title: 'Postupy: Definice operátora převodu'
ms.date: 07/20/2015
helpviewer_keywords:
- procedures [Visual Basic], defining
- operators [Visual Basic], defining
- procedures [Visual Basic], operator
- operators [Visual Basic], overloading
- return values [Visual Basic], Operator procedures
- operator overloading
ms.assetid: 54203dfa-c24b-463f-9942-d5153e89e762
ms.openlocfilehash: 0ff95390206947e5a28f7a5b85547b496746a9cc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74344890"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Postupy: Definice operátora převodu (Visual Basic)
Pokud jste definovali třídu nebo strukturu, můžete definovat operátor konverze typu mezi typem vaší třídy nebo struktury a jiným datovým typem (například `Integer`, `Double`nebo `String`).  
  
 Definujte převod typu jako proceduru [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) v rámci třídy nebo struktury. Všechny postupy převodu musí být `Public Shared`a každá z nich musí určovat buď [rozšiřování](../../../../visual-basic/language-reference/modifiers/widening.md) , nebo [zúžení](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje operátory převodu mezi strukturou nazvanou `digit` a `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Strukturu `digit` lze otestovat pomocí následujícího kódu.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také:

- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definice operátoru](./how-to-define-an-operator.md)
- [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)
- [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Postupy: Definice struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
