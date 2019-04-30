---
title: Odvozené třídy nemohou vyvolat události třídy Base.
ms.date: 07/20/2015
f1_keywords:
- vbc30029
- bc30029
helpviewer_keywords:
- BC30029
ms.assetid: 63afa1c6-2f93-4512-a2f0-372455979771
ms.openlocfilehash: 0e9acf4b3e71295655c15ae9b1c80852c9aca8df
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61803568"
---
# <a name="derived-classes-cannot-raise-base-class-events"></a>Odvozené třídy nemohou vyvolat události třídy Base.
Událost může být vyvolána pouze z místa deklarace ve kterém je deklarována. Proto třídy nemohou vyvolat události z jakékoli jiné třídy, dokonce i jeden, ze kterého je odvozen.  
  
 **ID chyby:** BC30029  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
- Přesunout `Event` příkazu nebo `RaiseEvent` příkaz tak, aby byly ve stejné třídě.  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz RaiseEvent](../../../visual-basic/language-reference/statements/raiseevent-statement.md)
