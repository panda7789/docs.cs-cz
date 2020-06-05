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
ms.openlocfilehash: 463dd2454aafebf11554fb7bacdb73724c3130d8
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392155"
---
# <a name="notoverridable-visual-basic"></a>NotOverridable (Visual Basic)
Určuje, že vlastnost nebo procedura nemůže být přepsána v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 `NotOverridable`Modifikátor zabraňuje přepsání vlastnosti nebo metody v odvozené třídě.  Modifikátor [overridable](overridable.md) umožňuje přepsat vlastnost nebo metodu ve třídě v odvozené třídě. Další informace najdete v tématu [základy dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md).  
  
 Pokud není `Overridable` `NotOverridable` zadán modifikátor nebo, výchozí nastavení závisí na tom, zda vlastnost nebo metoda přepisuje vlastnost nebo metodu základní třídy. Pokud vlastnost nebo metoda přepíše vlastnost nebo metodu základní třídy, výchozí nastavení je `Overridable` . v opačném případě je `NotOverridable` .  
  
 Element, který nelze přepsat, se někdy označuje jako *zapečetěný* element.  
  
 Můžete použít `NotOverridable` pouze v příkazu deklarace vlastnosti nebo procedury. Můžete zadat `NotOverridable` pouze vlastnost nebo proceduru, která přepisuje jinou vlastnost nebo proceduru, tedy pouze v kombinaci s `Overrides` .  
  
## <a name="combined-modifiers"></a>Kombinované modifikátory  
 Nemůžete zadat `Overridable` ani `NotOverridable` pro `Private` metodu.  
  
 Nelze zadat `NotOverridable` společně s `MustOverride` , `Overridable` nebo `Shared` ve stejné deklaraci.  
  
## <a name="usage"></a>Využití  
 `NotOverridable`V těchto kontextech lze použít modifikátor:  
  
 [Function – příkaz](../statements/function-statement.md)  
  
 [Property – příkaz](../statements/property-statement.md)  
  
 [Sub – příkaz](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Modifikátory](index.md)
- [Základní informace o dědičnosti](../../programming-guide/language-features/objects-and-classes/inheritance-basics.md)
- [MustOverride](mustoverride.md)
- [Overridable](overridable.md)
- [Přepsání](overrides.md)
- [Klíčová slova](../keywords/index.md)
- [Stínění v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
