---
title: "Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami."
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- bc30594
- vbc30594
helpviewer_keywords:
- BC30594
ms.assetid: 5b9fceb4-ab11-41bb-ad3b-6f1a9da8ae7e
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 53372927b88df3946583564492df42170f302739
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="events-of-shared-withevents-variables-cannot-be-handled-by-non-shared-methods"></a>Události sdílené proměnné WithEvents nelze zpracovat nesdílenými metodami.
Proměnná definovaná s `Shared` se modifikátor sdílené proměnné. Sdílené proměnné identifikuje přesně jedno umístění úložiště. Proměnná definovaná s `WithEvents` modifikátor vyhodnotí, že typem, ke kterému patří proměnnou zpracovává sadu událostí vyvolá proměnnou. Když je hodnotu přiřazenou proměnné, vytvořené vlastnost `WithEvents` deklarace unhooks všechny stávající obslužné rutiny události a zachytí si novou obslužnou rutinu události prostřednictvím `Add` metoda.  
  
 **ID chyby:** BC30594  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Deklarovat vaší obslužné rutiny události `Shared`.  
  
## <a name="see-also"></a>Viz také  
 [Sdílené](../../../visual-basic/language-reference/modifiers/shared.md)  
 [WithEvents](../../../visual-basic/language-reference/modifiers/withevents.md)
