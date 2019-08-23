---
title: '&amp;– Operátor (Visual Basic)'
ms.date: 07/20/2015
f1_keywords:
- vb.&
helpviewer_keywords:
- And (&) operator
- ampersand operator (&)
- '& operator'
- concatenation operators [Visual Basic], syntax
- strings [Visual Basic], concatenating
ms.assetid: fefc3d00-cbf1-475c-8c5e-6fb213b3f85a
ms.openlocfilehash: d387b2dfdbb3fefe357364f7b2a3dde155cbd489
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968356"
---
# <a name="amp-operator-visual-basic"></a>&amp;– Operátor (Visual Basic)
Generuje řetězení řetězců dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Jakékoli `String` proměnné `Object` nebo.  
  
 `expression1`  
 Povinný parametr. Libovolný výraz s datovým typem, který se rozšiřuje `String`na.  
  
 `expression2`  
 Povinný parametr. Libovolný výraz s datovým typem, který se rozšiřuje `String`na.  
  
## <a name="remarks"></a>Poznámky  
 Pokud `expression1` datový typ `String`nebo `expression2` `String`není, ale rozšiřuje se na, je převeden na. `String` Pokud se některý z datových typů nerozšíří na `String`, kompilátor vygeneruje chybu.  
  
 Datový typ `result` je `String`. Pokud se jeden nebo oba výrazy vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md) nebo pokud <xref:System.DBNull.Value?displayProperty=nameWithType>mají hodnotu, považují se za řetězec s hodnotou "".  
  
> [!NOTE]
> Operátor může být přetížen, což znamená, že třída nebo struktura může předefinovat své chování, pokud má operand typ této třídy nebo struktury. `&` Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Znak ampersand (&) lze také použít k identifikaci proměnných jako typu `Long`. Další informace naleznete v tématu [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se `&` používá operátor k vynucení zřetězení řetězců. Výsledkem je řetězcová hodnota představující zřetězení dvou řetězcových operandů.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [&= – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory zřetězení v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
