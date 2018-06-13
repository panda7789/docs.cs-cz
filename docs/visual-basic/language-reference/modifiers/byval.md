---
title: ByVal (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ByVal
- ByVal
helpviewer_keywords:
- ByVal keyword [Visual Basic], contexts
- ByVal keyword [Visual Basic]
ms.assetid: 1eaf4e58-b305-4785-9e3d-e416b9c75598
ms.openlocfilehash: 076289ff303dce58f036d6c7cb1505b151da19f6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602980"
---
# <a name="byval-visual-basic"></a>ByVal (Visual Basic)
Určuje, že je předán argument tak, že volané procedury nebo vlastnost nelze změnit hodnotu proměnné základní argument ve volání kódu.  
  
## <a name="remarks"></a>Poznámky  
 `ByVal` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Declare](../../../visual-basic/language-reference/statements/declare-statement.md)  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Operator](../../../visual-basic/language-reference/statements/operator-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje použití `ByVal` předávání mechanismus s argumentem odkaz na typ parametru. V příkladu je argument `c1`, instance třídy `Class1`. `ByVal` kód v postupech nebude změna základní hodnota argumentu odkaz, `c1`, ale nechrání přístupné pole a vlastnosti `c1`.  
  
 [!code-vb[VbVbalrKeywords#10](../../../visual-basic/language-reference/codesnippet/VisualBasic/byval_1.vb)]  
  
## <a name="see-also"></a>Viz také  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Předávání argumentů podle hodnoty a reference](../../../visual-basic/programming-guide/language-features/procedures/passing-arguments-by-value-and-by-reference.md)
