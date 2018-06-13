---
title: Overrides (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- Overrides
- vb.Overrides
helpviewer_keywords:
- properties [Visual Basic], redefining
- procedures [Visual Basic], overriding
- procedures [Visual Basic], redefining
- overriding
- Overrides keyword [Visual Basic]
- overriding, Overrides keyword
- properties [Visual Basic], overriding
ms.assetid: 9f5e6144-ce10-465e-842b-1a8f8760af90
ms.openlocfilehash: 81118b9e97f320bffdbb58e5e1a2859052c4cee5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33602516"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)
Určuje, že vlastnost nebo postup přepisuje stejně jako s názvem vlastnosti nebo postup zděděn ze základní třídy.  
  
## <a name="remarks"></a>Poznámky  
  
## <a name="rules"></a>Pravidla  
  
-   **Kontext deklarace.** Můžete použít `Overrides` jenom v příkazu deklarace vlastnosti nebo postupu.  
  
-   **Kombinovaná parametrů.** Nelze zadat `Overrides` společně s `Shadows` nebo `Shared` ve stejné deklaraci. Element přepsání je implicitně přepisovatelné, a proto nelze kombinovat `Overridable` s `Overrides`.  
  
-   **Odpovídající podpisy.** Podpis tohoto prohlášení, musí přesně shodovat *podpis* vlastnost nebo postup, který přepíše. To znamená, seznamy parametr musí mít stejný počet parametrů, ve stejném pořadí, se stejnými typy data.  
  
     Kromě podpis přepsání deklaraci musí také přesně shodovat následující:  
  
    -   Úroveň přístupu  
  
    -   Návratový typ, pokud existuje  
  
-   **Obecné podpisy.** Obecný postup zahrnuje podpis počet parametrů typu. Přepsání deklaraci proto musí shodovat s verzí základní třídy v tomto ohledu také.  
  
-   **Další odpovídající.** Kromě párování podpis verze základní třídy, toto prohlášení se taky musí shodovat se v těchto ohledech:  
  
    -   Úroveň přístupu – modifikátor (například [veřejné](../../../visual-basic/language-reference/modifiers/public.md))  
  
    -   Předávání mechanismus každý parametr ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))  
  
    -   Omezení jsou uvedeny na každý parametr typu obecné procedury  
  
-   **Stínováním a přepsáním.** Jak stínováním a přepsáním znovu definovat zděděné elementu, ale existují významné rozdíly mezi dva přístupy. Další informace najdete v tématu [stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).  
  
 Pokud používáte `Overrides`, kompilátor implicitně přidá `Overloads` tak, aby vaše knihovna rozhraní API pro práci s C# snadněji.  
  
 `Overrides` Modifikátor lze použít v těchto kontexty:  
  
 [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)  
  
 [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)  
  
 [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)  
 [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)  
 [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)  
 [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)  
 [Stínový provoz v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)  
 [Obecné typy v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)  
 [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
