---
title: '&gt;&gt;= – Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.>>=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator >>= [Visual Basic]
- compound assignment statements [Visual Basic]
- '>>= operator [Visual Basic]'
ms.assetid: 2bcd9abb-7a8c-4229-b75d-8816ff1dc700
ms.openlocfilehash: d0c0ea819741f80e30e55a960b1187699898a3bb
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="gtgt-operator-visual-basic"></a>&gt;&gt;= – Operátor (Visual Basic)
Provede aritmetický správné posun na hodnotě proměnné nebo vlastnosti a přiřadí výsledek zpět do proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty >>= amount  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Proměnná nebo vlastnost integrální typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).  
  
 `amount`  
 Požadováno. Číselný výraz datový typ, který rozšiřuje na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `>>=` operátor může být jednoduché skalární proměnné, vlastnost nebo element pole. Název proměnné nebo vlastnost nelze [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `>>=` Operátor nejprve provádí aritmetické posunutí doprava na hodnotě proměnné nebo vlastnosti. Operátor poté přiřadí výsledek této operace zpět do proměnné nebo vlastnosti.  
  
 Aritmetické posuny nejsou cyklické, což znamená, že služba bits přesunout mimo jeden element end výsledku nejsou znovu uvedeny na druhém konci. V aritmetické posunutí doprava jsou zahozeny bits zapuštěno nad rámec pozici nejvíce vpravo bit a levou krajní bit rozšířena do pozice bit vacated na levé straně. To znamená, že pokud `variableorproperty` má zápornou hodnotu vacated pozice se nastavit na jedno. Pokud `variableorproperty` kladné, nebo pokud je jeho datový typ je typ bez znaménka, vacated pozic nastaveny na nulu.  
  
## <a name="overloading"></a>Přetížení  
 [>> Operátor](../../../visual-basic/language-reference/operators/right-shift-operator.md) může být *přetížený*, což znamená, že třídu nebo strukturu lze znovu definovat své chování při operand má typ třídy nebo struktura. Přetížení `>>` operátor má vliv na chování `>>=` operátor. Pokud váš kód používá `>>=` na třídu nebo strukturu, která přetížení `>>`, ujistěte se, pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `>>=` operátor se posunou bit vzor `Integer` proměnné přímo ve stanoveném a přiřadit výsledek, který má proměnná.  
  
 [!code-vb[VbVbalrOperators#15](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/right-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [>> – operátor](../../../visual-basic/language-reference/operators/right-shift-operator.md)  
 [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)  
 [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
