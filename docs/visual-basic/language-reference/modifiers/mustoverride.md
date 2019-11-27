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
ms.openlocfilehash: dc6a153a604fd0e5cee9d7d46ebcd63294f33628
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351481"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Určuje, že vlastnost nebo procedura není v této třídě implementována a musí být přepsána v odvozené třídě předtím, než je možné ji použít.  
  
## <a name="remarks"></a>Poznámky  
 `MustOverride` lze použít pouze v příkazu deklarace vlastnosti nebo procedury. Vlastnost nebo procedura určující `MustOverride` musí být členem třídy a třída musí být označena jako [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Pravidla  
  
- **Neúplná deklarace** Pokud zadáte `MustOverride`, neposkytnete žádné další řádky kódu pro vlastnost nebo proceduru, ani příkaz `End Function`, `End Property`nebo `End Sub`.  
  
- **Kombinované modifikátory.** V rámci stejné deklarace nelze zadat `MustOverride` společně s `NotOverridable`, `Overridable`nebo `Shared`.  
  
- **Nastínování a přepisování.** Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy. Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
- **Alternativní výrazy.** Element, který nelze použít s výjimkou v přepsání, se někdy označuje jako *čistě virtuální* prvek.  
  
 V těchto kontextech lze použít modifikátor `MustOverride`:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Stínování v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
