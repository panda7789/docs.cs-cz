---
title: Protected Friend
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: f92021f5f0dab9762470c270bdd5182187d587e5
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74351312"
---
# <a name="protected-friend-visual-basic"></a>Chráněný přítel (Visual Basic)

Kombinací klíčového slova `Protected Friend` je modifikátor přístupu ke členu. Uděluje přístup [příteli](friend.md) i [chráněným](protected.md) přístupům k deklarovaným prvkům, takže jsou přístupné odkudkoli ve stejném sestavení, z vlastní třídy a z odvozených tříd. Můžete zadat `Protected Friend` pouze pro členy třídy; `Protected Friend` nelze použít u členů struktury, protože struktury nelze dědit.

> [!NOTE]
> V aplikaci Visual Studio vyberte nápovědu F1 v `protected friend` poskytne nápovědu pro buď [chráněný](protected.md) , nebo [Friend](friend.md). Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.

## <a name="rules"></a>Pravidla

**Kontext deklarace** `Protected Friend` lze použít pouze na úrovni třídy. To znamená, že kontext deklarace pro prvek `Protected` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.

## <a name="see-also"></a>Viz také:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Úrovně přístupu v Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
