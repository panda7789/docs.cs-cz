---
title: Chráněné Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: 1858411e5543448e6d822c97b6e5c18da4a6c11e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54639598"
---
# <a name="protected-friend-visual-basic"></a>Chráněné Friend (Visual Basic)

`Protected Friend` – Kombinace klíčových slov je modifikátor přístupu členu. To uděluje obě [Friend](friend.md) přístup a [chráněné](protected.md) přístup na deklarované elementy, takže jsou přístupné odkudkoli ve stejném sestavení, ze své vlastní třídy a z odvozených tříd. Můžete zadat `Protected Friend` pouze pro členy třídy; nelze použít `Protected Friend` na členy struktury protože struktury nelze dědit.

> [!NOTE]
> V sadě Visual Studio, že vyberete nápovědy klávesy F1 na `protected friend` poskytuje nápovědu pro buď [chráněné](protected.md) nebo [friend](friend.md). Rozhraní IDE zvolí jeden token pod kurzor spíše než složené slovo.

## <a name="rules"></a>pravidla

- **Místní deklarace.** Můžete použít `Protected Friend` pouze na úrovni třídy. To znamená, že deklarace kontext `Protected` elementu musí být třída a nemůže být zdrojový soubor, obor názvů, rozhraní, modul, struktury nebo proceduru. 


## <a name="see-also"></a>Viz také:

- [Public](../../../visual-basic/language-reference/modifiers/public.md)
- [Protected](../../../visual-basic/language-reference/modifiers/protected.md)
- [Friend](friend.md)
- [Private](../../../visual-basic/language-reference/modifiers/private.md)
- [Private Protected](./private-protected.md)
- [Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)
- [Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)
- [Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)
- [Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
