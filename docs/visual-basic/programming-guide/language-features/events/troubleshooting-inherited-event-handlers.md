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
ms.openlocfilehash: 704ca667a6d14ade7be0192e872f5e40791cb864
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62053805"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="a0833-102">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="a0833-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="a0833-103">Toto téma obsahuje seznam běžných problémů, které vznikají u obslužných rutin událostí v zděděné součásti.</span><span class="sxs-lookup"><span data-stu-id="a0833-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="a0833-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="a0833-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="a0833-105">Spustí kód v obslužné rutině události dvakrát za každé volání</span><span class="sxs-lookup"><span data-stu-id="a0833-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="a0833-106">Nesmí obsahovat obslužnou rutinu zděděné události [zpracovává](../../../../visual-basic/language-reference/statements/handles-clause.md) klauzuli.</span><span class="sxs-lookup"><span data-stu-id="a0833-106">An inherited event handler must not include a [Handles](../../../../visual-basic/language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="a0833-107">Metodu v základní třídě je již přidruženo k události a odpovídajícím způsobem se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="a0833-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="a0833-108">Odeberte `Handles` klauzule z zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="a0833-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="a0833-109">Pokud nemá žádné zděděné metody `Handles` – klíčové slovo, ověřte, že váš kód neobsahuje speciální [AddHandler – příkaz](../../../../visual-basic/language-reference/statements/addhandler-statement.md) nebo jakékoli další metody, které zpracovávají stejné události.</span><span class="sxs-lookup"><span data-stu-id="a0833-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../../visual-basic/language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a0833-110">Viz také:</span><span class="sxs-lookup"><span data-stu-id="a0833-110">See also</span></span>

- [<span data-ttu-id="a0833-111">Události</span><span class="sxs-lookup"><span data-stu-id="a0833-111">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
