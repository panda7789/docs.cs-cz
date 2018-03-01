---
title: "-= – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 753e3efca311da9e09c67131969626ff59c130f0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="--operator-visual-basic"></a>-= – operátor (Visual Basic)
Odečte hodnotu výrazu z hodnoty proměnné nebo vlastnosti a výsledek přiřadí proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Číselné proměnné nebo vlastnost.  
  
 `expression`  
 Požadováno. Jakýkoli číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `-=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole. Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `-=` Hodnotu výrazu (na pravé straně operátoru) operátor nejprve odečítá od hodnoty proměnné nebo vlastnosti (na levé straně operátoru). Výsledek této operace operátor poté přiřadí proměnné nebo vlastnost.  
  
## <a name="overloading"></a>Přetížení  
 [– Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Přetížení `-` operátor má vliv na chování `-=` operátor. Pokud váš kód používá `-=` na třídu nebo strukturu, která přetížení `-`, ujistěte se, pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `-=` operátor má odečíst jeden `Integer` proměnné z jiné a přiřadit výsledek, který má druhé proměnné.  
  
 [!code-vb[VbVbalrOperators#11](codesnippet/VisualBasic/subtraction-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [-– Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
