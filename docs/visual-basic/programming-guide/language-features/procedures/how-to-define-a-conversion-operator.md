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
ms.openlocfilehash: 76d0769456e30766b830023c1f27381ceca59cbb
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54521527"
---
# <a name="how-to-define-a-conversion-operator-visual-basic"></a>Postupy: Definice operátora převodu (Visual Basic)
Pokud jste definovali třídy nebo struktury, můžete definovat operátor převodu typu mezi typem třídy nebo struktury a jiný typ dat (například `Integer`, `Double`, nebo `String`).  
  
 Definovat převod typu jako [funkce CType](../../../../visual-basic/language-reference/functions/ctype-function.md) postup v rámci třídy nebo struktury. Všechny postupy převod musí být `Public Shared`, a každý z nich musí určovat buď [Widening](../../../../visual-basic/language-reference/modifiers/widening.md) nebo [Narrowing](../../../../visual-basic/language-reference/modifiers/narrowing.md).  
  
 Definování v třídě nebo struktuře operátor se také nazývá *přetížení* operátor.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje operátory převodu mezi strukturu s názvem `digit` a `Byte`.  
  
 [!code-vb[VbVbcnProcedures#27](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_1.vb)]  
  
 Můžete otestovat strukturu `digit` následujícím kódem.  
  
 [!code-vb[VbVbcnProcedures#28](./codesnippet/VisualBasic/how-to-define-a-conversion-operator_2.vb)]  
  
## <a name="see-also"></a>Viz také:
- [Procedury operátoru](./operator-procedures.md)
- [Postupy: Definovat operátor](./how-to-define-an-operator.md)
- [Postupy: Volání procedury operátora](./how-to-call-an-operator-procedure.md)
- [Postupy: Použití třídy, která definuje operátory](./how-to-use-a-class-that-defines-operators.md)
- [Příkaz Operator](../../../../visual-basic/language-reference/statements/operator-statement.md)
- [Příkaz Structure](../../../../visual-basic/language-reference/statements/structure-statement.md)
- [Postupy: Deklarace struktury](../../../../visual-basic/programming-guide/language-features/data-types/how-to-declare-a-structure.md)
- [Implicitní a explicitní převody](../../../../visual-basic/programming-guide/language-features/data-types/implicit-and-explicit-conversions.md)
- [Rozšíření a zúžení převodů](../../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md)
