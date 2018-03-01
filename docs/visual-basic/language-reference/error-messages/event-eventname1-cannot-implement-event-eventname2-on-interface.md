---
title: "Událost & č. 39; &lt;eventname1&gt;& č. 39; nelze implementovat, události & č. 39;&lt; eventname2&gt;& č. 39; na rozhraní & č. 39;&lt; rozhraní&gt;& č. 39; protože jejich typy delegáta & č. 39;&lt; delegate1&gt;& č. 39; a & č. 39;&lt; delegate2&gt;& č. 39; neshodují"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: b0fcbbf8a6e23270e4dcbf9d813c773e1522a92a
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Událost & č. 39; &lt;eventname1&gt;& č. 39; nelze implementovat, události & č. 39;&lt; eventname2&gt;& č. 39; na rozhraní & č. 39;&lt; rozhraní&gt;& č. 39; protože jejich typy delegáta & č. 39;&lt; delegate1&gt;& č. 39; a & č. 39;&lt; delegate2&gt;& č. 39; neshodují
[!INCLUDE[vbprvb](~/includes/vbprvb-md.md)]událost nelze implementovat, protože typ delegáta události neodpovídá typu delegáta události v rozhraní. Této chybě může dojít, když definovat více událostí v rozhraní a pak pokus o jejich implementaci společně s stejnou událost. Událost můžete implementovat dvě nebo více událostí pouze v případě, že všechny implementována události jsou deklarováno s použitím `As` syntaxe a specifikují stejný typ delegáta.  
  
 **ID chyby:** BC31423  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Implementujte události samostatně.  
  
     —nebo—  
  
-   Definování události v rozhraní pomocí `As` syntaxe a specifikují stejný typ delegáta.  
  
## <a name="see-also"></a>Viz také  
 [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Delegate – příkaz](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
