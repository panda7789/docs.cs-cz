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
ms.openlocfilehash: 47d3239af6ff24501e6babc23c0db4103c477796
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701071"
---
# <a name="-operator-visual-basic"></a>*= – operátor (Visual Basic)
Vynásobí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty *= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Požadováno. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `*=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operátor `*=` nejprve vynásobí hodnotu výrazu (na pravé straně operátoru) hodnotou proměnné nebo vlastnosti (na levé straně operátoru). Operátor potom přiřadí výsledek této operace proměnné nebo vlastnosti.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor *](../../../visual-basic/language-reference/operators/multiplication-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, když má operand typ této třídy nebo struktury. Přetížení operátoru `*` má vliv na chování operátoru `*=`. Pokud váš kód používá `*=` na třídě nebo struktuře, která přetěžuje `*`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu je použit operátor `*=` k vynásobení jedné proměnné `Integer` sekundou a k první proměnné se přiřadí výsledek.  
  
 [!code-vb[VbVbalrOperators#5](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#5)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor *](../../../visual-basic/language-reference/operators/multiplication-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
