---
title: Is – operátor
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: 52fbb39ab0a36c8b947b78f464fad26be05ce204
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74349537"
---
# <a name="is-operator-visual-basic"></a>Is – operátor (Visual Basic)
Porovná dvě proměnné odkazu na objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```vb  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Jakákoli `Boolean` hodnota.  
  
 `object1`  
 Požadováno. Libovolný `Object` název.  
  
 `object2`  
 Požadováno. Libovolný `Object` název.  
  
## <a name="remarks"></a>Poznámky  
 Operátor `Is` určuje, zda dva odkazy na objekt odkazují na stejný objekt. Ale neprovádí porovnávání hodnot. Pokud `object1` a `object2` odkazují na přesnou stejnou instanci objektu, `result` je `True`; Pokud ne, `result` je `False`.  
  
 `Is` lze také použít s klíčovým slovem `TypeOf` k vytvoření výrazu `TypeOf`...`Is`, který testuje, zda je objektová proměnná kompatibilní s datovým typem.  
  
> [!NOTE]
> Klíčové slovo `Is` se používá také v rámci [výběru... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá operátor `Is` pro porovnání párů odkazů na objekty. Výsledky jsou přiřazeny `Boolean` hodnotě, která představuje, zda jsou dva objekty identické.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Jak ukazuje předchozí příklad, lze použít operátor `Is` k otestování počátečních a pozdních vázaných objektů.  
  
## <a name="see-also"></a>Viz také:

- [Operátor Typeof](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operátory porovnávání v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
