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
ms.openlocfilehash: 0cce36073b53442bce63f966f3bd94bd5d70d2a8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84406323"
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
 Vrátil. `Boolean`Hodnota.  
  
 `objectexpression`  
 Povinná hodnota. Libovolný výraz, který je vyhodnocen jako typ odkazu.  
  
 `typename`  
 Povinná hodnota. Libovolný název datového typu.  
  
## <a name="remarks"></a>Poznámky  
 `TypeOf`Operátor určuje, zda je běhový typ `objectexpression` kompatibilní s `typename` . Kompatibilita závisí na kategorii typu v `typename` . Následující tabulka ukazuje, jak je určována kompatibilita.  
  
|Kategorie typu`typename`|Kritérium kompatibility|  
|---------------------------------|-----------------------------|  
|Třída|`objectexpression`je typu `typename` nebo dědí z`typename`|  
|Struktura|`objectexpression`je typu`typename`|  
|Rozhraní|`objectexpression`implementuje `typename` nebo dědí z třídy, která implementuje`typename`|  
  
 Pokud typ běhu `objectexpression` splňuje kritéria kompatibility, `result` je `True` . V opačném případě `result` je `False` .  Pokud `objectexpression` je null, pak `TypeOf` ... `Is` vrátí `False` a... `IsNot` vrátí `True` .  
  
 `TypeOf`se vždy používá s `Is` klíčovým slovem k sestavení `TypeOf` výrazu... `Is` nebo s `IsNot` klíčovým slovem pro sestavení `TypeOf` výrazu... `IsNot` .  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `TypeOf` výrazy... `Is` k otestování kompatibility typů dvou proměnných odkazů na objekty s různými datovými typy.  
  
 [!code-vb[VbVbalrOperators#39](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#39)]  
  
 Proměnná `refInteger` má běhový typ `Integer` . Je kompatibilní s, `Integer` ale ne s `Double` . Proměnná `refForm` má běhový typ <xref:System.Windows.Forms.Form> . Je kompatibilní s, <xref:System.Windows.Forms.Form> protože to je jeho typ s, <xref:System.Windows.Forms.Control> protože <xref:System.Windows.Forms.Form> dědí z, <xref:System.Windows.Forms.Control> a s, <xref:System.ComponentModel.IComponent> protože <xref:System.Windows.Forms.Form> dědí z <xref:System.ComponentModel.Component> , který implementuje <xref:System.ComponentModel.IComponent> . Není však `refForm` kompatibilní se systémem <xref:System.Windows.Forms.Label> .  
  
## <a name="see-also"></a>Viz také

- [Is – operátor](is-operator.md)
- [IsNot – operátor](isnot-operator.md)
- [Operátory porovnání v jazyce Visual Basic](../../programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorita operátorů v jazyce Visual Basic](operator-precedence.md)
- [Operátory uvedené podle funkce](operators-listed-by-functionality.md)
- [Operátory a výrazy](../../programming-guide/language-features/operators-and-expressions/index.md)
