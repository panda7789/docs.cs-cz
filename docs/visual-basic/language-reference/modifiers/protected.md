---
title: Chráněno
ms.date: 07/20/2015
f1_keywords:
- vb.Protected
helpviewer_keywords:
- Protected Friend keyword combination
- Protected keyword [Visual Basic], and Friend
- Protected keyword [Visual Basic], syntax
- Protected access modifier
- Protected keyword [Visual Basic]
ms.assetid: 74ad3d56-309f-49d2-b60c-1d0157d010e8
ms.openlocfilehash: d66ed68004f8b6ef21ae703f02b317589814764b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84398217"
---
# <a name="protected-visual-basic"></a>Protected (Visual Basic)

Modifikátor přístupu ke členu, který určuje, že nejmíň jeden deklarovaný programový prvek je přístupný jenom v rámci své vlastní třídy nebo z odvozené třídy.

## <a name="remarks"></a>Poznámky

V některých případech programovací element deklarovaný ve třídě obsahuje citlivá data nebo omezený kód a vy chcete omezit přístup k elementu. Nicméně, pokud je třída děděna a očekáváte hierarchii odvozených tříd, může být nutné, aby tyto odvozené třídy měly přístup k datům nebo kódu. V takovém případě chcete, aby byl prvek přístupný jak ze základní třídy, tak ze všech odvozených tříd. Chcete-li omezit přístup k prvku tímto způsobem, můžete jej deklarovat pomocí `Protected` .

> [!NOTE]
> `Protected`Modifikátor přístupu lze kombinovat se dvěma dalšími modifikátory:
>
> - [Chráněný modifikátor Friend](protected-friend.md) zpřístupňuje člena třídy v rámci této třídy, z odvozených tříd a ze stejného sestavení, ve kterém je třída definovaná.
> - Modifikátor [Private protecter](private-protected.md) zpřístupňuje člena třídy, který je přístupný odvozeným typům, ale pouze v rámci jeho nadřazeného sestavení.

## <a name="rules"></a>Pravidla

**Kontext deklarace** Můžete použít `Protected` pouze na úrovni třídy. To znamená, že kontext deklarace pro `Protected` prvek musí být třída a nemůže se jednat o zdrojový soubor, obor názvů, rozhraní, modul, strukturu nebo proceduru.

## <a name="behavior"></a>Chování

- **Úroveň přístupu.** Veškerý kód ve třídě má přístup k jeho prvkům. Kód v jakékoli třídě, která je odvozena od základní třídy, má přístup ke všem `Protected` prvkům základní třídy. To platí pro všechny generace odvození. To znamená, že třída může přistupovat k `Protected` prvkům základní třídy základní třídy a tak dále.

     Protected Access není nadmnožinou ani podmnožinou přístupu typu Friend.

- **Modifikátory přístupu.** Klíčová slova, která určují úroveň přístupu, se nazývají *modifikátory přístupu*. Porovnání modifikátorů přístupu najdete [v tématu úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md).

`Protected`V těchto kontextech lze použít modifikátor:

- [Class – příkaz](../statements/class-statement.md)

- [Const – příkaz](../statements/const-statement.md)

- [Declare – příkaz](../statements/declare-statement.md)

- [Delegate – příkaz](../statements/delegate-statement.md)

- [Dim – příkaz](../statements/dim-statement.md)

- [Enum – příkaz](../statements/enum-statement.md)

- [Event – příkaz](../statements/event-statement.md)

- [Function – příkaz](../statements/function-statement.md)

- [Interface – příkaz](../statements/interface-statement.md)

- [Property – příkaz](../statements/property-statement.md)

- [Structure – příkaz](../statements/structure-statement.md)

- [Sub – příkaz](../statements/sub-statement.md)

## <a name="see-also"></a>Viz také

- [Republik](public.md)
- [Friend](friend.md)
- [Hlášen](private.md)
- [Soukromé chráněné](private-protected.md)
- [Protected Friend](protected-friend.md)
- [Úrovně přístupu v Visual Basic](../../programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../programming-guide/language-features/procedures/index.md)
- [Struktury](../../programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../programming-guide/language-features/objects-and-classes/index.md)
