---
title: Overrides
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
ms.openlocfilehash: 04f1cb27d6a8366c2dd13f8fdc1d975d382f1cfd
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351387"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)

Určuje, že vlastnost nebo procedura Přepisuje identicky pojmenovanou vlastnost nebo proceduru zděděnou ze základní třídy.

## <a name="rules"></a>Pravidla

- **Kontext deklarace** `Overrides` lze použít pouze v příkazu deklarace vlastnosti nebo procedury.

- **Kombinované modifikátory.** V rámci stejné deklarace nelze zadat `Overrides` společně s `Shadows` nebo `Shared`. Vzhledem k tomu, že přepsání elementu je implicitně přepsatelné, nelze kombinovat `Overridable` s `Overrides`.

- **Vyhovující signatury.** Signatura této deklarace musí přesně odpovídat *podpisu* vlastnosti nebo procedury, kterou Přepisuje. To znamená, že seznamy parametrů musí mít stejný počet parametrů ve stejném pořadí se stejnými datovými typy.

  Kromě signatury musí překrytá deklarace také přesně odpovídat následujícímu:

  - Úroveň přístupu

  - Návratový typ, pokud existuje

- **Obecné podpisy** Pro obecný postup signatura obsahuje počet parametrů typu. Proto musí přepsání deklarace odpovídat verzi základní třídy i v tomto ohledu.

- **Další shoda.** Kromě shody signatury verze základní třídy musí tato deklarace také odpovídat těmto kritériím v následujících ohledech:

  - Modifikátor úrovně přístupu (například [Public](../../../visual-basic/language-reference/modifiers/public.md))

  - Předání mechanismu každého parametru ([ByVal](../../../visual-basic/language-reference/modifiers/byval.md) nebo [ByRef](../../../visual-basic/language-reference/modifiers/byref.md))

  - Seznamy omezení pro každý parametr typu Obecné procedury

- **Nastínování a přepisování.** Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy. Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md).

Použijete-li `Overrides`, kompilátor implicitně přidá `Overloads`, aby vaše rozhraní API knihovny fungovala C# snadněji.

V těchto kontextech lze použít modifikátor `Overrides`:

- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)

- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)

- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)

## <a name="see-also"></a>Viz také:

- [MustOverride](../../../visual-basic/language-reference/modifiers/mustoverride.md)
- [NotOverridable](../../../visual-basic/language-reference/modifiers/notoverridable.md)
- [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md)
- [Klíčová slova](../../../visual-basic/language-reference/keywords/index.md)
- [Stínování v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/shadowing.md)
- [Obecné typy v Visual Basic](../../../visual-basic/programming-guide/language-features/data-types/generic-types.md)
- [Seznam typů](../../../visual-basic/language-reference/statements/type-list.md)
