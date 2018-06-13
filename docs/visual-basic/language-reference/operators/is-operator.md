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
ms.openlocfilehash: 8beca1dc8788514224f70cacc5b8ede0974f5230
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33601947"
---
# <a name="is-operator-visual-basic"></a>Is – operátor (Visual Basic)
Porovná dvě proměnné objektových referencí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. Všechny `Boolean` hodnotu.  
  
 `object1`  
 Požadováno. Všechny `Object` název.  
  
 `object2`  
 Požadováno. Všechny `Object` název.  
  
## <a name="remarks"></a>Poznámky  
 `Is` Operátor určuje, pokud dva odkazy na objekty odkazují na stejný objekt. Neprovede však porovnání hodnot. Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `True`; Pokud ne, `result` je `False`.  
  
 `Is` Můžete také použít s `TypeOf` – klíčové slovo, aby `TypeOf`... `Is` výraz, který testuje, zda je kompatibilní s datovým typem proměnné objektu.  
  
> [!NOTE]
>  `Is` – Klíčové slovo je používán také [vyberte... Příkaz případ](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Příklad  
 Následující příklad používá `Is` operátor k porovnání páry odkazy na objekty. Výsledky jsou přiřazeny k `Boolean` hodnotu udávající, zda dva objekty jsou identické.  
  
 [!code-vb[VbVbalrOperators#27](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/is-operator_1.vb)]  
  
 Jak ukazuje předchozí příklad, můžete použít `Is` operátor k testování obě časné a pozdní vazba objekty.  
  
## <a name="see-also"></a>Viz také  
 [Operátor Typeof](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)  
 [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
