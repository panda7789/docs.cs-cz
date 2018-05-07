---
title: '&amp;= – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: c3db2d4095600f32af92d1a4ce1f806a3f032af0
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="amp-operator-visual-basic"></a>&amp;= – Operátor (Visual Basic)
Zřetězí `String` výraz, který se `String` proměnné nebo vlastnosti a výsledek přiřadí proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Všechny `String` proměnné nebo vlastnosti.  
  
 `expression`  
 Požadováno. Všechny `String` výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `&=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole. Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md). `&=` Operátor zřetězí `String` výraz jeho vpravo `String` proměnné nebo vlastnosti na levé straně a přiřadí výsledek proměnné nebo vlastnost na levé straně.  
  
## <a name="overloading"></a>Přetížení  
 [& Operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Přetížení `&` operátor má vliv na chování `&=` operátor. Pokud váš kód používá `&=` na třídu nebo strukturu, která přetížení `&`, ujistěte se, pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `&=` operátor ke zřetězení dva `String` proměnné a přiřazení výsledek, který má první proměnné.  
  
 [!code-vb[VbVbalrOperators#3](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/and-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [& – operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [+= – operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
