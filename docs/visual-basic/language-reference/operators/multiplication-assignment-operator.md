---
title: '*= – operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.*=
helpviewer_keywords:
- operator *=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '*= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 96c86509-6eb8-4682-8226-3852e049376f
ms.openlocfilehash: d672ac147a4d7b2c21f4fcb7ee6cdf91b8b4924b
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56965329"
---
# <a name="-operator-visual-basic"></a>*= – operátor (Visual Basic)
Vynásobí hodnotu proměnné nebo vlastnosti hodnotou výrazu a výsledek přiřadí proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinný parametr. Všechny číselné proměnné nebo vlastnosti.  
  
 `expression`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `*=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `*=` Operátor nejprve vynásobí hodnotu výrazu (na pravé straně operátoru) hodnotu proměnné nebo vlastnosti (na levé straně operátoru). Operátor, který se pak přiřadí výsledek této operace na proměnnou nebo vlastnost.  
  
## <a name="overloading"></a>Přetížení  
 [* – Operátor](../../../visual-basic/language-reference/operators/multiplication-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Přetížení `*` operátor má vliv na chování `*=` operátor. Pokud váš kód používá `*=` v třídě nebo struktuře, která přetížení `*`, je nutné pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `*=` operátor násobit jeden `Integer` proměnné tak, že druhé a přiřadit výsledek, který má první proměnné.  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Viz také:
- [* – operátor](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
