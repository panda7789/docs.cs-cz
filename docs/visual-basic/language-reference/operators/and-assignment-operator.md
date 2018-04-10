---
title: '&amp;= – Operátor (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 929a9e8c3384451679fc52ad478eb03219d67192
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
 [& – Operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md)  
 [+= – Operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
