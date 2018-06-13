---
title: Implements – klauzule (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.ImplementsClause
helpviewer_keywords:
- interface implementation [Visual Basic], reimplementation
- interface members [Visual Basic], reimplementation
- interface members [Visual Basic], Implements keyword
- interface members
- members [Visual Basic], reimplementation
- interface implementation [Visual Basic], Implements keyword
- interface members [Visual Basic], implementing
- Implements keyword [Visual Basic]
- Implements statement [Visual Basic], about Implements
- members [Visual Basic], implementing
- members [Visual Basic], Implements keyword
- reimplementation
ms.assetid: 5252cdf9-964d-4fc6-af0f-0449b7126b5a
ms.openlocfilehash: 1e34245ac528e9e2463afbfd07dff91bf693830b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603402"
---
# <a name="implements-clause-visual-basic"></a>Implements – klauzule (Visual Basic)
Označuje, že členem třídu nebo strukturu poskytuje implementaci pro člena definované v rozhraní.  
  
## <a name="remarks"></a>Poznámky  
`Implements` – Klíčové slovo není stejný jako [Implements – příkaz](../../../visual-basic/language-reference/statements/implements-statement.md). Můžete použít `Implements` lze zadat třídu nebo strukturu implementuje jedno nebo více rozhraní, a pak použít pro každého člena `Implements` – klíčové slovo k určení, které rozhraní a které člen implementuje.

Pokud třídu nebo strukturu implementuje rozhraní, musí obsahovat `Implements` příkaz ihned po [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md) nebo [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md), a musí implementovat všechny členy definované rozhraní.

## <a name="reimplementation"></a>Opětovná implementace  
V odvozené třídě můžete přeimplementovat člena rozhraní, která základní třídy již implementována. To se liší od přepsání člen základní třídy v těchto ohledech:

- Člen základní třídy nemusí být [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) k být reimplemented.
- Můžete přeimplementovat člena s jiným názvem.

`Implements` – Klíčové slovo lze použít v kontextech následující:
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
