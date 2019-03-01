---
title: ^= – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.^=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- ^= operator [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 397da132-2d96-4a85-a7bc-f7c730a608c9
ms.openlocfilehash: efea38d7da13b67490f498658e7739929517dba2
ms.sourcegitcommit: 40364ded04fa6cdcb2b6beca7f68412e2e12f633
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2019
ms.locfileid: "56964922"
---
# <a name="-operator-visual-basic"></a>^= – operátor (Visual Basic)
Vyvolá hodnotu proměnné nebo vlastnosti k elektrické energie výrazu a přiřadí výsledek zpět na proměnnou nebo vlastnost.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty ^= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinný parametr. Všechny číselné proměnné nebo vlastnosti.  
  
 `expression`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `^=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `^=` Nejprve Umocní hodnotu proměnné nebo vlastnosti (na levé straně operátoru) k elektrické energie hodnota výrazu (na pravé straně operátoru). Operátor, který se pak přiřadí výsledek této operace zpět na proměnnou nebo vlastnost.  
  
 Visual Basic vždy provádí umocnění v [datový typ Double](../../../visual-basic/language-reference/data-types/double-data-type.md). Jakýkoli jiný typ operandy jsou převedeny na `Double`, a výsledek je vždy `Double`.  
  
 Hodnota `expression` může být zlomkové záporné nebo obojí.  
  
## <a name="overloading"></a>Přetížení  
 [^ – Operátor](../../../visual-basic/language-reference/operators/exponentiation-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Přetížení `^` operátor má vliv na chování `^=` operátor. Pokud váš kód používá `^=` v třídě nebo struktuře, která přetížení `^`, je nutné pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `^=` operátor zvýšit hodnotu jedné `Integer` proměnné k elektrické energie z druhé proměnné a přiřadit výsledek, který má první proměnné.  
  
 [!code-vb[VbVbalrOperators#21](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#21)]  
  
## <a name="see-also"></a>Viz také:
- [^ – operátor](../../../visual-basic/language-reference/operators/exponentiation-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
