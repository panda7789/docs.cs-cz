---
title: Chráněné Friend (Visual Basic)
ms.date: 05/10/2018
helpviewer_keywords:
- Protected Friend keyword [Visual Basic]
- Protected Friend keyword [Visual Basic], syntax
ms.openlocfilehash: b72cbee0394043620e792d1c014bfe55121e175e
ms.sourcegitcommit: 22c3c8f74eaa138dbbbb02eb7d720fce87fc30a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/18/2018
ms.locfileid: "34306554"
---
# <a name="protected-friend-visual-basic"></a>Chráněné Friend (Visual Basic)

`Protected Friend` – Kombinace klíčových slov je modifikátor přístupu členů. Se uděluje obě [Friend](friend.md) přístup a [chráněné](protected.md) přístup na deklarované elementy, které jsou přístupné z libovolné místo ve stejném sestavení, ze své vlastní třídy a z odvozené třídy. Můžete zadat `Protected Friend` pouze u členů tříd; nelze použít `Protected Friend` u členů struktury protože struktury nemůže být zděděno.

> [!NOTE]
> V sadě Visual Studio, výběr F1 – Nápověda na `protected friend` poskytuje nápovědu pro buď [chráněné](protected.md) nebo [friend](friend.md). Prostředí IDE vybere jeden token pod kurzor spíše než složené aplikace word.

## <a name="rules"></a>Pravidla

- **Kontext deklarace.** Můžete použít `Protected Friend` pouze na úrovni třídy. To znamená kontext deklarace `Protected` element musí být třída a nesmí být zdrojový soubor, obor názvů, rozhraní, modul, struktura nebo postup. 


## <a name="see-also"></a>Viz také

[Public](../../../visual-basic/language-reference/modifiers/public.md)  
[Protected](../../../visual-basic/language-reference/modifiers/protected.md)  
[Friend](friend.md)   
[Private](../../../visual-basic/language-reference/modifiers/private.md)  
[Privátní chráněný](./private-protected.md)   
[Úrovně přístupu v jazyce Visual Basic](../../../visual-basic/programming-guide/language-features/declared-elements/access-levels.md)  
[Procedury](../../../visual-basic/programming-guide/language-features/procedures/index.md)  
[Struktury](../../../visual-basic/programming-guide/language-features/data-types/structures.md)  
[Objekty a třídy](../../../visual-basic/programming-guide/language-features/objects-and-classes/index.md)
