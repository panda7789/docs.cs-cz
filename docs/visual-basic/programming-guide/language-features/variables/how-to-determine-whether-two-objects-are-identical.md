---
title: 'Postupy: Určení, zda dva objekty jsou identické.'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 5deebd4ffc5b277c94f5ae36c00fd6e5010a1551
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74348600"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Postupy: Určení, zda dva objekty jsou identické (Visual Basic).
V Visual Basic jsou dva odkazy na proměnné považovány za identické, pokud jsou ukazatele stejné, to znamená, pokud obě proměnné odkazují na stejnou instanci třídy v paměti. Například v aplikaci model Windows Forms můžete chtít porovnat, abyste zjistili, zda je aktuální instance (`Me`) stejná jako konkrétní instance, jako je například `Form2`.  
  
 Visual Basic poskytuje dva operátory pro porovnání ukazatelů. [Operátor is](../../../../visual-basic/language-reference/operators/is-operator.md) vrátí `True`, pokud jsou objekty identické a [operátor IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md) vrátí `True`, pokud nejsou.  
  
## <a name="determining-if-two-objects-are-identical"></a>Určení, zda jsou dva objekty identické  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Určení, zda jsou dva objekty identické  
  
1. Nastavte výraz `Boolean` pro otestování těchto dvou objektů.  
  
2. Ve výrazu testování použijte operátor `Is` se dvěma objekty jako operandy.  
  
     `Is` vrátí `True`, pokud objekty odkazují na stejnou instanci třídy.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Určení, zda dva objekty nejsou identické  
 Někdy je vhodné provést akci, pokud tyto dva objekty nejsou identické a může být nevhodné kombinovat `Not` a `Is`, například `If Not obj1 Is obj2`. V takovém případě můžete použít operátor `IsNot`.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Určení, zda dva objekty nejsou identické  
  
1. Nastavte výraz `Boolean` pro otestování těchto dvou objektů.  
  
2. Ve výrazu testování použijte operátor `IsNot` se dvěma objekty jako operandy.  
  
     `IsNot` vrátí `True`, pokud objekty neodkazují na stejnou instanci třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad testuje páry `Object` proměnných, aby bylo možné zjistit, zda odkazují na stejnou instanci třídy.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 V předchozím příkladu se zobrazí následující výstup.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Viz také:

- [Datový typ Object](../../../../visual-basic/language-reference/data-types/object-data-type.md)
- [Objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variables.md)
- [Hodnoty objektové proměnné](../../../../visual-basic/programming-guide/language-features/variables/object-variable-values.md)
- [Operátor Is](../../../../visual-basic/language-reference/operators/is-operator.md)
- [Operátor IsNot](../../../../visual-basic/language-reference/operators/isnot-operator.md)
- [Postupy: Určení, zda dva objekty spolu souvisí](../../../../visual-basic/programming-guide/language-features/variables/how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase a MyClass](../../../../visual-basic/programming-guide/program-structure/me-my-mybase-and-myclass.md)
