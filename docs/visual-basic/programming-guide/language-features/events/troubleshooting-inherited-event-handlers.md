---
title: Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: f6355cf7fc2e43651c1112d048220a8179968c76
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
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
