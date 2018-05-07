---
title: Overridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overridable
- vb.Overridable
helpviewer_keywords:
- elements [Visual Basic], concrete
- properties [Visual Basic], redefining
- overriding, Overridable keyword
- elements [Visual Basic], virtual
- virtual [elements VB]
- procedures [Visual Basic], overriding
- concrete [elements VB]
- procedures [Visual Basic], redefining
- Overridable keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 612581e7-8a4c-4a5d-beff-3402fffa6f35
ms.openlocfilehash: 4844bf7f3ecf23335715b950a96be15e54ebc601
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
Určuje, že vlastnost nebo postupu může být přepsáno stejně jako s názvem vlastnosti nebo postup v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 `Overridable` Modifikátor umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě. [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifikátor brání vlastnosti nebo metody přepsání v odvozené třídě.  Další informace najdete v tématu [základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud `Overridable` nebo `NotOverridable` modifikátor nezadáte, výchozí nastavení závisí na tom, jestli jsou vlastnost nebo metoda přepsání základní třída vlastnosti nebo metody. Pokud jsou vlastnost nebo metoda přepsání základní třída vlastnosti nebo metody, výchozí nastavení je `Overridable`, jinak je `NotOverridable`.  
  
 Můžete stínové nebo přepsat znovu definovat zděděné elementu, ale existují významné rozdíly mezi dva přístupy. Další informace najdete v tématu [stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Element, který je možné přepsat se někdy označuje jako *virtuální* elementu. Pokud je možné přepsat, ale nemusí být, se někdy se také označuje jako *konkrétní* elementu.  
  
 Můžete použít `Overridable` jenom v příkazu deklarace vlastnosti nebo postupu.  
  
## <a name="combined-modifiers"></a>Kombinovaná modifikátory  
 Nelze zadat `Overridable` nebo `NotOverridable` pro `Private` metoda.  
  
 Nelze zadat `Overridable` společně s `MustOverride`, `NotOverridable`, nebo `Shared` ve stejné deklaraci.  
  
 Element přepsání je implicitně přepisovatelné, a proto nelze kombinovat `Overridable` s `Overrides`.  
  
## <a name="usage"></a>Použití  
 `Overridable` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Modifikátory](../../../visual-basic/language-reference/modifiers/index.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
