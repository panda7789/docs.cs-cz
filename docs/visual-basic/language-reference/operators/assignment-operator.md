---
title: = – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 55b3a8201940a6fec351327aaa88e4ac1ee9246a
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="-operator-visual-basic"></a>= – operátor (Visual Basic)
Přiřazuje hodnotu proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Všechny zapisovatelné proměnné nebo libovolné vlastnosti.  
  
 `value`  
 Všechny literál, konstanta nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně znaménkem rovnosti (`=`) může být jednoduché skalární proměnné, vlastnost nebo element pole. Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md). `=` Operátor přiřadí hodnota v jeho pravé proměnnou nebo vlastnost na levé straně.  
  
> [!NOTE]
>  `=` Operátor slouží také jako operátor porovnání. Podrobnosti najdete v tématu [operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Přetížení  
 `=` Operátor může být přetížené pouze jako operátor porovnání relační, ne jako operátor přiřazení. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje operátor přiřazení. Hodnota na pravé straně je přiřazena k proměnné na levé straně.  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [&= – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [*= – operátor](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [+= – operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [/ = – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\\= – Operátor](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [^= – operátor](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
