---
title: MustOverride (Visual Basic)
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
ms.openlocfilehash: 5dabd90d29bc41d017436876af24a67fa87e8e17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Určuje, že vlastnost nebo postup není implementována v této třídě a musí být přepsána nastaveními v odvozené třídě před použitím.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `MustOverride` jenom v příkazu deklarace vlastnosti nebo postupu. Vlastnost nebo procedury, která určuje `MustOverride` musí být členem třídy, a musí být označen třída [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>Pravidla  
  
-   **Nedokončené deklarace.** Pokud zadáte `MustOverride`, nezadáte není žádné další řádky kódu pro vlastnost nebo postupu, i na `End Function`, `End Property`, nebo `End Sub` příkaz.  
  
-   **Kombinovaná parametrů.** Nelze zadat `MustOverride` společně s `NotOverridable`, `Overridable`, nebo `Shared` ve stejné deklaraci.  
  
-   **Stínováním a přepsáním.** Jak stínováním a přepsáním znovu definovat zděděné elementu, ale existují významné rozdíly mezi dva přístupy. Další informace najdete v tématu [stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Alternativní podmínky.** Element, který nelze použít s výjimkou v přepsání se někdy nazývá *čistý virtuální* elementu.  
  
 `MustOverride` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)  
 [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
