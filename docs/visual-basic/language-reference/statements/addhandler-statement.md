---
title: AddHandler – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.AddHandlerMethod
- addhandler
- vb.addhandler
helpviewer_keywords:
- AddHandler statement [Visual Basic]
ms.assetid: cfe69799-2a0f-42c0-a99e-09fed954da01
ms.openlocfilehash: a9913cd682e52562422ba140e27187d37c592684
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69928941"
---
# <a name="addhandler-statement"></a><span data-ttu-id="4bcf4-102">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="4bcf4-102">AddHandler Statement</span></span>
<span data-ttu-id="4bcf4-103">Přidruží událost k obslužné rutině události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="4bcf4-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="4bcf4-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="4bcf4-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="4bcf4-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="4bcf4-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="4bcf4-106">event</span><span class="sxs-lookup"><span data-stu-id="4bcf4-106">event</span></span>|<span data-ttu-id="4bcf4-107">Název události, která má být zpracována.</span><span class="sxs-lookup"><span data-stu-id="4bcf4-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="4bcf4-108">Název procedury, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="4bcf4-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="4bcf4-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="4bcf4-109">Remarks</span></span>  
 <span data-ttu-id="4bcf4-110">Příkazy `AddHandler` a`RemoveHandler` umožňují kdykoli spustit a zastavit zpracování událostí během provádění programu.</span><span class="sxs-lookup"><span data-stu-id="4bcf4-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="4bcf4-111">Podpis `eventhandler` procedury se musí shodovat s signaturou události `event`.</span><span class="sxs-lookup"><span data-stu-id="4bcf4-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="4bcf4-112">`Handles` Klíčové slovo `AddHandler` a příkaz umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="4bcf4-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="4bcf4-113">`AddHandler` Příkaz propojuje procedury s událostmi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="4bcf4-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="4bcf4-114">Při definování procedury použijte klíčovéslovo,kteréurčuje,žezpracujekonkrétníudálost.`Handles`</span><span class="sxs-lookup"><span data-stu-id="4bcf4-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="4bcf4-115">Další informace najdete v tématu [obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf4-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4bcf4-116">Pro vlastní události `AddHandler` Vyvolá příkaz `AddHandler` přístup k události.</span><span class="sxs-lookup"><span data-stu-id="4bcf4-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="4bcf4-117">Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="4bcf4-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="4bcf4-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="4bcf4-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="4bcf4-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4bcf4-119">See also</span></span>

- [<span data-ttu-id="4bcf4-120">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="4bcf4-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="4bcf4-121">Řeší</span><span class="sxs-lookup"><span data-stu-id="4bcf4-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="4bcf4-122">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="4bcf4-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="4bcf4-123">Události</span><span class="sxs-lookup"><span data-stu-id="4bcf4-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
