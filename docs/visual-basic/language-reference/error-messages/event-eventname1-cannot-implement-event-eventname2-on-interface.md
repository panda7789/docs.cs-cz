---
title: Událost &#39; &lt;eventname1&gt; &#39; nemůže implementovat událost &#39; &lt;eventname2&gt; &#39; na rozhraní &#39; &lt;rozhraní&gt; &#39; protože jejich typy delegáta &#39; &lt;delegate1&gt; &#39; a &#39; &lt;delegate2&gt; &#39; neodpovídají
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
caps.latest.revision: 6
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 41f5984458eb17db04f20b292a0d80783093dcb4
ms.sourcegitcommit: 86adcc06e35390f13c1e372c36d2e044f1fc31ef
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/26/2018
---
# <a name="event-39lteventname1gt39-cannot-implement-event-39lteventname2gt39-on-interface-39ltinterfacegt39-because-their-delegate-types-39ltdelegate1gt39-and-39ltdelegate2gt39-do-not-match"></a>Událost &#39; &lt;eventname1&gt; &#39; nemůže implementovat událost &#39; &lt;eventname2&gt; &#39; na rozhraní &#39; &lt;rozhraní&gt; &#39; protože jejich typy delegáta &#39; &lt;delegate1&gt; &#39; a &#39; &lt;delegate2&gt; &#39; neodpovídají
Visual Basic nelze implementovat událost, protože typ delegáta události neodpovídá typu delegáta události v rozhraní. Této chybě může dojít, když definovat více událostí v rozhraní a pak pokus o jejich implementaci společně s stejnou událost. Událost můžete implementovat dvě nebo více událostí pouze v případě, že všechny implementována události jsou deklarováno s použitím `As` syntaxe a specifikují stejný typ delegáta.  
  
 **ID chyby:** BC31423  
  
## <a name="to-correct-this-error"></a>Oprava této chyby  
  
-   Implementujte události samostatně.  
  
     —nebo—  
  
-   Definování události v rozhraní pomocí `As` syntaxe a specifikují stejný typ delegáta.  
  
## <a name="see-also"></a>Viz také  
 [Příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md)  
 [Příkaz Delegate](../../../visual-basic/language-reference/statements/delegate-statement.md)  
 [Události](../../../visual-basic/programming-guide/language-features/events/index.md)
