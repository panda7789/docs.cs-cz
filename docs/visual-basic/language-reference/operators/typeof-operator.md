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
ms.openlocfilehash: c6028f524a16b836310f0c8d564205244515cdc9
ms.sourcegitcommit: 3094dcd17141b32a570a82ae3f62a331616e2c9c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/01/2019
ms.locfileid: "71701286"
---
# <a name="typeof-operator-visual-basic"></a>TypeOf – operátor (Visual Basic)
Kontroluje, zda typ modulu runtime výsledku výrazu je kompatibilní s typem zadaného typu.
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = TypeOf objectexpression Is typename  
```  
  
```vb  
result = TypeOf objectexpression IsNot typename  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Vrátil. Hodnota `Boolean`.  
  
 `objectexpression`  
 Požadováno. Libovolný výraz, který je vyhodnocen jako typ odkazu.  
  
 `typename`  
 Požadováno. Libovolný název datového typu.  
  
## <a name="remarks"></a>Poznámky  
 Operátor `TypeOf` určuje, zda je běhový typ `objectexpression` kompatibilní s `typename`. Kompatibilita závisí na kategorii typu `typename`. Následující tabulka ukazuje, jak je určována kompatibilita.  
  
|Typ kategorie `typename`|Kritérium kompatibility|  
|---------------------------------|-----------------------------|  
|Třída|`objectexpression` je typu `typename` nebo dědí z `typename`.|  
|Struktura|`objectexpression` je typu `typename`.|  
|Rozhraní|`objectexpression` implementuje `typename` nebo dědí ze třídy, která implementuje `typename`.|  
  
 Pokud typ běhu `objectexpression` splňuje kritérium kompatibility, `result` je `True`. V opačném případě `result` `False`.  Pokud je hodnota `objectexpression` null, pak `TypeOf`... `Is` vrátí `False` a... `IsNot` vrátí `True`.  
  
 `TypeOf` se vždy používá s klíčovým slovem `Is` k vytvoření výrazu `TypeOf`... `Is` nebo pomocí klíčového slova `IsNot` pro vytvoření výrazu `TypeOf`... `IsNot`.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu jsou použity výrazy `TypeOf`... `Is` k otestování kompatibility typů dvou proměnných odkazu na objekt s různými datovými typy.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Proměnná `refInteger` má běhový typ `Integer`. Je kompatibilní s `Integer`, ale ne s `Double`. Proměnná `refForm` má běhový typ <xref:System.Windows.Forms.Form>. Je kompatibilní s <xref:System.Windows.Forms.Form>, protože to je jeho typ s <xref:System.Windows.Forms.Control>, protože <xref:System.Windows.Forms.Form> dědí od <xref:System.Windows.Forms.Control> a <xref:System.ComponentModel.IComponent>, protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component>, které implementuje <xref:System.ComponentModel.IComponent>. @No__t-0 však není kompatibilní s <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Viz také:

- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operátory porovnávání v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
