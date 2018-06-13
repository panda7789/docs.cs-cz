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
ms.locfileid: "33646304"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="8e035-102">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="8e035-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="8e035-103">V tomto tématu jsou uvedeny běžné problémy, které nastat u obslužné rutiny událostí v zděděné součásti.</span><span class="sxs-lookup"><span data-stu-id="8e035-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="8e035-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="8e035-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="8e035-105">Spustí kód v obslužné rutiny události dvakrát pro každé volání</span><span class="sxs-lookup"><span data-stu-id="8e035-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="8e035-106">Obslužné rutiny události zděděné nesmí obsahovat [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzule.</span><span class="sxs-lookup"><span data-stu-id="8e035-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="8e035-107">Metoda v základní třídě je již přidruženo k události a bude odpovídajícím způsobem platit.</span><span class="sxs-lookup"><span data-stu-id="8e035-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="8e035-108">Odeberte `Handles` klauzule z zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="8e035-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="8e035-109">Není-li metodu zděděné `Handles` – klíčové slovo, ověřte, zda kód neobsahuje další [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nebo jakékoli další metody, které zpracovávají stejnou událost.</span><span class="sxs-lookup"><span data-stu-id="8e035-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="8e035-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="8e035-110">See Also</span></span>  
 [<span data-ttu-id="8e035-111">Události</span><span class="sxs-lookup"><span data-stu-id="8e035-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
