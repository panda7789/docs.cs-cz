---
title: Řešení potíží s obslužnými rutinami zděděných událostí
ms.date: 07/20/2015
helpviewer_keywords:
- troubleshooting events [Visual Basic]
- inherited events [Visual Basic]
- troubleshooting Visual Basic, event handlers
- event handling, troubleshooting
- event handlers, troubleshooting
ms.assetid: e1c8759f-5370-4308-8476-8c48b73509bf
ms.openlocfilehash: 4e7bedd1de5197fcf8b69091f4cc878f41b01cd5
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405103"
---
# <a name="troubleshooting-inherited-event-handlers-in-visual-basic"></a><span data-ttu-id="bb1f7-102">Řešení potíží s obslužnými rutinami zděděných událostí v jazyce Visual Basic</span><span class="sxs-lookup"><span data-stu-id="bb1f7-102">Troubleshooting Inherited Event Handlers in Visual Basic</span></span>
<span data-ttu-id="bb1f7-103">V tomto tématu jsou uvedeny běžné problémy, které vznikají pomocí obslužných rutin událostí ve zděděných součástech.</span><span class="sxs-lookup"><span data-stu-id="bb1f7-103">This topic lists common issues that arise with event handlers in inherited components.</span></span>  
  
## <a name="procedures"></a><span data-ttu-id="bb1f7-104">Procedury</span><span class="sxs-lookup"><span data-stu-id="bb1f7-104">Procedures</span></span>  
  
#### <a name="code-in-event-handler-executes-twice-for-every-call"></a><span data-ttu-id="bb1f7-105">Kód v obslužné rutině události se spustí dvakrát pro každé volání.</span><span class="sxs-lookup"><span data-stu-id="bb1f7-105">Code in Event Handler Executes Twice for Every Call</span></span>  
  
- <span data-ttu-id="bb1f7-106">Zděděná obslužná rutina události nesmí obsahovat klauzuli [Handles](../../../language-reference/statements/handles-clause.md) .</span><span class="sxs-lookup"><span data-stu-id="bb1f7-106">An inherited event handler must not include a [Handles](../../../language-reference/statements/handles-clause.md) clause.</span></span> <span data-ttu-id="bb1f7-107">Metoda v základní třídě je již k události přidružena a bude ji následně zavolávat.</span><span class="sxs-lookup"><span data-stu-id="bb1f7-107">The method in the base class is already associated with the event and will fire accordingly.</span></span> <span data-ttu-id="bb1f7-108">Odeberte `Handles` klauzuli z zděděné metody.</span><span class="sxs-lookup"><span data-stu-id="bb1f7-108">Remove the `Handles` clause from the inherited method.</span></span>  
  
     [!code-vb[VbVbalrEvents#32](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#32)]  
  
- <span data-ttu-id="bb1f7-109">Pokud zděděná metoda neobsahuje `Handles` klíčové slovo, ověřte, že váš kód neobsahuje další [příkaz AddHandler](../../../language-reference/statements/addhandler-statement.md) , ani žádné další metody, které zpracovávají stejnou událost.</span><span class="sxs-lookup"><span data-stu-id="bb1f7-109">If the inherited method does not have a `Handles` keyword, verify that your code does not contain an extra [AddHandler Statement](../../../language-reference/statements/addhandler-statement.md) or any additional methods that handle the same event.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bb1f7-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="bb1f7-110">See also</span></span>

- [<span data-ttu-id="bb1f7-111">Události</span><span class="sxs-lookup"><span data-stu-id="bb1f7-111">Events</span></span>](index.md)
