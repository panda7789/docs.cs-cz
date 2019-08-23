---
title: Is – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.is
helpviewer_keywords:
- comparison operators [Visual Basic]
- equivalent objects
- TypeOf...Is expression
- Is operator [Visual Basic]
ms.assetid: 8045a6c8-2a83-45b6-ad47-d09a704c656d
ms.openlocfilehash: a5481a9bce01e84ce4f078335c8cd15a747a3c51
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917218"
---
# <a name="is-operator-visual-basic"></a>Is – operátor (Visual Basic)
Porovná dvě proměnné odkazu na objekt.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Libovolná `Boolean` hodnota.  
  
 `object1`  
 Povinný parametr. Libovolný `Object` název.  
  
 `object2`  
 Povinný parametr. Libovolný `Object` název.  
  
## <a name="remarks"></a>Poznámky  
 `Is` Operátor určuje, zda dva odkazy na objekt odkazují na stejný objekt. Ale neprovádí porovnávání hodnot. Pokud `object1` a `True` `result` `result` `False`oba odkazují na přesnou stejnou instanci objektu, je; Pokud ne, je. `object2`  
  
 `Is`lze také použít s `TypeOf` klíčovým slovem pro `TypeOf`vytvoření... `Is` výraz, který testuje, zda je objektová proměnná kompatibilní s datovým typem.  
  
> [!NOTE]
> `Is` Klíčové slovo se používá také v rámci [výběru... Příkaz Case](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Is` operátor pro porovnání párů odkazů na objekty. Výsledky jsou přiřazeny k `Boolean` hodnotě, která představuje, zda jsou dva objekty identické.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Jak ukazuje předchozí příklad, lze použít `Is` operátor k otestování počátečních a pozdních vázaných objektů.  
  
## <a name="see-also"></a>Viz také:

- [Operátor Typeof](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operátory porovnávání v Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorita operátorů v Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
