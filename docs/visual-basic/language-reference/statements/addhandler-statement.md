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
ms.openlocfilehash: c110116af75d4fb39c016b8d6afcdb707fa6599b
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74350181"
---
# <a name="addhandler-statement"></a><span data-ttu-id="83692-102">AddHandler – příkaz</span><span class="sxs-lookup"><span data-stu-id="83692-102">AddHandler Statement</span></span>
<span data-ttu-id="83692-103">Přidruží událost k obslužné rutině události v době běhu.</span><span class="sxs-lookup"><span data-stu-id="83692-103">Associates an event with an event handler at run time.</span></span>  
  
## <a name="syntax"></a><span data-ttu-id="83692-104">Syntaxe</span><span class="sxs-lookup"><span data-stu-id="83692-104">Syntax</span></span>  
  
```vb  
AddHandler event, AddressOf eventhandler  
```  
  
## <a name="parts"></a><span data-ttu-id="83692-105">Součásti</span><span class="sxs-lookup"><span data-stu-id="83692-105">Parts</span></span>  
|||
|---|---|
|<span data-ttu-id="83692-106">událost</span><span class="sxs-lookup"><span data-stu-id="83692-106">event</span></span>|<span data-ttu-id="83692-107">Název události, která má být zpracována.</span><span class="sxs-lookup"><span data-stu-id="83692-107">The name of the event to handle.</span></span>|  
|`eventhandler`|<span data-ttu-id="83692-108">Název procedury, která zpracovává událost.</span><span class="sxs-lookup"><span data-stu-id="83692-108">The name of a procedure that handles the event.</span></span>|
|||
  
## <a name="remarks"></a><span data-ttu-id="83692-109">Poznámky</span><span class="sxs-lookup"><span data-stu-id="83692-109">Remarks</span></span>  
 <span data-ttu-id="83692-110">Příkazy `AddHandler` a `RemoveHandler` umožňují kdykoli spustit a zastavit zpracování událostí během provádění programu.</span><span class="sxs-lookup"><span data-stu-id="83692-110">The `AddHandler` and `RemoveHandler` statements allow you to start and stop event handling at any time during program execution.</span></span>  
  
 <span data-ttu-id="83692-111">Podpis `eventhandler`ho postupu musí odpovídat podpisu `event`události.</span><span class="sxs-lookup"><span data-stu-id="83692-111">The signature of the `eventhandler` procedure must match the signature of the event `event`.</span></span>  
  
 <span data-ttu-id="83692-112">Klíčové slovo `Handles` a příkaz `AddHandler` umožňují určit, že konkrétní procedury budou zpracovávat konkrétní události, ale existují rozdíly.</span><span class="sxs-lookup"><span data-stu-id="83692-112">The `Handles` keyword and the `AddHandler` statement both allow you to specify that particular procedures handle particular events, but there are differences.</span></span> <span data-ttu-id="83692-113">Příkaz `AddHandler` propojuje procedury s událostmi v době běhu.</span><span class="sxs-lookup"><span data-stu-id="83692-113">The `AddHandler` statement connects procedures to events at run time.</span></span> <span data-ttu-id="83692-114">Při definování procedury použijte klíčové slovo `Handles`, které určuje, že zpracuje konkrétní událost.</span><span class="sxs-lookup"><span data-stu-id="83692-114">Use the `Handles` keyword when defining a procedure to specify that it handles a particular event.</span></span> <span data-ttu-id="83692-115">Další informace najdete v tématu [obslužné rutiny](../../../visual-basic/language-reference/statements/handles-clause.md).</span><span class="sxs-lookup"><span data-stu-id="83692-115">For more information, see [Handles](../../../visual-basic/language-reference/statements/handles-clause.md).</span></span>  
  
> [!NOTE]
> <span data-ttu-id="83692-116">Pro vlastní události příkaz `AddHandler` vyvolá přistupující objekt `AddHandler` události.</span><span class="sxs-lookup"><span data-stu-id="83692-116">For custom events, the `AddHandler` statement invokes the event's `AddHandler` accessor.</span></span> <span data-ttu-id="83692-117">Další informace o vlastních událostech naleznete v tématu [příkaz Event](../../../visual-basic/language-reference/statements/event-statement.md).</span><span class="sxs-lookup"><span data-stu-id="83692-117">For more information on custom events, see [Event Statement](../../../visual-basic/language-reference/statements/event-statement.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="83692-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="83692-118">Example</span></span>  
 [!code-vb[VbVbalrEvents#17](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#17)]  
  
## <a name="see-also"></a><span data-ttu-id="83692-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="83692-119">See also</span></span>

- [<span data-ttu-id="83692-120">Příkaz RemoveHandler</span><span class="sxs-lookup"><span data-stu-id="83692-120">RemoveHandler Statement</span></span>](../../../visual-basic/language-reference/statements/removehandler-statement.md)
- [<span data-ttu-id="83692-121">Řeší</span><span class="sxs-lookup"><span data-stu-id="83692-121">Handles</span></span>](../../../visual-basic/language-reference/statements/handles-clause.md)
- [<span data-ttu-id="83692-122">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="83692-122">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="83692-123">Události</span><span class="sxs-lookup"><span data-stu-id="83692-123">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
