---
title: NotOverridable
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
ms.openlocfilehash: c55d57bb3008b2825fe5382844908ea32f0d500c
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351448"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Určuje, že vlastnost nebo procedura nemůže být přepsána v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 Modifikátor `NotOverridable` zabrání v přepsání vlastnosti nebo metody v odvozené třídě.  Modifikátor [overridable](../../../visual-basic/language-reference/modifiers/overridable.md) umožňuje přepsat vlastnost nebo metodu ve třídě v odvozené třídě. Další informace najdete v tématu [základy dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud není zadán modifikátor `Overridable` nebo `NotOverridable`, bude výchozí nastavení záviset na tom, zda vlastnost nebo metoda přepisuje vlastnost nebo metodu základní třídy. Pokud vlastnost nebo metoda přepíše vlastnost nebo metodu základní třídy, výchozí nastavení je `Overridable`; v opačném případě je `NotOverridable`.  
  
 Element, který nelze přepsat, se někdy označuje jako *zapečetěný* element.  
  
 `NotOverridable` lze použít pouze v příkazu deklarace vlastnosti nebo procedury. `NotOverridable` lze zadat pouze pro vlastnost nebo proceduru, která přepisuje jinou vlastnost nebo proceduru, tedy pouze v kombinaci s `Overrides`.  
  
## <a name="combined-modifiers"></a>Kombinované modifikátory  
 Pro metodu `Private` nelze zadat `Overridable` ani `NotOverridable`.  
  
 V rámci stejné deklarace nelze zadat `NotOverridable` společně s `MustOverride`, `Overridable`nebo `Shared`.  
  
## <a name="usage"></a>Využití  
 V těchto kontextech lze použít modifikátor `NotOverridable`:  
  
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
- [Stínování v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
