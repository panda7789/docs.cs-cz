---
title: '&amp; – Operátor (Visual Basic)'
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
ms.openlocfilehash: eac99ba38841f6972b5bdc8a01f816519af06288
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54684668"
---
# <a name="amp-operator-visual-basic"></a>&amp; – Operátor (Visual Basic)
Vytvoří spojení řetězců dvou výrazů.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = expression1 & expression2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Žádné `String` nebo `Object` proměnné.  
  
 `expression1`  
 Povinný parametr. Libovolný výraz s datovým typem, který rozšiřuje na `String`.  
  
 `expression2`  
 Povinný parametr. Libovolný výraz s datovým typem, který rozšiřuje na `String`.  
  
## <a name="remarks"></a>Poznámky  
 Pokud datový typ `expression1` nebo `expression2` není `String` ale rozšiřuje na `String`, je převedena na `String`. Pokud některý z datové typy nelze rozšířit na `String`, kompilátor vygeneruje chybu.  
  
 Datový typ `result` je `String`. Pokud jeden nebo oba výrazy [nic](../../../visual-basic/language-reference/nothing.md) nebo mít hodnotu <xref:System.DBNull.Value?displayProperty=nameWithType>, jsou považovány za řetězec s hodnotou "".  
  
> [!NOTE]
>  `&` Operátor může být *přetížené*, což znamená, že třídy nebo struktury lze znovu definovat jeho chování při operand má typ této třídě nebo struktuře. Pokud váš kód používá tento operátor na takové třídy nebo struktury, ujistěte se, že rozumíte jeho Předefinovaná chování. Další informace najdete v tématu [procedury operátoru](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
> [!NOTE]
>  Znak ampersand (&) je také možné identifikovat jako typ proměnné `Long`. Další informace najdete v tématu [znaky typu](../../../visual-basic/programming-guide/language-features/data-types/type-characters.md).  
  
## <a name="example"></a>Příklad  
 V tomto příkladu `&` operátoru pro zřetězení řetězců vynucení. Výsledkem je řetězcovou hodnotu představující zřetězení operandy dva řetězce.  
  
 [!code-vb[VbVbalrOperators#2](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/concatenation-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také:
- [&= – operátor](../../../visual-basic/language-reference/operators/and-assignment-operator.md)
- [Operátory zřetězení](../../../visual-basic/language-reference/operators/concatenation-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory řetězení v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/concatenation-operators.md)
