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
ms.openlocfilehash: f114aee75356e59eafd9d3ba6af9c64402cb374f
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345875"
---
# <a name="implements-clause-visual-basic"></a>Implements – klauzule (Visual Basic)
Indikuje, že člen třídy nebo struktury poskytuje implementaci pro člena definovaného v rozhraní.  
  
## <a name="remarks"></a>Poznámky  
Klíčové slovo `Implements` není stejné jako [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md). Pomocí příkazu `Implements` určíte, že třída nebo struktura implementuje jedno nebo více rozhraní, a poté pro každého člena, který použijete klíčové slovo `Implements` k určení, které rozhraní a který člen implementuje.

Pokud třída nebo struktura implementuje rozhraní, musí obsahovat příkaz `Implements` ihned po [příkazu třídy](../../../visual-basic/language-reference/statements/class-statement.md) nebo [příkazu struktury](../../../visual-basic/language-reference/statements/structure-statement.md)a musí implementovat všechny členy definované rozhraním.

## <a name="reimplementation"></a>Implementaci  
V odvozené třídě můžete znovu implementovat člena rozhraní, který je základní třídou již implementován. To se liší od přepsání člena základní třídy v následujících ohledech:

- Člen základní třídy není nutné [přepsat](../../../visual-basic/language-reference/modifiers/overridable.md) , aby jej bylo možné znovu implementovat.
- Člena můžete znovu implementovat s jiným názvem.

Klíčové slovo `Implements` lze použít v následujících kontextech:

- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
