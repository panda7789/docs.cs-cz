---
title: NotOverridable (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.NotOverridable
- NotOverridable
helpviewer_keywords:
- sealed methods [Visual Basic]
- NotOverridable keyword [Visual Basic]
- properties [Visual Basic], redefining
- elements [Visual Basic], sealed
- sealed [elements VB]
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- methods [Visual Basic], sealed
- properties [Visual Basic], overriding
ms.assetid: 66ec6984-f5f5-4857-b362-6a3907aaf9e0
ms.openlocfilehash: 3fae1a4b587c379dbc459cbc973982851e713785
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33600750"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Určuje, že vlastnost nebo procedury nelze přepsat v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 `NotOverridable` Modifikátor brání vlastnosti nebo metody přepsání v odvozené třídě.  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifikátor umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě. Další informace najdete v tématu [základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud `Overridable` nebo `NotOverridable` modifikátor nezadáte, výchozí nastavení závisí na tom, jestli jsou vlastnost nebo metoda přepsání základní třída vlastnosti nebo metody. Pokud jsou vlastnost nebo metoda přepsání základní třída vlastnosti nebo metody, výchozí nastavení je `Overridable`, jinak je `NotOverridable`.  
  
 Element, který nebylo možné přepsat se někdy nazývá *zapečetěné* elementu.  
  
 Můžete použít `NotOverridable` jenom v příkazu deklarace vlastnosti nebo postupu. Můžete zadat `NotOverridable` pouze na vlastnosti nebo postup, který přepíše jinou vlastnost nebo postup, který je pouze v kombinaci s `Overrides`.  
  
## <a name="combined-modifiers"></a>Kombinovaná modifikátory  
 Nelze zadat `Overridable` nebo `NotOverridable` pro `Private` metoda.  
  
 Nelze zadat `NotOverridable` společně s `MustOverride`, `Overridable`, nebo `Shared` ve stejné deklaraci.  
  
## <a name="usage"></a>Použití  
 `NotOverridable` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Modifikátory](../../../visual-basic/language-reference/modifiers/index.md)  
 [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
