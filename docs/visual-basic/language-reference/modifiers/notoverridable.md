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
ms.openlocfilehash: 41c08a48fdb7501081e887fb5cf9f99c334c72ac
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58822312"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Určuje, že vlastnost nebo procedura nedá přepsat v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 `NotOverridable` Modifikátor zabraňuje vlastnosti nebo metody přepsání v odvozené třídě.  [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) modifikátor umožňuje vlastnosti nebo metody ve třídě k přepsání v odvozené třídě. Další informace najdete v tématu [základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud `Overridable` nebo `NotOverridable` modifikátor není zadán, výchozí nastavení závisí na tom, zda vlastnosti nebo metody přepíše vlastnost základní třídy nebo metody. Pokud vlastnost nebo metoda přepíše vlastnost základní třídy nebo metody, ve výchozím nastavení je `Overridable`; v opačném případě je `NotOverridable`.  
  
 Někdy se označuje jako element, který nelze přepsat *zapečetěné* elementu.  
  
 Můžete použít `NotOverridable` pouze v příkazu deklarace vlastnost nebo procedura. Můžete zadat `NotOverridable` pouze na vlastnost nebo procedura, která přepíše jiné vlastnost nebo procedura, tedy pouze v kombinaci s `Overrides`.  
  
## <a name="combined-modifiers"></a>Kombinované modifikátory  
 Nelze zadat `Overridable` nebo `NotOverridable` pro `Private` metoda.  
  
 Nelze zadat `NotOverridable` spolu s `MustOverride`, `Overridable`, nebo `Shared` ve stejné deklaraci.  
  
## <a name="usage"></a>Použití  
 `NotOverridable` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Modifikátory](../../../visual-basic/language-reference/modifiers/index.md)
- [Základní informace o dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
