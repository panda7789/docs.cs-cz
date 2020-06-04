---
title: Implements – klauzule
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
ms.openlocfilehash: 46ab1a1148e8d73d91293aedfc407e5efdc7cfb4
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404560"
---
# <a name="implements-clause-visual-basic"></a>Implements – klauzule (Visual Basic)
Indikuje, že člen třídy nebo struktury poskytuje implementaci pro člena definovaného v rozhraní.  
  
## <a name="remarks"></a>Poznámky  
`Implements`Klíčové slovo není stejné jako [příkaz Implements](implements-statement.md). Pomocí `Implements` příkazu určíte, že třída nebo struktura implementuje jedno nebo více rozhraní, a poté pro každého člena, který použijete `Implements` klíčové slovo k určení, které rozhraní a který člen implementuje.

Pokud třída nebo struktura implementuje rozhraní, musí obsahovat `Implements` příkaz ihned po příkazu [třídy](class-statement.md) nebo [příkazu struktury](structure-statement.md)a musí implementovat všechny členy definované rozhraním.

## <a name="reimplementation"></a>Implementaci  
V odvozené třídě můžete znovu implementovat člena rozhraní, který je základní třídou již implementován. To se liší od přepsání člena základní třídy v následujících ohledech:

- Člen základní třídy není nutné [přepsat](../modifiers/overridable.md) , aby jej bylo možné znovu implementovat.
- Člena můžete znovu implementovat s jiným názvem.

`Implements`Klíčové slovo lze použít v následujících kontextech:

- [Event – příkaz](event-statement.md)
- [Function – příkaz](function-statement.md)
- [Property – příkaz](property-statement.md)
- [Sub – příkaz](sub-statement.md)  
  
## <a name="see-also"></a>Viz také

- [Implements – Příkaz](implements-statement.md)
- [Interface – příkaz](interface-statement.md)
- [Class – příkaz](class-statement.md)
- [Structure – příkaz](structure-statement.md)
