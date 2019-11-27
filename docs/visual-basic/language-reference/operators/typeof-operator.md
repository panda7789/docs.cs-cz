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
|Třída|`objectexpression` je typu `typename` nebo dědí z `typename`|  
|Struktura|`objectexpression` je typu `typename`|  
|Rozhraní|`objectexpression` implementuje `typename` nebo dědí ze třídy, která implementuje `typename`|  
  
 Pokud běhový typ `objectexpression` splňuje kritérium kompatibility, `result` je `True`. V opačném případě `result` `False`.  Pokud je `objectexpression` null, pak `TypeOf`...`Is` vrátí `False`a...`IsNot` vrátí `True`.  
  
 `TypeOf` se vždy používá s klíčovým slovem `Is` k vytvoření `TypeOf`...`Is` nebo pomocí klíčového slova `IsNot` k vytvoření výrazu `TypeOf`...`IsNot`.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `TypeOf`...`Is` výrazy k otestování kompatibility typů dvou proměnných odkazů na objekty s různými datovými typy.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Proměnná `refInteger` má běhový typ `Integer`. Je kompatibilní s `Integer`, ale ne s `Double`. Proměnná `refForm` má běhový typ <xref:System.Windows.Forms.Form>. Je kompatibilní s <xref:System.Windows.Forms.Form>, protože to je jeho typ s <xref:System.Windows.Forms.Control>, protože <xref:System.Windows.Forms.Form> dědí od <xref:System.Windows.Forms.Control>a s <xref:System.ComponentModel.IComponent>, protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component>, které implementuje <xref:System.ComponentModel.IComponent>. `refForm` ale není kompatibilní s <xref:System.Windows.Forms.Label>.  
  
## <a name="see-also"></a>Viz také:

- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operátory porovnávání v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
