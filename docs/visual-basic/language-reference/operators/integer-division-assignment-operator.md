---
title: "\\=Operátor"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5ba74f7a433687b306e8b4273f3a2a6d60583396
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator"></a>\\= – Operátor
Vydělí hodnoty proměnné nebo vlastnosti hodnotou výrazu a přiřadí proměnné nebo vlastnosti celé číslo.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Číselné proměnné nebo vlastnost.  
  
 `expression`  
 Požadováno. Jakýkoli číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `\=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole. Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `\=` Operátor vydělí hodnoty proměnné nebo vlastnosti na levé straně, se hodnota na záhlavím vpravo a přiřadí proměnné nebo vlastnosti na levé straně, celé číslo  
  
 Další informace o dělení celého čísla v tématu [\ – operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).  
  
## <a name="overloading"></a>Přetížení  
 `\` Může být operátor *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Přetížení `\` operátor má vliv na chování `\=` operátor. Pokud váš kód používá `\=` na třídu nebo strukturu, která přetížení `\`, ujistěte se, pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `\=` operátor rozdělit jednu `Integer` proměnné sekundu a přiřadit na celé číslo vést k první proměnné.  
  
 [!code-vb[VbVbalrOperators#19](codesnippet/VisualBasic/integer-division-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)  
 [/ = – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
