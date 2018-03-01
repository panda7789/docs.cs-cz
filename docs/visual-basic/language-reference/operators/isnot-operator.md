---
title: "IsNot – operátor (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.isnot
helpviewer_keywords:
- IsNot operator [Visual Basic]
ms.assetid: 8dd2bcdb-0166-48a2-9094-60dfb448f36c
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 969fdebdf15a1f779075c58616ccd16c64976a35
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="isnot-operator-visual-basic"></a>IsNot – operátor (Visual Basic)
Porovná dvě proměnné objektových referencí.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
result = object1 IsNot object2  
```  
  
## <a name="parts"></a>Součásti  
 `result`  
 Požadováno. A `Boolean` hodnotu.  
  
 `object1`  
 Požadováno. Všechny `Object` proměnnou nebo výraz.  
  
 `object2`  
 Požadováno. Všechny `Object` proměnnou nebo výraz.  
  
## <a name="remarks"></a>Poznámky  
 `IsNot` Operátor určuje, pokud dva odkazy na objekty odkazovat na jiné objekty. Neprovede však porovnání hodnot. Pokud `object1` a `object2` odkazují na přesně stejnou instanci objektu, `result` je `False`; Pokud ne, `result` je `True`.  
  
 `IsNot`maska je opakem `Is` operátor. Výhodou `IsNot` je, že se můžete vyhnout nevhodných syntaxi společně s `Not` a `Is`, což může být obtížné číst.  
  
 Můžete použít `Is` a `IsNot` operátory k testování objekty časné vazby a pozdní vazbu.  
  
> [!NOTE]
>  `IsNot` Operátor nelze použít k porovnání vrácená z výrazů `TypeOf` operátor. Místo toho musíte použít `Not` a `Is` operátory.  
  
## <a name="example"></a>Příklad  
 Následující příklad kódu používá i `Is` operátor a `IsNot` operátor provedete stejné porovnání.  
  
 [!code-vb[VbVbalrOperators#29](../../../visual-basic/language-reference/operators/codesnippet/VisualBasic/isnot-operator_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Is – operátor](../../../visual-basic/language-reference/operators/is-operator.md)  
 [Typeof – operátor](../../../visual-basic/language-reference/operators/typeof-operator.md)  
 [Priorita operátorů v jazyce Visual Basic](../../../visual-basic/language-reference/operators/operator-precedence.md)  
 [Postupy: Test, zda dva objekty jsou stejné](../../../visual-basic/programming-guide/language-features/operators-and-expressions/how-to-test-whether-two-objects-are-the-same.md)
