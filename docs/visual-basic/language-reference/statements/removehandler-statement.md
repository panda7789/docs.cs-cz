---
title: "RemoveHandler – příkaz"
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 82d130c6536df7d72977a028333293b4e0ee89de
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="removehandler-statement"></a><span data-ttu-id="29976-102">RemoveHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="29976-102">RemoveHandler Statement</span></span>
<span data-ttu-id="29976-103">Odebere přidružení mezi událost a obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="29976-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="29976-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="29976-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="29976-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="29976-105">Parts</span></span>  
  
|<span data-ttu-id="29976-106">Termín</span><span class="sxs-lookup"><span data-stu-id="29976-106">Term</span></span>|<span data-ttu-id="29976-107">Definice</span><span class="sxs-lookup"><span data-stu-id="29976-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="29976-108">Název události ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="29976-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="29976-109">Název procesu, který aktuálně zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="29976-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="29976-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="29976-110">Remarks</span></span>  
 <span data-ttu-id="29976-111">`AddHandler` a `RemoveHandler` příkazy umožňují spuštění a zastavení zpracování událostí pro určitou událost kdykoli během spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="29976-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="29976-112">Pro vlastní události `RemoveHandler` příkaz volá události `RemoveHandler` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="29976-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="29976-113">Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="29976-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="29976-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="29976-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="29976-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="29976-115">See Also</span></span>  
 [<span data-ttu-id="29976-116">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="29976-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="29976-117">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="29976-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="29976-118">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="29976-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="29976-119">Události</span><span class="sxs-lookup"><span data-stu-id="29976-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
