---
title: -= – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.-=
helpviewer_keywords:
- -= operator [Visual Basic]
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator -=
- compound assignment statements [Visual Basic]
ms.assetid: 5ead0c37-ae50-48f7-8435-8e341d81cae1
ms.openlocfilehash: f857c8bf2f89120e047c49674ce9e8a3bff22f7d
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701308"
---
# <a name="--operator-visual-basic"></a>-= – operátor (Visual Basic)
Odečte hodnotu výrazu z hodnoty proměnné nebo vlastnosti a přiřadí výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Požadováno. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `-=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operátor `-=` nejprve odečte hodnotu výrazu (na pravé straně operátoru) z hodnoty proměnné nebo vlastnosti (na levé straně operátoru). Operátor potom přiřadí výsledek této operace proměnné nebo vlastnosti.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor-operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Přetížení operátoru `-` má vliv na chování operátoru `-=`. Pokud váš kód používá `-=` na třídě nebo struktuře, která přetěžuje `-`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit operátor `-=` pro odečtení jedné proměnné `Integer` od druhé a přiřazení výsledku k druhé proměnné.  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Viz také:

- [-– Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/subtraction-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
