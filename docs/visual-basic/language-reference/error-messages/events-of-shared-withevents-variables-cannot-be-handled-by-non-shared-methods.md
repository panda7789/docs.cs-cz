---
title: Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
ms.date: 07/20/2015
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
ms.openlocfilehash: f61f4cd17b1bb3088117e0a0d91b186fd40db3b2
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33585168"
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
Proměnná definovaná s `Shared` se modifikátor sdílené proměnné. Sdílené proměnné identifikuje přesně jedno umístění úložiště. Proměnná definovaná s `WithEvents` modifikátor vyhodnotí, že typem, ke kterému patří proměnnou zpracovává sadu událostí vyvolá proměnnou. Když je hodnotu přiřazenou proměnné, vytvořené vlastnost `WithEvents` deklarace unhooks všechny stávající obslužné rutiny události a zachytí si novou obslužnou rutinu události prostřednictvím `Add` metoda.  
  
 **ID chyby:** BC30594  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Deklarovat vaší obslužné rutiny události `Shared`.  
  
## <a name="see-also"></a>Viz také  
 [Shared](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
