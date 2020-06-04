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
ms.openlocfilehash: 53b0211c6304625edd7ac24fa52ff0c051d8f0a0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84388086"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Postupy: Definice operátora převodu (Visual Basic)
Pokud jste definovali třídu nebo strukturu, můžete definovat operátor konverze typu mezi typem vaší třídy nebo struktury a jiným datovým typem (například `Integer` , `Double` nebo `String` ).  
  
 Definujte převod typu jako proceduru [funkce CType](../../../language-reference/functions/ctype-function.md) v rámci třídy nebo struktury. Všechny postupy převodu musí být `Public Shared` a každá z nich musí určovat buď [rozšiřování](../../../language-reference/modifiers/widening.md) , nebo [zúžení](../../../language-reference/modifiers/narrowing.md).  
  
 Definování operátoru pro třídu nebo strukturu se označuje také jako *přetížení* operátoru.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje operátory převodu mezi strukturou nazvanou `digit` a `Byte` .  
  
 [!code-vb[VbVbcnProcedures#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#27)]  
  
 Strukturu můžete otestovat `digit` pomocí následujícího kódu.  
  
 [!code-vb[VbVbcnProcedures#28](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbcnProcedures/VB/Class1.vb#28)]  
  
## <a name="see-also"></a>Viz také

- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definice operátoru](./how-to-define-an-operator.md)
- [Postupy: Volání procedury operátoru](./how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)
- [Operator – příkaz](../../../language-reference/statements/operator-statement.md)
- [Structure – příkaz](../../../language-reference/statements/structure-statement.md)
- [Postupy: Deklarace struktury](../data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../data-types/widening-and-narrowing-conversions.md)
