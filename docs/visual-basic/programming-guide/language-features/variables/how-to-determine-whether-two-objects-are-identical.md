---
title: 'Postupy: Určení, zda dva objekty jsou identické (Visual Basic).'
ms.custom: ''
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.tgt_pltfrm: ''
ms.topic: article
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
caps.latest.revision: 19
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 266e878e7f5fa8deb1c8cd91795af8d63ded0177
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Postupy: Určení, zda dva objekty jsou identické (Visual Basic).
V jazyce Visual Basic dva odkazy na proměnné jsou považovány za shodné, pokud jejich ukazatele jsou stejné, to znamená, pokud obě proměnné bodu na stejnou instanci třídy v paměti. Například v aplikaci Windows Forms, můžete chtít provést porovnání Chcete-li určit, zda aktuální instance (`Me`) je stejný jako konkrétní instanci, například `Form2`.  
  
 Visual Basic poskytuje dva operátory k porovnání ukazatele. [Je operátor](../../../../visual-basic/language-reference/operators/is-operator.md) vrátí `True` případě objekty jsou identické a [IsNot – operátor](../../../../visual-basic/language-reference/operators/isnot-operator.md) vrátí `True` Pokud tomu tak není.  
  
## <a name="determining-if-two-objects-are-identical"></a>Určení, zda dva objekty jsou identické  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Chcete-li zjistit, zda dva objekty jsou identické  
  
1.  Nastavení `Boolean` výraz k testování dva objekty.  
  
2.  Do výrazu testování pomocí `Is` operátor s dva objekty jako operandy.  
  
     `Is` Vrátí `True` Pokud objekty bodu na stejnou instanci třídy.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Určení, pokud dva objekty nejsou identické  
 Občas můžete chtít k provedení akce, pokud dva objekty nejsou identické, a může být nevhodných kombinovat `Not` a `Is`, například `If Not obj1 Is obj2`. V takovém případě můžete použít `IsNot` operátor.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Chcete-li zjistit, pokud dva objekty nejsou identické  
  
1.  Nastavení `Boolean` výraz k testování dva objekty.  
  
2.  Do výrazu testování pomocí `IsNot` operátor s dva objekty jako operandy.  
  
     `IsNot` Vrátí `True` Pokud objekty neodkazují na stejnou instanci třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad testy dvojici `Object` proměnné, které chcete zobrazit, pokud se bod na stejnou instanci třídy.  
  
 [!code-vb[VbVbalrKeywords#14](../../../../visual-basic/language-reference/codesnippet/VisualBasic/how-to-determine-whether-two-objects-are-identical_1.vb)]  
  
 V předchozím příkladu zobrazí následující výstup.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Viz také  
 [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)  
 [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)  
 [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)  
 [Operátor Is](../../../../visual-basic/language-reference/operators/is-operator.md)  
 [Operátor IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md)  
 [Postupy: Určení, zda dva objekty spolu souvisí](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)  
 [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
