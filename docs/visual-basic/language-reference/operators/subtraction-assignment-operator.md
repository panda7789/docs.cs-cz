---
title: -= – operátor
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
ms.openlocfilehash: 4f403cd8a28f8d9d0ba1d24b0792a352a9c961db
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406402"
---
# <a name="--operator-visual-basic"></a>-= – operátor (Visual Basic)
Odečte hodnotu výrazu z hodnoty proměnné nebo vlastnosti a přiřadí výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty -= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinná hodnota. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Povinná hodnota. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `-=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md).  
  
 `-=`Operátor nejprve ododečte hodnotu výrazu (na pravé straně operátoru) z hodnoty proměnné nebo vlastnosti (na levé straně operátoru). Operátor potom přiřadí výsledek této operace proměnné nebo vlastnosti.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor-operátor (Visual Basic)](subtraction-operator.md) může být *přetížený*, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. Přetížení `-` operátoru ovlivňuje chování `-=` operátoru. Pokud váš kód používá `-=` pro třídu nebo strukturu, která je přetížena `-` , ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `-=` operátor k odečtení jedné `Integer` proměnné od druhé a přiřazení výsledku k druhé proměnné.  
  
 [!code-vb[VbVbalrOperators#11](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#11)]  
  
## <a name="see-also"></a>Viz také

- [- – operátor (Visual Basic)](subtraction-operator.md)
- [Operátory přiřazení](assignment-operators.md)
- [Aritmetické operátory](arithmetic-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
