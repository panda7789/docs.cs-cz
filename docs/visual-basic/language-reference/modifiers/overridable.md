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
ms.openlocfilehash: 7002589b303c41b26b611588f339fa70dd19f959
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54537592"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
Určuje, že se vlastnost nebo procedura lze přepsat identicky pojmenovanou vlastnost nebo procedura v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 `Overridable` Modifikátor umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě. [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) modifikátor zabraňuje vlastnosti nebo metody přepsání v odvozené třídě.  Další informace najdete v tématu [základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud `Overridable` nebo `NotOverridable` modifikátor není zadán, výchozí nastavení závisí na tom, zda vlastnosti nebo metody přepíše vlastnost základní třídy nebo metody. Pokud vlastnost nebo metoda přepíše vlastnost základní třídy nebo metody, ve výchozím nastavení je `Overridable`; v opačném případě je `NotOverridable`.  
  
 Můžete stínové nebo přepsání nastavení za účelem znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy. Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Element, který se dá přepsat se někdy označuje jako *virtuální* elementu. Pokud se dá přepsat, ale nemusí být, někdy nazývá se také *konkrétní* elementu.  
  
 Můžete použít `Overridable` pouze v příkazu deklarace vlastnost nebo procedura.  
  
## <a name="combined-modifiers"></a>Kombinované modifikátory  
 Nelze zadat `Overridable` nebo `NotOverridable` pro `Private` metoda.  
  
 Nelze zadat `Overridable` spolu s `MustOverride`, `NotOverridable`, nebo `Shared` ve stejné deklaraci.  
  
 Vzhledem k tomu, že element přepsání přepsatelné, nelze kombinovat `Overridable` s `Overrides`.  
  
## <a name="usage"></a>Použití  
 `Overridable` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:
- [Modifikátory](../../../visual-basic/language-reference/modifiers/index.md)
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
