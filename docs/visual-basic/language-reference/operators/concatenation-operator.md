---
title: Operátor &amp; (Visual Basic)
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
ms.openlocfilehash: aaa7c1b9ab7f6c920180d97b55c3bdeb23f00e02
ms.sourcegitcommit: 35da8fb45b4cca4e59cc99a5c56262c356977159
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/28/2019
ms.locfileid: "71592246"
---
# <a name="amp-operator-visual-basic"></a>Operátor &amp; (Visual Basic)
Generuje řetězení řetězců dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Jakákoli proměnná `String` nebo `Object`.  
  
 `expression1`  
 Povinný parametr. Libovolný výraz s datovým typem, který se rozšíří na `String`.  
  
 `expression2`  
 Povinný parametr. Libovolný výraz s datovým typem, který se rozšíří na `String`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud datový typ `expression1` nebo `expression2` není `String`, ale rozšiřuje na `String`, je převeden na `String`. Pokud se některý z datových typů nerozšíří na `String`, kompilátor vygeneruje chybu.  
  
 Datový typ `result` je `String`. Pokud se jeden nebo oba výrazy vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md) nebo pokud mají hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType>, považují se za řetězec s hodnotou "".  
  
> [!NOTE]
> Operátor `&` lze přetížit, což znamená, že třída nebo struktura může předefinovat *chování, pokud*operand má typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Znak ampersand (&) lze také použít k identifikaci proměnných jako typu `Long`. Další informace naleznete v tématu [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá operátor `&` k vynucení zřetězení řetězců. Výsledkem je řetězcová hodnota představující zřetězení dvou řetězcových operandů.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [&= – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory zřetězení v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
