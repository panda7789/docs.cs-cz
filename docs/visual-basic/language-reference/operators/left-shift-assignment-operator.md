---
title: '&lt;&lt;= – Operátor (Visual Basic)'
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.<<=
helpviewer_keywords:
- operator <<=
- assignment statements [Visual Basic], compound
- <<= operator [Visual Basic]
- statements [Visual Basic], compound assignment
- operator<<=
- compound assignment statements [Visual Basic]
ms.assetid: 8ad26613-faff-4e2f-89ee-63feee33bfda
caps.latest.revision: 17
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 5c5c36e4f91155c09d01b448777483941d018d9a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt;= – Operátor (Visual Basic)
Provede aritmetický levém posun na hodnotě proměnné nebo vlastnosti a přiřadí výsledek zpět do proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Proměnná nebo vlastnost integrální typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz datový typ, který rozšiřuje na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `<<=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole. Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `<<=` Operátor nejprve provede aritmetický levém posun na hodnotě proměnné nebo vlastnosti. Operátor poté přiřadí výsledek této operace zpět do této proměnné nebo vlastnosti.  
  
 Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci. V aritmetické posunutí doleva jsou zahozeny bits zapuštěno mimo rozsah datového typu výsledek a pozice bit vacated na pravé straně nastaveny na nulu.  
  
## <a name="overloading"></a>Přetížení  
 [<< Operátor](../../../visual-basic/language-reference/operators/left-shift-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Přetížení `<<` operátor má vliv na chování `<<=` operátor. Pokud váš kód používá `<<=` na třídu nebo strukturu, která přetížení `<<`, ujistěte se, pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `<<=` operátor se posunou bit vzor `Integer` proměnná levé ve stanoveném a přiřadit výsledek na proměnnou.  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [<< – Operátor](../../../visual-basic/language-reference/operators/left-shift-operator.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operátory bitového posunutí](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
