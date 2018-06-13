---
title: AddHandler – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: db8131dc82aed40e725c9375efef274fb6917d41
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33603649"
---
# <a name="addhandler-statement"></a><span data-ttu-id="d5f54-102">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="d5f54-102">AddHandler Statement</span></span>
<span data-ttu-id="d5f54-103">Přidruží událost obslužné rutiny události za běhu.</span><span class="sxs-lookup"><span data-stu-id="d5f54-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d5f54-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d5f54-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="d5f54-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d5f54-105">Parts</span></span>  
 `event`  
 <span data-ttu-id="d5f54-106">Název události ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="d5f54-106">The name of the event to handle.</span></span>  
  
 `eventhandler`  
 <span data-ttu-id="d5f54-107">Název procedury, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="d5f54-107">The name of a procedure that handles the event.</span></span>  
  
## <a name="remarks"></a><span data-ttu-id="d5f54-108">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d5f54-108">Remarks</span></span>  
 <span data-ttu-id="d5f54-109">`AddHandler` a `RemoveHandler` příkazy umožňují spuštění a zastavení zpracování událostí v průběhu provádění programu.</span><span class="sxs-lookup"><span data-stu-id="d5f54-109">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="d5f54-110">Podpis `eventhandler` postupu musí odpovídat podpis události `event`.</span><span class="sxs-lookup"><span data-stu-id="d5f54-110">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="d5f54-111">`Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování konkrétní události, ale jsou rozdíly.</span><span class="sxs-lookup"><span data-stu-id="d5f54-111">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="d5f54-112">`AddHandler` Příkaz připojí postupy pro události za běhu.</span><span class="sxs-lookup"><span data-stu-id="d5f54-112">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="d5f54-113">Použití `Handles` – klíčové slovo při definování postup, chcete-li určit, která byla zjištěna určitá událost.</span><span class="sxs-lookup"><span data-stu-id="d5f54-113">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="d5f54-114">Další informace najdete v tématu [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d5f54-114">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d5f54-115">Pro vlastní události `AddHandler` příkaz volá události `AddHandler` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="d5f54-115">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="d5f54-116">Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d5f54-116">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d5f54-117">Příklad</span><span class="sxs-lookup"><span data-stu-id="d5f54-117">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/addhandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="d5f54-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="d5f54-118">See Also</span></span>  
 [<span data-ttu-id="d5f54-119">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="d5f54-119">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)  
 [<span data-ttu-id="d5f54-120">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="d5f54-120">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="d5f54-121">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="d5f54-121">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="d5f54-122">Události</span><span class="sxs-lookup"><span data-stu-id="d5f54-122">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
