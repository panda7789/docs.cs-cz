---
title: AddHandler – příkaz
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: ''
ms.suite: ''
ms.technology:
- devlang-visual-basic
ms.topic: article
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
caps.latest.revision: 15
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: 07fbfe04ccd01b7d0f99338ef2682238830099dc
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="addhandler-statement"></a><span data-ttu-id="4385e-102">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="4385e-102">AddHandler Statement</span></span>
<span data-ttu-id="4385e-103">Přidruží událost obslužné rutiny události za běhu.</span><span class="sxs-lookup"><span data-stu-id="4385e-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4385e-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4385e-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="4385e-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4385e-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="4385e-106">Název události ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="4385e-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="4385e-107">Název procedury, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="4385e-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="4385e-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4385e-108">Remarks</span></span>  
 <span data-ttu-id="4385e-109">`AddHandler` a `RemoveHandler` příkazy umožňují spuštění a zastavení zpracování událostí v průběhu provádění programu.</span><span class="sxs-lookup"><span data-stu-id="4385e-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="4385e-110">Podpis `eventhandler` postupu musí odpovídat podpis události `event`.</span><span class="sxs-lookup"><span data-stu-id="4385e-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="4385e-111">`Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování konkrétní události, ale jsou rozdíly.</span><span class="sxs-lookup"><span data-stu-id="4385e-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="4385e-112">`AddHandler` Příkaz připojí postupy pro události za běhu.</span><span class="sxs-lookup"><span data-stu-id="4385e-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="4385e-113">Použití `Handles` – klíčové slovo při definování postup, chcete-li určit, která byla zjištěna určitá událost.</span><span class="sxs-lookup"><span data-stu-id="4385e-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="4385e-114">Další informace najdete v tématu [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4385e-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4385e-115">Pro vlastní události `AddHandler` příkaz volá události `AddHandler` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="4385e-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="4385e-116">Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4385e-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4385e-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="4385e-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="4385e-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="4385e-118">See Also</span></span>  
 [<span data-ttu-id="4385e-119">RemoveHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="4385e-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="4385e-120">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="4385e-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="4385e-121">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="4385e-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="4385e-122">Události</span><span class="sxs-lookup"><span data-stu-id="4385e-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
