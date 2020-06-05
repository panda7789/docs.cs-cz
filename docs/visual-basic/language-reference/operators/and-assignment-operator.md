---
title: '&amp;= – Operátor'
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
ms.openlocfilehash: db42f7be7225b866eacf5b73066754e91cd1a0f7
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84371983"
---
# <a name="amp-operator-visual-basic"></a>&amp;= – Operátor (Visual Basic)
Zřetězí `String` výraz na `String` proměnnou nebo vlastnost a přiřadí výsledek proměnné nebo vlastnosti.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
variableorproperty &= expression  
```  
  
## <a name="parts"></a>Součásti  
 `variableorproperty`  
 Povinná hodnota. Jakákoli `String` proměnná nebo vlastnost.  
  
 `expression`  
 Povinná hodnota. Libovolný `String` výraz.  
  
## <a name="remarks"></a>Poznámky  
 Element na levé straně `&=` operátoru může být jednoduchá skalární proměnná, vlastnost nebo prvek pole. Proměnná nebo vlastnost nemůže být [jen pro čtení](../modifiers/readonly.md). `&=`Operátor zřetězí `String` výraz na základě jeho práva na `String` proměnnou nebo vlastnost vlevo a výsledek přiřadí proměnné nebo vlastnosti nalevo.  
  
## <a name="overloading"></a>Přetížení  
 [Operátor&](concatenation-operator.md) lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Přetížení `&` operátoru ovlivňuje chování `&=` operátoru. Pokud váš kód používá `&=` pro třídu nebo strukturu, která je přetížena `&` , ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `&=` operátor ke zřetězení dvou `String` proměnných a přiřazení výsledku k první proměnné.  
  
 [!code-vb[VbVbalrOperators#3](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#3)]  
  
## <a name="see-also"></a>Viz také

- [Operátor&](concatenation-operator.md)
- [+ = – Operátor](addition-assignment-operator.md)
- [Operátory přiřazení](assignment-operators.md)
- [Operátory řetězení](concatenation-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Příkazy](../../programming-guide/language-features/statements.md)
