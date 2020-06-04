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
ms.openlocfilehash: de995a13b34678410e2af74b59f2d0c467982b75
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84408481"
---
# <a name="addhandler-statement"></a><span data-ttu-id="d7cc5-102">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="d7cc5-102">AddHandler Statement</span></span>
<span data-ttu-id="d7cc5-103">Přidruží událost k obslužné rutině události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d7cc5-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="d7cc5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="d7cc5-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="d7cc5-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="d7cc5-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="d7cc5-106">event</span><span class="sxs-lookup"><span data-stu-id="d7cc5-106">event</span></span>|<span data-ttu-id="d7cc5-107">Název události, která má být zpracována.</span><span class="sxs-lookup"><span data-stu-id="d7cc5-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="d7cc5-108">Název procedury, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="d7cc5-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="d7cc5-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="d7cc5-109">Remarks</span></span>  
 <span data-ttu-id="d7cc5-110">`AddHandler`Příkazy a `RemoveHandler` umožňují kdykoli spustit a zastavit zpracování událostí během provádění programu.</span><span class="sxs-lookup"><span data-stu-id="d7cc5-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="d7cc5-111">Podpis `eventhandler` procedury se musí shodovat s signaturou události `event` .</span><span class="sxs-lookup"><span data-stu-id="d7cc5-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="d7cc5-112">`Handles`Klíčové slovo a `AddHandler` příkaz umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="d7cc5-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="d7cc5-113">`AddHandler`Příkaz propojuje procedury s událostmi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="d7cc5-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="d7cc5-114">`Handles`Při definování procedury použijte klíčové slovo, které určuje, že zpracuje konkrétní událost.</span><span class="sxs-lookup"><span data-stu-id="d7cc5-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="d7cc5-115">Další informace najdete v tématu [obslužné rutiny](handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="d7cc5-115">For more information, see [Handles](handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d7cc5-116">Pro vlastní události `AddHandler` Vyvolá příkaz přístup k události `AddHandler` .</span><span class="sxs-lookup"><span data-stu-id="d7cc5-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="d7cc5-117">Další informace o vlastních událostech naleznete v tématu [příkaz Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="d7cc5-117">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7cc5-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7cc5-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="d7cc5-119">Viz také</span><span class="sxs-lookup"><span data-stu-id="d7cc5-119">See also</span></span>

- [<span data-ttu-id="d7cc5-120">RemoveHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="d7cc5-120">RemoveHandler Statement</span></span>](removehandler-statement.md)
- [<span data-ttu-id="d7cc5-121">Handles</span><span class="sxs-lookup"><span data-stu-id="d7cc5-121">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="d7cc5-122">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="d7cc5-122">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="d7cc5-123">Události</span><span class="sxs-lookup"><span data-stu-id="d7cc5-123">Events</span></span>](../../programming-guide/language-features/events/index.md)
