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
ms.openlocfilehash: 1e8d8f512f163d82f074a5ad53fbb38a10904dfa
ms.sourcegitcommit: bce0586f0cccaae6d6cbd625d5a7b824d1d3de4b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/02/2019
ms.locfileid: "58827078"
---
# <a name="addhandler-statement"></a><span data-ttu-id="79773-102">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="79773-102">AddHandler Statement</span></span>
<span data-ttu-id="79773-103">Přidruží událost k obslužné rutiny události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="79773-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="79773-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="79773-104">Syntax</span></span>  
  
```  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="79773-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="79773-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="79773-106">event</span><span class="sxs-lookup"><span data-stu-id="79773-106">event</span></span>|<span data-ttu-id="79773-107">Název události ke zpracování.</span><span class="sxs-lookup"><span data-stu-id="79773-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="79773-108">Název procedury, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="79773-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="79773-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="79773-109">Remarks</span></span>  
 <span data-ttu-id="79773-110">`AddHandler` a `RemoveHandler` příkazy umožňují spustit a zastavit zpracování událostí v průběhu provádění programu.</span><span class="sxs-lookup"><span data-stu-id="79773-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="79773-111">Podpis metody `eventhandler` postupu musí odpovídat signatuře události `event`.</span><span class="sxs-lookup"><span data-stu-id="79773-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="79773-112">`Handles` – Klíčové slovo a `AddHandler` příkaz oba umožňují určit, že konkrétní postupy zpracování určité události, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="79773-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="79773-113">`AddHandler` Příkaz se připojí postupy k událostem v době běhu.</span><span class="sxs-lookup"><span data-stu-id="79773-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="79773-114">Použití `Handles` – klíčové slovo při definování proceduru k určení, že zpracovává konkrétní události.</span><span class="sxs-lookup"><span data-stu-id="79773-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="79773-115">Další informace najdete v tématu [zpracovává](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="79773-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="79773-116">Pro vlastní události `AddHandler` příkaz volá události `AddHandler` přistupujícího objektu.</span><span class="sxs-lookup"><span data-stu-id="79773-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="79773-117">Další informace o vlastních událostech najdete v tématu [Event – příkaz](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="79773-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="79773-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="79773-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="79773-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="79773-119">See also</span></span>

- [<span data-ttu-id="79773-120">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="79773-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="79773-121">Obslužné rutiny</span><span class="sxs-lookup"><span data-stu-id="79773-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="79773-122">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="79773-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="79773-123">Události</span><span class="sxs-lookup"><span data-stu-id="79773-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
