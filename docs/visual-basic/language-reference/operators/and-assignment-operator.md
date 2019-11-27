---
title: '&amp;= – operátor'
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
ms.openlocfilehash: 8668bfcbf32bb34b422efe8116bbd12a2d80b1d4
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350269"
---
# <a name="amp-operator-visual-basic"></a>&amp;= – operátor (Visual Basic)
Zřetězí výraz `String` na `String` proměnnou nebo vlastnost a přiřadí výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Požadováno. Jakákoli `String` proměnnou nebo vlastnost.  
  
 `expression`  
 Požadováno. Libovolný výraz `String`.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně operátoru `&=` může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../../../visual-basic/language-reference/modifiers/readonly.md). Operátor `&=` zřetězí výraz `String` na základě jeho práva na `String` proměnnou nebo vlastnost nalevo a přiřadí výsledek proměnné nebo vlastnosti na levé straně.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor &](../../../visual-basic/language-reference/operators/concatenation-operator.md) lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Přetížení operátoru `&` má vliv na chování operátoru `&=`. Pokud váš kód používá `&=` ve třídě nebo struktuře, která přetěžuje `&`, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `&=` k zřetězení dvou proměnných `String` a přiřazení výsledku první proměnné.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také:

- [& – operátor](../../../visual-basic/language-reference/operators/concatenation-operator.md)
- [+= – operátor](../../../visual-basic/language-reference/operators/addition-assignment-operator.md)
- [Operátory přiřazení](../../../visual-basic/language-reference/operators/assignment-operators.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Příkazy](../../../visual-basic/programming-guide/language-features/statements.md)
