---
title: Not – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.Not
helpviewer_keywords:
- Boolean expressions, negating
- operators [Visual Basic], bitwise
- negation operator [Visual Basic]
- inverse bit values in variables [Visual Basic]
- bitwise operators [Visual Basic], NOT operator
- bitwise comparison [Visual Basic]
- Not operator [Visual Basic]
- logical negation
- operators [Visual Basic], negation
ms.assetid: 8f2ea83c-d2ed-480a-a474-3042a1cad9b5
ms.openlocfilehash: 08b091ccf6c50438b5ad9d6c445510112abe7418
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348298"
---
# <a name="not-operator-visual-basic"></a>Not – operátor (Visual Basic)
Performs logical negation on a `Boolean` expression, or bitwise negation on a numeric expression.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = Not expression  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Any `Boolean` or numeric expression.  
  
 `expression`  
 Požadováno. Any `Boolean` or numeric expression.  
  
## <a name="remarks"></a>Poznámky  
 For `Boolean` expressions, the following table illustrates how `result` is determined.  
  
|If `expression` is|The value of `result` is|  
|------------------------|------------------------------|  
|`True`|`False`|  
|`False`|`True`|  
  
 For numeric expressions, the `Not` operator inverts the bit values of any numeric expression and sets the corresponding bit in `result` according to the following table.  
  
|If bit in `expression` is|The bit in `result` is|  
|-------------------------------|----------------------------|  
|1|0|  
|0|1|  
  
> [!NOTE]
> Since the logical and bitwise operators have a lower precedence than other arithmetic and relational operators, any bitwise operations should be enclosed in parentheses to ensure accurate execution.  
  
## <a name="data-types"></a>Datové typy  
 For a Boolean negation, the data type of the result is `Boolean`. For a bitwise negation, the result data type is the same as that of `expression`. However, if expression is `Decimal`, the result is `Long`.  
  
## <a name="overloading"></a>Přetížení  
 The `Not` operator can be *overloaded*, which means that a class or structure can redefine its behavior when its operand has the type of that class or structure. If your code uses this operator on such a class or structure, be sure you understand its redefined behavior. For more information, see [Operator Procedures](../../../visual-basic/programming-guide/language-features/procedures/operator-procedures.md).  
  
## <a name="example"></a>Příklad  
 The following example uses the `Not` operator to perform logical negation on a `Boolean` expression. The result is a `Boolean` value that represents the reverse of the value of the expression.  
  
 [!code-vb[VbVbalrOperators#33](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#33)]  
  
 The preceding example produces results of `False` and `True`, respectively.  
  
## <a name="example"></a>Příklad  
 The following example uses the `Not` operator to perform logical negation of the individual bits of a numeric expression. The bit in the result pattern is set to the reverse of the corresponding bit in the operand pattern, including the sign bit.  
  
 [!code-vb[VbVbalrOperators#34](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#34)]  
  
 The preceding example produces results of –11, –9, and –7, respectively.  
  
## <a name="see-also"></a>Viz také:

- [Logical/Bitwise Operators (Visual Basic)](../../../visual-basic/language-reference/operators/logical-bitwise-operators.md)
- [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Logical and Bitwise Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/logical-and-bitwise-operators.md)
