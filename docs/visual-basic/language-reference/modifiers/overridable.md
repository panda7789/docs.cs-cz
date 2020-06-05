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
ms.openlocfilehash: dcbabde8464dd8a0ce5fad24d7d72b1e780270d3
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392116"
---
# <a name="overridable-visual-basic"></a>Overridable (Visual Basic)
Určuje, že vlastnost nebo procedura může být přepsána identicky pojmenovanou vlastností nebo procedurou v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 `Overridable`Modifikátor umožňuje přepsat vlastnost nebo metodu ve třídě v odvozené třídě. Modifikátor [NotOverridable](notoverridable.md) zabrání v přepsání vlastnosti nebo metody v odvozené třídě.  Další informace najdete v tématu [základy dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud není `Overridable` `NotOverridable` zadán modifikátor nebo, výchozí nastavení závisí na tom, zda vlastnost nebo metoda přepisuje vlastnost nebo metodu základní třídy. Pokud vlastnost nebo metoda přepíše vlastnost nebo metodu základní třídy, výchozí nastavení je `Overridable` . v opačném případě je `NotOverridable` .  
  
 Můžete předefinovat zděděný element stínem nebo přepsáním, ale existují významné rozdíly mezi těmito dvěma přístupy. Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).  
  
 Element, který lze přepsat, je někdy označován jako *virtuální* prvek. Pokud je možné ji přepsat, ale nemusí být, někdy se také označuje jako *konkrétní* prvek.  
  
 Můžete použít `Overridable` pouze v příkazu deklarace vlastnosti nebo procedury.  
  
## <a name="combined-modifiers"></a>Kombinované modifikátory  
 Nemůžete zadat `Overridable` ani `NotOverridable` pro `Private` metodu.  
  
 Nelze zadat `Overridable` společně s `MustOverride` , `NotOverridable` nebo `Shared` ve stejné deklaraci.  
  
 Vzhledem k tomu, že přepsání elementu je implicitně přepsatelné, nelze kombinovat `Overridable` s `Overrides` .  
  
## <a name="usage"></a>Využití  
 `Overridable`V těchto kontextech lze použít modifikátor:  
  
 [Function – příkaz](../statements/function-statement.md)  
  
 [Property – příkaz](../statements/property-statement.md)  
  
 [Sub – příkaz](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Modifikátory](index.md)
- [Základní informace o dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Přepsání](overrides.md)
- [Klíčová slova](../keywords/index.md)
- [Stínění v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
