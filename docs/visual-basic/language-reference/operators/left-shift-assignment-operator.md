---
title: '&lt;&lt;= Operator (Visual Basic)'
ms.date: 07/20/2015
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
ms.openlocfilehash: 9d4f367506c847ddf2478dd1ea07e28332cc62a2
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54677768"
---
# <a name="ltlt-operator-visual-basic"></a>&lt;&lt;= Operator (Visual Basic)
Provede aritmetický operátor posunu vlevo na základě hodnoty proměnnou nebo vlastnost a přiřadí výsledek zpět na proměnnou nebo vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty <<= amount  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinný parametr. Proměnná nebo vlastnost celočíselného typu (`SByte`, `Byte`, `Short`, `UShort`, `Integer`, `UInteger`, `Long`, nebo `ULong`).  
  
 `amount`  
 Povinný parametr. Číselný výraz datový typ, který rozšiřuje na `Integer`.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `<<=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `<<=` Operátor nejprve provede aritmetický operátor posunu vlevo na hodnotě proměnné nebo vlastnosti. Operátor, který se pak přiřadí výsledek této operace zpět na tuto proměnnou nebo vlastnost.  
  
 Aritmetické staffhubu nejsou cyklické, což znamená, že nejsou na druhém konci znovuzavedeno bity posunuly jeden konec výsledek. V aritmetických posunutí doleva bity posunuta mimo rozsah datového typu výsledku ignorovány a bitové pozice uvolněné na pravé straně jsou nastaveny na hodnotu nula.  
  
## <a name="overloading"></a>Přetížení  
 [<< Operátor](../../../visual-basic/language-reference/operators/left-shift-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Přetížení `<<` operátor má vliv na chování `<<=` operátor. Pokud váš kód používá `<<=` v třídě nebo struktuře, která přetížení `<<`, je nutné pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `<<=` operátor shift bitový vzor z `Integer` proměnnou zanechaný určenou dobu a přiřadit výsledek do proměnné.  
  
 [!code-vb[VbVbalrOperators#13](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/left-shift-assignment-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [<< – operátor](../../../visual-basic/language-reference/operators/left-shift-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operátory bitového posunu](../../../visual-basic/language-reference/operators/bit-shift-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
