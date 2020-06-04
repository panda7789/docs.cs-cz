---
title: RemoveHandler – příkaz
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 3514a79f2430b148e6a3727b83029b4e207a677b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84404249"
---
# <a name="removehandler-statement"></a><span data-ttu-id="7f2b7-102">RemoveHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="7f2b7-102">RemoveHandler Statement</span></span>
<span data-ttu-id="7f2b7-103">Odebere přidružení mezi událostí a obslužnou rutinou události.</span><span class="sxs-lookup"><span data-stu-id="7f2b7-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="7f2b7-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="7f2b7-104">Syntax</span></span>  
  
```vb  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="7f2b7-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="7f2b7-105">Parts</span></span>  
  
|<span data-ttu-id="7f2b7-106">Pojem</span><span class="sxs-lookup"><span data-stu-id="7f2b7-106">Term</span></span>|<span data-ttu-id="7f2b7-107">Definice</span><span class="sxs-lookup"><span data-stu-id="7f2b7-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="7f2b7-108">Název zpracovávané události.</span><span class="sxs-lookup"><span data-stu-id="7f2b7-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="7f2b7-109">Název procedury, která tuto událost právě zpracovává.</span><span class="sxs-lookup"><span data-stu-id="7f2b7-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="7f2b7-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="7f2b7-110">Remarks</span></span>  
 <span data-ttu-id="7f2b7-111">`AddHandler`Příkazy a `RemoveHandler` umožňují kdykoli během provádění programu spouštět a zastavovat zpracování událostí pro konkrétní událost.</span><span class="sxs-lookup"><span data-stu-id="7f2b7-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="7f2b7-112">Pro vlastní události `RemoveHandler` Vyvolá příkaz přístup k události `RemoveHandler` .</span><span class="sxs-lookup"><span data-stu-id="7f2b7-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="7f2b7-113">Další informace o vlastních událostech naleznete v tématu [příkaz Event](event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="7f2b7-113">For more information on custom events, see [Event Statement](event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7f2b7-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="7f2b7-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="7f2b7-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="7f2b7-115">See also</span></span>

- [<span data-ttu-id="7f2b7-116">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="7f2b7-116">AddHandler Statement</span></span>](addhandler-statement.md)
- [<span data-ttu-id="7f2b7-117">Handles</span><span class="sxs-lookup"><span data-stu-id="7f2b7-117">Handles</span></span>](handles-clause.md)
- [<span data-ttu-id="7f2b7-118">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="7f2b7-118">Event Statement</span></span>](event-statement.md)
- [<span data-ttu-id="7f2b7-119">Události</span><span class="sxs-lookup"><span data-stu-id="7f2b7-119">Events</span></span>](../../programming-guide/language-features/events/index.md)
