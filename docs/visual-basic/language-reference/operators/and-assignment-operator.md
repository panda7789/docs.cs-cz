---
title: '&amp; = – operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&=
helpviewer_keywords:
- operator &=
- assignment statements [Visual Basic], compound
- statements [Visual Basic], compound assignment
- '&= operator [Visual Basic]'
- compound assignment statements [Visual Basic]
ms.assetid: 0cf262fc-1a05-419a-a503-60013f111c8a
ms.openlocfilehash: 82d791e5d66c301442c99d2cc73e3172c3e30f17
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71591626"
---
# <a name="amp-operator-visual-basic"></a>&amp; = – operátor (Visual Basic)
Zřetězí výraz `String` na proměnnou nebo vlastnost `String` a přiřadí výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinný parametr. Jakákoli proměnná nebo vlastnost `String`.  
  
 `expression`  
 Povinný parametr. Libovolný výraz `String`.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `&=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md). Operátor `&=` zřetězí výraz `String` na jeho pravé straně k proměnné nebo vlastnosti `String` a přiřadí výsledek proměnné nebo vlastnosti na levé straně.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor &](../../../visual-basic/language-reference/operators/concatenation-operator.md) lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Přetížení operátoru `&` má vliv na chování operátoru `&=`. Pokud váš kód používá `&=` na třídě nebo struktuře, která přetěžuje `&`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `&=` ke zřetězení dvou proměnných `String` a přiřazení výsledku k první proměnné.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [& – operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+= – operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
