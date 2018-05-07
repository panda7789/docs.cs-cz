---
title: TypeOf – operátor (Visual Basic)
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
ms.openlocfilehash: fe287794423048e993d953c83fc8590a06b7a5e3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="typeof-operator-visual-basic"></a>TypeOf – operátor (Visual Basic)
Porovná proměnná odkaz objektu k datovému typu.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = TypeOf objectexpression Is typename  
```  
  
```  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Vrátí. A `Boolean` hodnotu.  
  
 `objectexpression`  
 Požadováno. Jakýkoli výraz, jehož výsledkem odkazového typu.  
  
 `typename`  
 Požadováno. Všechna data, zadejte název.  
  
## <a name="remarks"></a>Poznámky  
 `TypeOf` Operátor určuje, zda běhu typ `objectexpression` je kompatibilní s `typename`. Kompatibility závisí na typu kategorii `typename`. Následující tabulka uvádí, jakým způsobem je určován kompatibility.  
  
|Typ kategorie `typename`|Kritérium kompatibility|  
|---------------------------------|-----------------------------|  
|Třída|`objectexpression` je typu `typename` nebo dědí z `typename`|  
|Struktura|`objectexpression` je typu `typename`|  
|Rozhraní|`objectexpression` implementuje `typename` nebo dědí z třídy, který implementuje `typename`|  
  
 Pokud běhu typ `objectexpression` splňuje kritéria kompatibility `result` je `True`. V opačném `result` je `False`.  Pokud `objectexpression` má hodnotu null, pak `TypeOf`... `Is` vrátí `False`, a... `IsNot` vrátí `True`.  
  
 `TypeOf` vždy používá s `Is` – klíčové slovo vytvořit `TypeOf`... `Is` výrazu, nebo pomocí `IsNot` – klíčové slovo vytvořit `TypeOf`... `IsNot` výraz.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `TypeOf`... `Is` výrazy pro testování kompatibility typu dva objektu referenční proměnné s různými datovými typy.  
  
 [!code-vb[VbVbalrOperators#39](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/typeof-operator_1.vb)]  
  
 Proměnná `refInteger` má typ spuštění `Integer`. Je kompatibilní s `Integer` , ale ne při `Double`. Proměnná `refForm` má typ spuštění <xref:System.Windows.Forms.Form>. Je kompatibilní s <xref:System.Windows.Forms.Form> je její typ se totiž <xref:System.Windows.Forms.Control> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.Windows.Forms.Control>a s <xref:System.ComponentModel.IComponent> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component>, který implementuje <xref:System.ComponentModel.IComponent>. Ale `refForm` není kompatibilní s <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Viz také  
 [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)  
 [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
