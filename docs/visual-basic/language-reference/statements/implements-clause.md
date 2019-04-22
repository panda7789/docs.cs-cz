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
ms.openlocfilehash: 05de1d9f8966c17d84deba34f27819cce4aff3fe
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "58832616"
---
# <a name="implements-clause-visual-basic"></a>Implements – klauzule (Visual Basic)
Označuje, že člen třídy nebo struktury poskytuje implementaci pro člena definovaného v rozhraní.  
  
## <a name="remarks"></a>Poznámky  
`Implements` – Klíčové slovo není stejný jako [příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md). Můžete použít `Implements` příkaz určíte, že třída nebo struktura, jeden nebo více rozhraní implementuje, a pak použít pro každého člena `Implements` – klíčové slovo k určení, které rozhraní a který člen implementuje.

Pokud třída nebo struktura implementuje rozhraní, musí zahrnovat `Implements` příkaz ihned po [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md) nebo [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md), a musí implementovat všechny členy definované rozhraní.

## <a name="reimplementation"></a>Patřící třídě  
V odvozené třídě můžete znovu implementovat člen rozhraní, která je již implementováno základní třídy. Tím se liší od přepsání člena základní třídy v těchto ohledech:

- Členu základní třídy nemusí být [Overridable](../../../visual-basic/language-reference/modifiers/overridable.md) chcete být reimplemented.
- Můžete znovu implementovat člena s jiným názvem.

`Implements` – Klíčové slovo lze použít v následujících kontextů:
- [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)
- [Příkaz Function](../../../visual-basic/language-reference/statements/function-statement.md)
- [Příkaz Property](../../../visual-basic/language-reference/statements/property-statement.md)
- [Příkaz Sub](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také:

- [Příkaz Implements](../../../visual-basic/language-reference/statements/implements-statement.md)
- [Příkaz Interface](../../../visual-basic/language-reference/statements/interface-statement.md)
- [Příkaz Class](../../../visual-basic/language-reference/statements/class-statement.md)
- [Příkaz Structure](../../../visual-basic/language-reference/statements/structure-statement.md)
