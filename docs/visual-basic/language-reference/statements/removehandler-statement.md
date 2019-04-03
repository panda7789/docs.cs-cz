---
title: RemoveHandler – příkaz (Visual Basic)
ms.date: 07/20/2015
f1_keywords:
- vb.RemoveHandlerMethod
- vb.RemoveHandler
- RemoveHandler
helpviewer_keywords:
- RemoveHandler keyword [Visual Basic]
- RemoveHandler statement [Visual Basic]
ms.assetid: 647cd825-e877-4910-b4f1-8d168beebe6a
ms.openlocfilehash: 8a9dc5874629c1687318496bd7c4016eb318c25a
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58831680"
---
# <a name="removehandler-statement"></a><span data-ttu-id="c80a5-102">RemoveHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="c80a5-102">RemoveHandler Statement</span></span>
<span data-ttu-id="c80a5-103">Odebere přidružení mezi událostí a obslužnou rutinu události.</span><span class="sxs-lookup"><span data-stu-id="c80a5-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="c80a5-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="c80a5-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="c80a5-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="c80a5-105">Parts</span></span>  
  
|<span data-ttu-id="c80a5-106">Termín</span><span class="sxs-lookup"><span data-stu-id="c80a5-106">Term</span></span>|<span data-ttu-id="c80a5-107">Definice</span><span class="sxs-lookup"><span data-stu-id="c80a5-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="c80a5-108">Název události, kterou bude manipulováno.</span><span class="sxs-lookup"><span data-stu-id="c80a5-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="c80a5-109">Název procedury aktuálně zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="c80a5-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="c80a5-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="c80a5-110">Remarks</span></span>  
 <span data-ttu-id="c80a5-111">`AddHandler` a `RemoveHandler` příkazy umožňují spustit a zastavit zpracování událostí pro určitou událost kdykoli během provádění programu.</span><span class="sxs-lookup"><span data-stu-id="c80a5-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c80a5-112">Pro vlastní události `RemoveHandler` příkaz volá události `RemoveHandler` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="c80a5-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="c80a5-113">Další informace o vlastních událostech najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="c80a5-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="c80a5-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="c80a5-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="c80a5-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c80a5-115">See also</span></span>

- [<span data-ttu-id="c80a5-116">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="c80a5-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)
- [<span data-ttu-id="c80a5-117">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="c80a5-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="c80a5-118">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="c80a5-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="c80a5-119">Události</span><span class="sxs-lookup"><span data-stu-id="c80a5-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
