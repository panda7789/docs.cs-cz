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
ms.openlocfilehash: f2ddef64ca02ca7c96c6c906f5ee79e3cf99dece
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64604065"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="619f3-102">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="619f3-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="619f3-103">Toto téma obsahuje seznam běžných problémů, které vznikají u obslužných rutin událostí v zděděné součásti.</span><span class="sxs-lookup"><span data-stu-id="619f3-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="619f3-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="619f3-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="619f3-105">Spustí kód v obslužné rutině události dvakrát za každé volání</span><span class="sxs-lookup"><span data-stu-id="619f3-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="619f3-106">Nesmí obsahovat obslužnou rutinu zděděné události [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="619f3-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="619f3-107">Metodu v základní třídě je již přidruženo k události a odpovídajícím způsobem se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="619f3-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="619f3-108">Odeberte `Handles` klauzule z zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="619f3-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="619f3-109">Pokud nemá žádné zděděné metody `Handles` – klíčové slovo, ověřte, že váš kód neobsahuje speciální [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nebo jakékoli další metody, které zpracovávají stejné události.</span><span class="sxs-lookup"><span data-stu-id="619f3-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="619f3-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="619f3-110">See also</span></span>

- [<span data-ttu-id="619f3-111">Události</span><span class="sxs-lookup"><span data-stu-id="619f3-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
