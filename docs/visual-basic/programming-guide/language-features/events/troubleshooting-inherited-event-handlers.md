---
title: "Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: e0e8f0b669566bbee6530931bfba9808fad0c085
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a>Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic
V tomto tématu jsou uvedeny běžné problémy, které nastat u obslužné rutiny událostí v zděděné součásti.  
  
## <a name="procedures"></a>Procedury  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a>Spustí kód v obslužné rutiny události dvakrát pro každé volání  
  
-   Obslužné rutiny události zděděné nesmí obsahovat [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzule. Metoda v základní třídě je již přidruženo k události a bude odpovídajícím způsobem platit. Odeberte `Handles` klauzule z zděděné metody.  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   Není-li metodu zděděné `Handles` – klíčové slovo, ověřte, zda kód neobsahuje další [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nebo jakékoli další metody, které zpracovávají stejnou událost.  
  
## <a name="see-also"></a>Viz také  
 [Události](../../../../visual-basic/programming-guide/language-features/events/index.md)
