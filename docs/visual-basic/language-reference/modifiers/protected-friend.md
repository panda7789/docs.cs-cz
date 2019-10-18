---
title: Chráněný přítel (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: d3592feaece1d5ce85ee6e2657d8a2715c4097a3
ms.sourcegitcommit: 4f4a32a5c16a75724920fa9627c59985c41e173c
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/17/2019
ms.locfileid: "72524771"
---
# <a name="protected-friend-visual-basic"></a>Chráněný přítel (Visual Basic)

Kombinací klíčového slova `Protected Friend` je modifikátor přístupu ke členu. Uděluje přístup [příteli](friend.md) i [chráněným](protected.md) přístupům k deklarovaným prvkům, takže jsou přístupné odkudkoli ve stejném sestavení, z vlastní třídy a z odvozených tříd. Můžete zadat `Protected Friend` pouze pro členy třídy; `Protected Friend` nelze použít u členů struktury, protože struktury nelze dědit.

> [!NOTE]
> V aplikaci Visual Studio vyberte nápovědu F1 v `protected friend` poskytne nápovědu pro buď [chráněný](protected.md) , nebo [Friend](friend.md). Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.

## <a name="rules"></a>Pravidly

**Kontext deklarace** @No__t_0 lze použít pouze na úrovni třídy. To znamená, že kontext deklarace pro prvek `Protected` musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.

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
