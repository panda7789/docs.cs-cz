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
ms.openlocfilehash: 75f303219b9bf32613989f65f90a9096ef70e02e
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350203"
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
 Element na levé straně znaménka rovná se (`=`) může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md). Operátor `=` přiřadí hodnotu přímo k proměnné nebo vlastnosti nalevo.  
  
> [!NOTE]
> Operátor `=` se používá také jako operátor porovnání. Podrobnosti naleznete v tématu [operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md).  
  
## <a name="overloading"></a>Přetížení  
 Operátor `=` může být přetížen pouze jako relační relační operátor, nikoli jako operátor přiřazení. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje operátor přiřazení. Hodnota na pravé straně je přiřazena k proměnné na levé straně.  
  
 [!code-vb[VbVbalrOperators#9](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#9)]  
  
## <a name="see-also"></a>Viz také:

- [&= – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [*= – operátor](../../../visual-basic/language-reference/operators/multiplication-assignment-operator.md)
- [+= – operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [-= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-assignment-operator.md)
- [/= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [\\= – operátor](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [^= – operátor](../../../visual-basic/language-reference/operators/exponentiation-assignment-operator.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
- [Operátory porovnání](../../../visual-basic/language-reference/operators/comparison-operators.md)
- [ReadOnly](../../../visual-basic/language-reference/modifiers/readonly.md)
- [Odvození místního typu](../../../visual-basic/programming-guide/language-features/variables/local-type-inference.md)
