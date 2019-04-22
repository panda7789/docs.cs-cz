---
title: /= – operátor [Visual Basic]
ms.date: 07/20/2015
f1_keywords:
- vb./=
helpviewer_keywords:
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- /= operator [Visual Basic]
- operator /=
- compound assignment statements [Visual Basic]
ms.assetid: a1e22d0e-8380-4761-9da1-84fb51c34821
ms.openlocfilehash: d9d3fa021654d3be1b9d304beb83caa737660264
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58813987"
---
# <a name="-operator-visual-basic"></a>/= – operátor [Visual Basic]
Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí k proměnné nebo vlastnosti výsledku s plovoucí desetinnou čárkou.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
variableorproperty /= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinný parametr. Všechny číselné proměnné nebo vlastnosti.  
  
 `expression`  
 Povinný parametr. Jakýkoli číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `/=` operátor může být jednoduché skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 `/=` Operátor nejprve vydělí hodnotu proměnné nebo vlastnosti (na levé straně operátoru) hodnotu výrazu (na pravé straně operátoru). Operátor, který se pak přiřadí s plovoucí desetinnou čárkou výsledek této operace na proměnnou nebo vlastnost.  
  
 Tento příkaz přiřadí `Double` hodnotu proměnné nebo vlastnosti na levé straně. Pokud `Option Strict` je `On`, `variableorproperty` musí být `Double`. Pokud `Option Strict` je `Off`, provádí implicitní převod jazyka Visual Basic a přiřadí výslednou hodnotu pro `variableorproperty`, s možnou chybu v době běhu. Další informace najdete v tématu [Widening a zúžení převodů](../../../visual-basic/programming-guide/language-features/data-types/widening-and-narrowing-conversions.md) a [Option Strict – příkaz](../../../visual-basic/language-reference/statements/option-strict-statement.md).  
  
## <a name="overloading"></a>Přetížení  
 [/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md) může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Přetížení `/` operátor má vliv na chování `/=` operátor. Pokud váš kód používá `/=` v třídě nebo struktuře, která přetížení `/`, je nutné pochopit jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `/=` operátor rozdělit jeden `Integer` proměnnou druhé a přiřaďte podíl první proměnné.  
  
 [!code-vb[VbVbalrOperators#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#17)]  
  
## <a name="see-also"></a>Viz také:

- [/ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-operator.md)
- [\\= Operator](../../../visual-basic/language-reference/operators/integer-division-assignment-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
