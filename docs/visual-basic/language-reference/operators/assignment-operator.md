---
title: = – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.Assign
- vb.=
helpviewer_keywords:
- = operator [Visual Basic]
- = assignment statements [Visual Basic]
ms.assetid: 2dac2e49-86c8-42f8-80c1-458452fb5e29
ms.openlocfilehash: 516cb21e02d9fb2cd4b8d72282bb74163e1fb14b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371762"
---
# <a name="-operator-visual-basic"></a>= – operátor (Visual Basic)
Přiřadí hodnotu proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty = value  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Jakákoli zapisovatelná proměnná nebo libovolná vlastnost.  
  
 `value`  
 Libovolný literál, konstanta nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně znaménka rovná se ( `=` ) může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md). `=`Operátor přiřadí hodnotu přímo k proměnné nebo vlastnosti nalevo.  
  
> [!NOTE]
> `=`Operátor je také použit jako operátor porovnání. Podrobnosti naleznete v tématu [operátory porovnání](comparison-operators.md).  
  
## <a name="overloading"></a>Přetížení  
 `=`Operátor může být přetížen pouze jako relační relační operátor, nikoli jako operátor přiřazení. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje operátor přiřazení. Hodnota na pravé straně je přiřazena k proměnné na levé straně.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také

- [&= – operátor](and-assignment-operator.md)
- [* = – Operátor](multiplication-assignment-operator.md)
- [+ = – Operátor](addition-assignment-operator.md)
- [-= – Operátor (Visual Basic)](subtraction-assignment-operator.md)
- [/= – Operátor (Visual Basic)](floating-point-division-assignment-operator.md)
- [\\= – Operátor](integer-division-assignment-operator.md)
- [^ = – Operátor](exponentiation-assignment-operator.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
- [Operátory porovnání](comparison-operators.md)
- [ReadOnly](../modifiers/readonly.md)
- [Odvození místního typu](../../programming-guide/language-features/variables/local-type-inference.md)
