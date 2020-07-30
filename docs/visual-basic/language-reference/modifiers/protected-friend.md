---
title: Protected Friend
ms.date: 05/10/2018
f1_keywords:
- vb.ProtectedFriend
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 27fc993ca0b94d406261d5e6275de8cd619eb6a8
ms.sourcegitcommit: 6f58a5f75ceeb936f8ee5b786e9adb81a9a3bee9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/28/2020
ms.locfileid: "87303449"
---
# <a name="protected-friend-visual-basic"></a>Chráněný přítel (Visual Basic)

`Protected Friend`Kombinace klíčového slova je modifikátor přístupu ke členu. Uděluje přístup [příteli](friend.md) i [chráněným](protected.md) přístupům k deklarovaným prvkům, takže jsou přístupné odkudkoli ve stejném sestavení, z vlastní třídy a z odvozených tříd. Můžete zadat `Protected Friend` pouze členy tříd. nemůžete použít `Protected Friend` pro členy struktury, protože struktury nelze dědit.

> [!NOTE]
> V aplikaci Visual Studio vyberte nápovědu F1, která `protected friend` poskytuje nápovědu pro buď [chráněný](protected.md) , nebo [Friend](friend.md). Rozhraní IDE vybere jeden token pod kurzorem namísto složeného slova.

## <a name="rules"></a>Pravidla

**Kontext deklarace** Můžete použít `Protected Friend` pouze na úrovni třídy. To znamená, že kontext deklarace pro `Protected` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.

## <a name="see-also"></a>Viz také:

- [Republik](public.md)
- [Proti](protected.md)
- [Friend](friend.md)
- [Soukromá](private.md)
- [Soukromé chráněné](./private-protected.md)
- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
