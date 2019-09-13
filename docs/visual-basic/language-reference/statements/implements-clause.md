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
ms.openlocfilehash: dcd20f21a989c327dcfcf27d5638d500b6e4b6da
ms.sourcegitcommit: 33c8d6f7342a4bb2c577842b7f075b0e20a2fa40
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2019
ms.locfileid: "70929321"
---
# <a name="implements-clause-visual-basic"></a>Implements – klauzule (Visual Basic)
Indikuje, že člen třídy nebo struktury poskytuje implementaci pro člena definovaného v rozhraní.  
  
## <a name="remarks"></a>Poznámky  
Klíčové slovo není stejné jako [příkaz Implements.](../../../visual-basic/language-reference/statements/implements-statement.md) `Implements` Pomocí `Implements` příkazu určíte, že třída nebo struktura implementuje jedno nebo více rozhraní, a poté pro každého člena, který `Implements` použijete klíčové slovo k určení, které rozhraní a který člen implementuje.

Pokud třída nebo struktura implementuje rozhraní, musí obsahovat `Implements` příkaz ihned po příkazu [třídy](../../../visual-basic/language-reference/statements/class-statement.md) nebo [příkazu struktury](../../../visual-basic/language-reference/statements/structure-statement.md)a musí implementovat všechny členy definované rozhraním.

## <a name="reimplementation"></a>Implementaci  
V odvozené třídě můžete znovu implementovat člena rozhraní, který je základní třídou již implementován. To se liší od přepsání člena základní třídy v následujících ohledech:

- Člen základní třídy není nutné [přepsat](../../../visual-basic/language-reference/modifiers/overridable.md) , aby jej bylo možné znovu implementovat.
- Člena můžete znovu implementovat s jiným názvem.

`Implements` Klíčové slovo lze použít v následujících kontextech:

- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
