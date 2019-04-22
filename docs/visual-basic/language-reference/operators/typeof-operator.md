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
ms.openlocfilehash: 7162fcc24595bbb16d268d5d9e1ea4d82f6e67fb
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58829860"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf – operátor (Visual Basic)
Porovná proměnné odkazu na objekt k datovému typu.  
  
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
 Povinný parametr. Libovolný výraz, který se vyhodnotí na typ odkazu.  
  
 `typename`  
 Povinný parametr. Všechna data, zadejte název.  
  
## <a name="remarks"></a>Poznámky  
 `TypeOf` Operátor určuje, zda za běhu typ `objectexpression` je kompatibilní s `typename`. Kompatibilita závisí na typu kategorie `typename`. Následující tabulka ukazuje, jak se určují kompatibilitu.  
  
|Typ kategorie `typename`|Kritérium kompatibility|  
|---------------------------------|-----------------------------|  
|Třída|`objectexpression` je typu `typename` nebo dědí z `typename`|  
|Struktura|`objectexpression` je typu `typename`|  
|Rozhraní|`objectexpression` implementuje `typename` nebo dědí z třídy, která implementuje `typename`|  
  
 Pokud typ za běhu `objectexpression` splňuje kritéria kompatibility `result` je `True`. V opačném případě `result` je `False`.  Pokud `objectexpression` má hodnotu null, pak `TypeOf`... `Is` vrátí `False`, a... `IsNot` vrátí `True`.  
  
 `TypeOf` je vždy použito s `Is` – klíčové slovo k vytvoření `TypeOf`... `Is` výrazu, nebo se `IsNot` – klíčové slovo k vytvoření `TypeOf`... `IsNot` výrazu.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `TypeOf`... `Is` výrazy pro testování kompatibility typ dvou objektů referenční proměnné s různými datovými typy.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Proměnná `refInteger` je za běhu typu `Integer`. Je kompatibilní s `Integer` , ale ne s `Double`. Proměnná `refForm` je za běhu typu <xref:System.Windows.Forms.Form>. Je kompatibilní s <xref:System.Windows.Forms.Form> protože jeho typ, který je s <xref:System.Windows.Forms.Control> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.Windows.Forms.Control>a s <xref:System.ComponentModel.IComponent> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component>, který implementuje <xref:System.ComponentModel.IComponent>. Ale `refForm` není kompatibilní s <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Viz také:

- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
