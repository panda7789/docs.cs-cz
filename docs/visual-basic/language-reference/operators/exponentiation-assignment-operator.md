---
title: "^= – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords: vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: fa9d87d2f090a8c18aaab742e73878c7b80f55c0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="-operator-visual-basic"></a>^= – operátor (Visual Basic)
Vyvolá hodnoty proměnné nebo vlastnost exponentem výrazu a přiřadí výsledek zpět do proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Číselné proměnné nebo vlastnost.  
  
 `expression`  
 Požadováno. Jakýkoli číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `^=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole. Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `^=` Operátor nejprve vyvolá hodnota proměnné nebo vlastnosti (na levé straně operátoru) exponentem hodnotu výrazu (na pravé straně operátoru). Operátor poté přiřadí výsledek této operace zpět do proměnné nebo vlastnosti.  
  
 Visual Basic vždy provede exponenciální zápis v [dvojitý datový typ](../../../visual-basic/language-reference/data-types/double-data-type.md). Operandy žádné jiného typu se převedou na `Double`, a výsledek je vždy `Double`.  
  
 Hodnota `expression` může být zlomkové záporné nebo obojí.  
  
## <a name="overloading"></a>Přetížení  
 [^ – Operátor](../../../visual-basic/language-reference/operators/exponentiation-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Přetížení `^` operátor má vliv na chování `^=` operátor. Pokud váš kód používá `^=` na třídu nebo strukturu, která přetížení `^`, ujistěte se, pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `^=` operátor umožňuje aktivovat hodnota jednoho `Integer` proměnné exponentem druhý proměnné a přiřazení výsledek, který má první proměnné.  
  
 [!code-vb[VbVbalrOperators#21](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/exponentiation-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [^ – Operátor](../../../visual-basic/language-reference/operators/exponentiation-operator.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
