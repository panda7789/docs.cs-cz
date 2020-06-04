---
title: MustOverride
ms.date: 07/20/2015
f1_keywords:
- vb.MustOverride
- MustOverride
helpviewer_keywords:
- virtual elements [Visual Basic], pure
- elements [Visual Basic], pure virtual
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- overriding, MustOverride keyword
- procedures [Visual Basic], redefining
- pure virtual elements [Visual Basic]
- MustOverride keyword [Visual Basic]
- properties [Visual Basic], overriding
ms.assetid: 6e9d9ad6-bb64-433f-b32b-3ef84293bf96
ms.openlocfilehash: 1b20108a2d42e82c0af7598fde8d60a08fea28ec
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84396191"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Určuje, že vlastnost nebo procedura není v této třídě implementována a musí být přepsána v odvozené třídě předtím, než je možné ji použít.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `MustOverride` pouze v příkazu deklarace vlastnosti nebo procedury. Vlastnost nebo procedura, která určuje, `MustOverride` musí být členem třídy a třída musí být označena jako [MustInherit](mustinherit.md).  
  
## <a name="rules"></a>Pravidla  
  
- **Neúplná deklarace** Pokud zadáte `MustOverride` , nezadáte žádné další řádky kódu pro vlastnost nebo proceduru, nikoli `End Function` `End Property` příkaz, nebo `End Sub` .  
  
- **Kombinované modifikátory.** Nelze zadat `MustOverride` společně s `NotOverridable` , `Overridable` nebo `Shared` ve stejné deklaraci.  
  
- **Nastínování a přepisování.** Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy. Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).  
  
- **Alternativní výrazy.** Element, který nelze použít s výjimkou v přepsání, se někdy označuje jako *čistě virtuální* prvek.  
  
 `MustOverride`V těchto kontextech lze použít modifikátor:  
  
 [Function – příkaz](../statements/function-statement.md)  
  
 [Property – příkaz](../statements/property-statement.md)  
  
 [Sub – příkaz](../statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Přepsání](overrides.md)
- [MustInherit](mustinherit.md)
- [Klíčová slova](../keywords/index.md)
- [Stínění v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
