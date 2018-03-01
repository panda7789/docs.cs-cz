---
title: "Implements – klauzule (Visual Basic)"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
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
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 73f66eda29e37fda15b4c838da5a0458684131da
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
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
- [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)
- [Function – příkaz](../../../visual-basic/language-reference/statements/function-statement.md)
- [Property – příkaz](../../../visual-basic/language-reference/statements/property-statement.md)
- [Sub – příkaz](../../../visual-basic/language-reference/statements/sub-statement.md)  
  
## <a name="see-also"></a>Viz také  
 [Implements – příkaz](../../../visual-basic/language-reference/statements/implements-statement.md)  
 [Interface – příkaz](../../../visual-basic/language-reference/statements/interface-statement.md)  
 [Class – příkaz](../../../visual-basic/language-reference/statements/class-statement.md)  
 [Structure – příkaz](../../../visual-basic/language-reference/statements/structure-statement.md)
