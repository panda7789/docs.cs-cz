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
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="98ae7-102">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="98ae7-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="98ae7-103">V tomto tématu jsou uvedeny běžné problémy, které nastat u obslužné rutiny událostí v zděděné součásti.</span><span class="sxs-lookup"><span data-stu-id="98ae7-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="98ae7-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="98ae7-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="98ae7-105">Spustí kód v obslužné rutiny události dvakrát pro každé volání</span><span class="sxs-lookup"><span data-stu-id="98ae7-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="98ae7-106">Obslužné rutiny události zděděné nesmí obsahovat [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="98ae7-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="98ae7-107">Metoda v základní třídě je již přidruženo k události a bude odpovídajícím způsobem platit.</span><span class="sxs-lookup"><span data-stu-id="98ae7-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="98ae7-108">Odeberte `Handles` klauzule z zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="98ae7-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="98ae7-109">Není-li metodu zděděné `Handles` – klíčové slovo, ověřte, zda kód neobsahuje další [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nebo jakékoli další metody, které zpracovávají stejnou událost.</span><span class="sxs-lookup"><span data-stu-id="98ae7-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="98ae7-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="98ae7-110">See Also</span></span>  
 [<span data-ttu-id="98ae7-111">Události</span><span class="sxs-lookup"><span data-stu-id="98ae7-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
