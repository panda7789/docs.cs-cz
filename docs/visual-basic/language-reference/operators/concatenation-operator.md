---
title: '&amp; – operátor'
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
ms.openlocfilehash: 4cae7e59083890e82d754bdaa58942c2224357b0
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74336059"
---
# <a name="amp-operator-visual-basic"></a>Operátor &amp; (Visual Basic)
Generuje řetězení řetězců dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Jakákoli `String` nebo proměnná `Object`.  
  
 `expression1`  
 Požadováno. Libovolný výraz s datovým typem, který se rozšíří na `String`.  
  
 `expression2`  
 Požadováno. Libovolný výraz s datovým typem, který se rozšíří na `String`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud datový typ `expression1` nebo `expression2` není `String`, ale rozšíří na `String`, je převeden na `String`. Pokud se některý z datových typů nerozšíří na `String`, kompilátor vygeneruje chybu.  
  
 Datový typ `result` je `String`. Pokud se jeden nebo oba výrazy vyhodnotí jako [Nothing](../../../visual-basic/language-reference/nothing.md) nebo pokud mají hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType>, považují se za řetězec s hodnotou "".  
  
> [!NOTE]
> Operátor `&` lze přetížit, což znamená, že třída nebo struktura může předefinovat své *chování, pokud*má operand typ této třídy nebo struktury. Pokud váš kód používá tento operátor na takové třídě nebo struktuře, ujistěte se, že rozumíte jeho předefinovanému chování. Další informace naleznete v tématu [procedury operátorů](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
> Znak ampersand (&) lze také použít k identifikaci proměnných jako typ `Long`. Další informace naleznete v tématu [Type Characters](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu se používá operátor `&` k vynucení zřetězení řetězců. Výsledkem je řetězcová hodnota představující zřetězení dvou řetězcových operandů.  
  
 [!code-vb[VbVbalrOperators#2](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#2)]  
  
## <a name="see-also"></a>Viz také:

- [&= – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory zřetězení v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
