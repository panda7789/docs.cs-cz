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
ms.openlocfilehash: 0d982768707948bd6c616445509e16a462b86f2c
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33597985"
---
# <a name="removehandler-statement"></a><span data-ttu-id="88023-102">RemoveHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="88023-102">RemoveHandler Statement</span></span>
<span data-ttu-id="88023-103">Odebere přidružení mezi událost a obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="88023-103">Removes the association between an event and an event handler.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="88023-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="88023-104">Syntax</span></span>  
  
```  
RemoveHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="88023-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="88023-105">Parts</span></span>  
  
|<span data-ttu-id="88023-106">Termín</span><span class="sxs-lookup"><span data-stu-id="88023-106">Term</span></span>|<span data-ttu-id="88023-107">Definice</span><span class="sxs-lookup"><span data-stu-id="88023-107">Definition</span></span>|  
|---|---|  
|`event`|<span data-ttu-id="88023-108">Název události ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="88023-108">The name of the event being handled.</span></span>|  
|`eventhandler`|<span data-ttu-id="88023-109">Název procesu, který aktuálně zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="88023-109">The name of the procedure currently handling the event.</span></span>|  
  
## <a name="remarks"></a><span data-ttu-id="88023-110">Poznámky</span><span class="sxs-lookup"><span data-stu-id="88023-110">Remarks</span></span>  
 <span data-ttu-id="88023-111">`AddHandler` a `RemoveHandler` příkazy umožňují spuštění a zastavení zpracování událostí pro určitou událost kdykoli během spuštění programu.</span><span class="sxs-lookup"><span data-stu-id="88023-111">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling for a specific event at any time during program execution.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="88023-112">Pro vlastní události `RemoveHandler` příkaz volá události `RemoveHandler` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="88023-112">For custom events, the `RemoveHandler` statement invokes the event's `RemoveHandler` accessor.</span></span> <span data-ttu-id="88023-113">Další informace o vlastních událostí najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="88023-113">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="88023-114">Příklad</span><span class="sxs-lookup"><span data-stu-id="88023-114">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/removehandler-statement_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="88023-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="88023-115">See Also</span></span>  
 [<span data-ttu-id="88023-116">Příkaz AddHandler</span><span class="sxs-lookup"><span data-stu-id="88023-116">AddHandler Statement</span></span>](../../../visual-basic/language-reference/statements/addhandler-statement.md)  
 [<span data-ttu-id="88023-117">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="88023-117">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)  
 [<span data-ttu-id="88023-118">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="88023-118">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)  
 [<span data-ttu-id="88023-119">Události</span><span class="sxs-lookup"><span data-stu-id="88023-119">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
