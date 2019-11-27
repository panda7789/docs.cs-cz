---
title: Overridable
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
ms.openlocfilehash: 9c639665fd92a56de6fb6e5147cda873ef457b45
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351390"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
Určuje, že vlastnost nebo procedura může být přepsána identicky pojmenovanou vlastností nebo procedurou v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 Modifikátor `Overridable` umožňuje přepsání vlastnosti nebo metody ve třídě v odvozené třídě. Modifikátor [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md) zabrání v přepsání vlastnosti nebo metody v odvozené třídě.  Další informace najdete v tématu [základy dědičnosti](../../../visual-basic/programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud není zadán modifikátor `Overridable` nebo `NotOverridable`, bude výchozí nastavení záviset na tom, zda vlastnost nebo metoda přepisuje vlastnost nebo metodu základní třídy. Pokud vlastnost nebo metoda přepíše vlastnost nebo metodu základní třídy, výchozí nastavení je `Overridable`; v opačném případě je `NotOverridable`.  
  
 Můžete předefinovat zděděný element stínem nebo přepsáním, ale existují významné rozdíly mezi těmito dvěma přístupy. Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Element, který lze přepsat, je někdy označován jako *virtuální* prvek. Pokud je možné ji přepsat, ale nemusí být, někdy se také označuje jako *konkrétní* prvek.  
  
 `Overridable` lze použít pouze v příkazu deklarace vlastnosti nebo procedury.  
  
## <a name="combined-modifiers"></a>Kombinované modifikátory  
 Pro metodu `Private` nelze zadat `Overridable` ani `NotOverridable`.  
  
 V rámci stejné deklarace nelze zadat `Overridable` společně s `MustOverride`, `NotOverridable`nebo `Shared`.  
  
 Vzhledem k tomu, že přepsání elementu je implicitně přepsatelné, nelze kombinovat `Overridable` s `Overrides`.  
  
## <a name="usage"></a>Využití  
 V těchto kontextech lze použít modifikátor `Overridable`:  
  
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
- [Stínování v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
