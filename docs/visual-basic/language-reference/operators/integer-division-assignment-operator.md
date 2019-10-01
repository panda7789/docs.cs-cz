---
title: Operátor \= (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- '\='
- vb.\=
helpviewer_keywords:
- '\= operator [Visual Basic]'
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- operator \= [Visual Basic]
- compound assignment statements [Visual Basic]
ms.assetid: 6f39915d-e398-4045-afcc-da6885e57b9c
ms.openlocfilehash: d7b4a6946cc38984272a6b63e14e8c1db2825a5e
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71700670"
---
# <a name="-operator"></a>\\ = – operátor
Vydělí hodnotu proměnné nebo vlastnosti hodnotou výrazu a přiřadí celočíselný výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty \= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Jakákoli číselná proměnná nebo vlastnost.  
  
 `expression`  
 Požadováno. Libovolný číselný výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `\=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md).  
  
 Operátor `\=` rozděluje hodnotu proměnné nebo vlastnosti nalevo od hodnoty vpravo a přiřadí celočíselný výsledek proměnné nebo vlastnosti na levé straně.  
  
 Další informace o celočíselném dělení naleznete v tématu [operátor \ (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md).  
  
## <a name="overloading"></a>Přetížení  
 Operátor `\` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Přetížení operátoru `\` má vliv na chování operátoru `\=`. Pokud váš kód používá `\=` na třídě nebo struktuře, která přetěžuje `\`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `\=` k rozdělení jedné proměnné `Integer` o sekundu a přiřazení celého výsledku k první proměnné.  
  
 [!code-vb[VbVbalrOperators#19](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#19)]  
  
## <a name="see-also"></a>Viz také:

- [\ – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/integer-division-operator.md)
- [/= – Operátor (Visual Basic)](../../../visual-basic/language-reference/operators/floating-point-division-assignment-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Aritmetické operátory](../../../visual-basic/language-reference/operators/arithmetic-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
