---
title: "= – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 230005640b2b494e5413b14ba13a7cb82ee9f22b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [& = – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)  
 [* = – Operátor](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)  
 [+= – Operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)  
 [/ = – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [\\= – Operátor](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)  
 [^ = – Operátor](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)  
 [Operátory porovnávání](../../../visual-basic/language-reference/operators/comparison-operators.md)  
 [Jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md)  
 [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
