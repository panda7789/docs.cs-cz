---
title: Přepsání
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
ms.openlocfilehash: 657f838b2959a5b6a7cef5ff18295a4ada709e9a
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84392025"
---
# <a name="overrides-visual-basic"></a>Overrides (Visual Basic)

Určuje, že vlastnost nebo procedura Přepisuje identicky pojmenovanou vlastnost nebo proceduru zděděnou ze základní třídy.

## <a name="rules"></a>Pravidla

- **Kontext deklarace** Můžete použít `Overrides` pouze v příkazu deklarace vlastnosti nebo procedury.

- **Kombinované modifikátory.** Nelze zadat `Overrides` společně s `Shadows` nebo `Shared` ve stejné deklaraci. Vzhledem k tomu, že přepsání elementu je implicitně přepsatelné, nelze kombinovat `Overridable` s `Overrides` .

- **Vyhovující signatury.** Signatura této deklarace musí přesně odpovídat *podpisu* vlastnosti nebo procedury, kterou Přepisuje. To znamená, že seznamy parametrů musí mít stejný počet parametrů ve stejném pořadí se stejnými datovými typy.

  Kromě signatury musí překrytá deklarace také přesně odpovídat následujícímu:

  - Úroveň přístupu

  - Návratový typ, pokud existuje

- **Obecné podpisy** Pro obecný postup signatura obsahuje počet parametrů typu. Proto musí přepsání deklarace odpovídat verzi základní třídy i v tomto ohledu.

- **Další shoda.** Kromě shody signatury verze základní třídy musí tato deklarace také odpovídat těmto kritériím v následujících ohledech:

  - Modifikátor úrovně přístupu (například [Public](public.md))

  - Předání mechanismu každého parametru ([ByVal](byval.md) nebo [ByRef](byref.md))

  - Seznamy omezení pro každý parametr typu Obecné procedury

- **Nastínování a přepisování.** Jak Stínová, tak i přepsání předefinují zděděný element, ale existují významné rozdíly mezi těmito dvěma přístupy. Další informace najdete v tématu [vytváření stínových kopií v Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md).

Použijete `Overrides` -li, kompilátor implicitně přidá, `Overloads` aby vaše rozhraní API knihovny pracovalo s jazykem C# snadněji.

`Overrides`V těchto kontextech lze použít modifikátor:

- [Function – příkaz](../statements/function-statement.md)

- [Property – příkaz](../statements/property-statement.md)

- [Sub – příkaz](../statements/sub-statement.md)

## <a name="see-also"></a>Viz také

- [MustOverride](mustoverride.md)
- [NotOverridable](notoverridable.md)
- [Overridable](overridable.md)
- [Klíčová slova](../keywords/index.md)
- [Stínění v jazyce Visual Basic](../../programming-guide/language-features/declared-elements/shadowing.md)
- [Obecné typy v Visual Basic](../../programming-guide/language-features/data-types/generic-types.md)
- [Seznam typů](../statements/type-list.md)
