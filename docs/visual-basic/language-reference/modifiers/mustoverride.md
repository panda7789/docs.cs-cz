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
ms.openlocfilehash: 0ddd7d0d2a57afc02aa7483ba5e83b65c48af534
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58822814"
---
# <a name="mustoverride-visual-basic"></a>MustOverride (Visual Basic)
Určuje, že se vlastnost nebo procedura není implementovaná v této třídě a předtím, než je možné, musí se přepsat v odvozené třídě.  
  
## <a name="remarks"></a>Poznámky  
 Můžete použít `MustOverride` pouze v příkazu deklarace vlastnost nebo procedura. Vlastnost nebo proceduru, která určuje `MustOverride` musíte být členem třídy, a musí být třída označena [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md).  
  
## <a name="rules"></a>pravidla  
  
-   **Neúplné deklarace.** Pokud zadáte `MustOverride`, nezadáte nejsou žádné další řádky kódu pro vlastnost nebo procedura, dokonce i pomocí `End Function`, `End Property`, nebo `End Sub` příkazu.  
  
-   **Kombinované modifikátory.** Nelze zadat `MustOverride` spolu s `NotOverridable`, `Overridable`, nebo `Shared` ve stejné deklaraci.  
  
-   **Stínováním a přepsáním.** Jak stínováním a přepsáním znovu definovat element zděděné, ale existují významné rozdíly mezi dvěma přístupy. Další informace najdete v tématu [stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
-   **Alternativní podmínky.** Někdy se označuje jako element, který nelze použít s výjimkou v přepsání *čistě virtuální* elementu.  
  
 `MustOverride` Modifikátor lze použít v těchto kontextech:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Overrides](../../../visual-basic/language-reference/modifiers/overrides.md)
- [MustInherit](../../../visual-basic/language-reference/modifiers/mustinherit.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Stínění v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
