---
title: TypeOf – operátor
ms.date: 07/20/2015
f1_keywords:
- TypeOf
- vb.TypeOf
helpviewer_keywords:
- types [Visual Basic], compatible
- comparison operators [Visual Basic]
- TypeOf...Is expression
- data types [Visual Basic], compatible
- TypeOf operator [Visual Basic]
- compatible data types [Visual Basic]
ms.assetid: 33f65296-659a-4b9a-9a29-c2a91cff68b2
ms.openlocfilehash: 22af5b8f8488ca44e388596530decd52e33525dc
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350894"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf – operátor (Visual Basic)
Checks whether the runtime type of an expression's result is type-compatible with the specified type.
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Returned. A `Boolean` value.  
  
 `objectexpression`  
 Požadováno. Any expression that evaluates to a reference type.  
  
 `typename`  
 Požadováno. Any data type name.  
  
## <a name="remarks"></a>Poznámky  
 The `TypeOf` operator determines whether the run-time type of `objectexpression` is compatible with `typename`. The compatibility depends on the type category of `typename`. The following table shows how compatibility is determined.  
  
|Type category of `typename`|Compatibility criterion|  
|---------------------------------|-----------------------------|  
|Třída|`objectexpression` is of type `typename` or inherits from `typename`|  
|Struktura|`objectexpression` is of type `typename`|  
|Rozhraní|`objectexpression` implements `typename` or inherits from a class that implements `typename`|  
  
 If the run-time type of `objectexpression` satisfies the compatibility criterion, `result` is `True`. Otherwise, `result` is `False`.  If `objectexpression` is null, then `TypeOf`...`Is` returns `False`, and ...`IsNot` returns `True`.  
  
 `TypeOf` is always used with the `Is` keyword to construct a `TypeOf`...`Is` expression, or with the `IsNot` keyword to construct a `TypeOf`...`IsNot` expression.  
  
## <a name="example"></a>Příklad  
 The following example uses `TypeOf`...`Is` expressions to test the type compatibility of two object reference variables with various data types.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 The variable `refInteger` has a run-time type of `Integer`. It is compatible with `Integer` but not with `Double`. The variable `refForm` has a run-time type of <xref:System.Windows.Forms.Form>. It is compatible with <xref:System.Windows.Forms.Form> because that is its type, with <xref:System.Windows.Forms.Control> because <xref:System.Windows.Forms.Form> inherits from <xref:System.Windows.Forms.Control>, and with <xref:System.ComponentModel.IComponent> because <xref:System.Windows.Forms.Form> inherits from <xref:System.ComponentModel.Component>, which implements <xref:System.ComponentModel.IComponent>. However, `refForm` is not compatible with <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Viz také:

- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Comparison Operators in Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Operator Precedence in Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
