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
ms.openlocfilehash: a59ff4c956724c614342f0ee4c0622a67f1c25e7
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62054952"
---
# <a name="is-operator-visual-basic"></a>Is – operátor (Visual Basic)
Porovná dvě proměnné objektových referencí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 Is object2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. Žádné `Boolean` hodnotu.  
  
 `object1`  
 Povinný parametr. Žádné `Object` název.  
  
 `object2`  
 Povinný parametr. Žádné `Object` název.  
  
## <a name="remarks"></a>Poznámky  
 `Is` Určuje operátor, pokud dva odkazy na objekty odkazují na stejný objekt. Neprovádí však porovnání hodnot. Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `True`; Pokud ne, `result` je `False`.  
  
 `Is` Můžete také použít s `TypeOf` – klíčové slovo, aby `TypeOf`... `Is` výraz, který testuje, jestli je kompatibilní s datovým typem proměnné objektu.  
  
> [!NOTE]
>  `Is` – Klíčové slovo se používá také v [vyberte... Case – příkaz](../../../visual-basic/language-reference/statements/select-case-statement.md).  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu `Is` operátor porovnání dvojice odkazů na objekty. Výsledky jsou přiřazeny k `Boolean` hodnotu udávající, zda dva objekty jsou identické.  
  
 [!code-vb[VbVbalrOperators#27](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#27)]  
  
 Jak ukazuje předchozí příklad, můžete použít `Is` operátor testování obou časné a pozdní vazby objektů.  
  
## <a name="see-also"></a>Viz také:

- [Operátor Typeof](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Operátor IsNot](../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Operátory porovnání v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/operators-and-expressions/comparison-operators.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Operátory uvedené podle funkce](../../../visual-basic/language-reference/operators/operators-listed-by-functionality.md)
- [Operátory a výrazy](../../../visual-basic/programming-guide/language-features/operators-and-expressions/index.md)
