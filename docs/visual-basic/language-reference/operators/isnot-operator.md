---
title: IsNot – operátor (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
ms.openlocfilehash: e07a775eec003a3e488f6909181aed3f742b4b91
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61768342"
---
# <a name="isnot-operator-visual-basic"></a>IsNot – operátor (Visual Basic)
Porovná dvě proměnné objektových referencí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Povinný parametr. A `Boolean` hodnotu.  
  
 `object1`  
 Povinný parametr. Žádné `Object` proměnné nebo výrazu.  
  
 `object2`  
 Povinný parametr. Žádné `Object` proměnné nebo výrazu.  
  
## <a name="remarks"></a>Poznámky  
 `IsNot` Určuje operátor, pokud reference na dva objekty odkazují na různé objekty. Neprovádí však porovnání hodnot. Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.  
  
 `IsNot` je opakem `Is` operátor. Výhodou `IsNot` je, že se můžete vyhnout nevhodnou syntaxe `Not` a `Is`, což může být obtížně čitelné.  
  
 Můžete použít `Is` a `IsNot` operátory k otestování objekty časné vazby a s pozdní vazbou.  
  
> [!NOTE]
>  `IsNot` Operátor nelze použít k porovnání výrazy vrácených `TypeOf` operátor. Místo toho je nutné použít `Not` a `Is` operátory.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá obě `Is` operátor a `IsNot` operátor k dosažení stejného porovnání.  
  
 [!code-vb[VbVbalrOperators#29](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrOperators/VB/Class1.vb#29)]  
  
## <a name="see-also"></a>Viz také:

- [Operátor Is](../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor Typeof](../../../visual-basic/language-reference/operators/typeof-operator.md)
- [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)
- [Postupy: Otestujte, zda jsou dva objekty stejné](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
