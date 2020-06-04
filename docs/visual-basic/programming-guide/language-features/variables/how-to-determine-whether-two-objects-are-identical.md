---
title: 'Postupy: Určení, zda dva objekty jsou identické.'
ms.date: 07/20/2015
helpviewer_keywords:
- testing [Visual Basic], objects
- objects [Visual Basic], comparing
- object variables [Visual Basic], determining identity
ms.assetid: 7829f817-0d1f-4749-a707-de0b95e0cf5c
ms.openlocfilehash: 67c3af8b7bdac3ad1c7e4908f1ac2684df7a87aa
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84410474"
---
# <a name="how-to-determine-whether-two-objects-are-identical-visual-basic"></a>Postupy: Určení, zda dva objekty jsou identické (Visual Basic).
V Visual Basic jsou dva odkazy na proměnné považovány za identické, pokud jsou ukazatele stejné, to znamená, pokud obě proměnné odkazují na stejnou instanci třídy v paměti. Například v aplikaci model Windows Forms můžete chtít porovnat, aby bylo možné určit, zda aktuální instance ( `Me` ) je stejná jako konkrétní instance, například `Form2` .  
  
 Visual Basic poskytuje dva operátory pro porovnání ukazatelů. [Operátor is](../../../language-reference/operators/is-operator.md) vrátí `True` , pokud jsou objekty shodné, a [operátor IsNot](../../../language-reference/operators/isnot-operator.md) vrátí, `True` Pokud nejsou.  
  
## <a name="determining-if-two-objects-are-identical"></a>Určení, zda jsou dva objekty identické  
  
#### <a name="to-determine-if-two-objects-are-identical"></a>Určení, zda jsou dva objekty identické  
  
1. Nastavte `Boolean` výraz pro otestování těchto dvou objektů.  
  
2. Ve výrazu testování použijte `Is` operátor se dvěma objekty jako operandy.  
  
     `Is`Vrátí `True` , zda objekty odkazují na stejnou instanci třídy.  
  
## <a name="determining-if-two-objects-are-not-identical"></a>Určení, zda dva objekty nejsou identické  
 V některých případech je třeba provést akci, pokud tyto dva objekty nejsou totožné a může být nevhodným způsobem kombinovat `Not` a například `Is` `If Not obj1 Is obj2` . V takovém případě můžete použít `IsNot` operátor.  
  
#### <a name="to-determine-if-two-objects-are-not-identical"></a>Určení, zda dva objekty nejsou identické  
  
1. Nastavte `Boolean` výraz pro otestování těchto dvou objektů.  
  
2. Ve výrazu testování použijte `IsNot` operátor se dvěma objekty jako operandy.  
  
     `IsNot`Vrátí, `True` zda objekty neodkazují na stejnou instanci třídy.  
  
## <a name="example"></a>Příklad  
 Následující příklad testuje páry proměnných, `Object` aby bylo možné zjistit, zda odkazují na stejnou instanci třídy.  
  
 [!code-vb[VbVbalrKeywords#14](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrKeywords/VB/class7.vb#14)]  
  
 V předchozím příkladu se zobrazí následující výstup.  
  
 `objA different from objB? True`  
  
 `objA identical to objC? True`  
  
## <a name="see-also"></a>Viz také

- [Datový typ objektu](../../../language-reference/data-types/object-data-type.md)
- [Proměnné objektu](object-variables.md)
- [Hodnoty proměnné objektu](object-variable-values.md)
- [Is – operátor](../../../language-reference/operators/is-operator.md)
- [IsNot – operátor](../../../language-reference/operators/isnot-operator.md)
- [Postupy: Určení, zda dva objekty souvisejí.](how-to-determine-whether-two-objects-are-related.md)
- [Me, My, MyBase a MyClass](../../program-structure/me-my-mybase-and-myclass.md)
