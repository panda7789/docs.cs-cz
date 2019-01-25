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
ms.openlocfilehash: 58dcdfd21fd8701c6ac391672e768819f696aab9
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54643546"
---
# <a name="-operator-visual-basic"></a>= – operátor (Visual Basic)
Přiřadí hodnotu k proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty = value  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Jakékoli zapisovatelné proměnnou nebo vlastnost.  
  
 `value`  
 Všechny literál, konstanta nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně znaménka rovnosti (`=`) může být jednoduché skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md). `=` Operátor přiřadí hodnotu napravo na proměnnou nebo vlastnost na levé straně.  
  
> [!NOTE]
>  `=` Operátor slouží také jako operátor porovnání. Podrobnosti najdete v tématu [operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Přetížení  
 `=` Operátor může být přetížená pouze jako operátor porovnání relační, nikoli jako operátor přiřazení. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje operátor přiřazení. Hodnota na pravé straně je přiřazena k proměnné na levé straně.  
  
 [!code-vb[VbVbalrOperators#9](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [&= – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= – operátor](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= – operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/ = – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= – operátor](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
- [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
