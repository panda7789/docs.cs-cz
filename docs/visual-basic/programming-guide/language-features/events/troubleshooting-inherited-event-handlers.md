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
ms.openlocfilehash: e7c56757d18a22a65b4ef8e81d2a05e5f4f4dffc
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54680194"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="aa7db-102">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="aa7db-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="aa7db-103">Toto téma obsahuje seznam běžných problémů, které vznikají u obslužných rutin událostí v zděděné součásti.</span><span class="sxs-lookup"><span data-stu-id="aa7db-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="aa7db-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="aa7db-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="aa7db-105">Spustí kód v obslužné rutině události dvakrát za každé volání</span><span class="sxs-lookup"><span data-stu-id="aa7db-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
-   <span data-ttu-id="aa7db-106">Nesmí obsahovat obslužnou rutinu zděděné události [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="aa7db-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="aa7db-107">Metodu v základní třídě je již přidruženo k události a odpovídajícím způsobem se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="aa7db-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="aa7db-108">Odeberte `Handles` klauzule z zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="aa7db-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/troubleshooting-inherited-event-handlers_1.vb)]  
  
-   <span data-ttu-id="aa7db-109">Pokud nemá žádné zděděné metody `Handles` – klíčové slovo, ověřte, že váš kód neobsahuje speciální [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nebo jakékoli další metody, které zpracovávají stejné události.</span><span class="sxs-lookup"><span data-stu-id="aa7db-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="aa7db-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="aa7db-110">See also</span></span>
- [<span data-ttu-id="aa7db-111">Události</span><span class="sxs-lookup"><span data-stu-id="aa7db-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
