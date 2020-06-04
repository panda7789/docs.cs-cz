---
title: Událost '<eventname1>' nemůže implementovat událost '<eventname2>' v rozhraní '<interface>' , protože se neshodují jejich typy delegátů '<delegate1>' a '<delegate2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: 32d6733580de8798a66c30d486b8439befd2af19
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409605"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="775bb-102">Událost '\<eventname1>' nemůže implementovat událost '\<eventname2>' v rozhraní '\<interface>' , protože se neshodují jejich typy delegátů '\<delegate1>' a '\<delegate2>'.</span><span class="sxs-lookup"><span data-stu-id="775bb-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>
<span data-ttu-id="775bb-103">Visual Basic nemůže implementovat událost, protože typ delegáta události neodpovídá typu delegáta události v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="775bb-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="775bb-104">K této chybě může dojít, pokud v rozhraní definujete více událostí a pak se pokusíte o jejich implementaci společně se stejnou událostí.</span><span class="sxs-lookup"><span data-stu-id="775bb-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="775bb-105">Událost může implementovat dvě nebo více událostí pouze v případě, že všechny implementované události jsou deklarovány pomocí `As` syntaxe a určí stejný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="775bb-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="775bb-106">**ID chyby:** BC31423</span><span class="sxs-lookup"><span data-stu-id="775bb-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="775bb-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="775bb-107">To correct this error</span></span>  
  
- <span data-ttu-id="775bb-108">Implementujte události samostatně.</span><span class="sxs-lookup"><span data-stu-id="775bb-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="775bb-109">—nebo—</span><span class="sxs-lookup"><span data-stu-id="775bb-109">—or—</span></span>  
  
- <span data-ttu-id="775bb-110">Definujte události v rozhraní pomocí `As` syntaxe a zadejte stejný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="775bb-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="775bb-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="775bb-111">See also</span></span>

- [<span data-ttu-id="775bb-112">Event – příkaz</span><span class="sxs-lookup"><span data-stu-id="775bb-112">Event Statement</span></span>](../statements/event-statement.md)
- [<span data-ttu-id="775bb-113">Delegate – příkaz</span><span class="sxs-lookup"><span data-stu-id="775bb-113">Delegate Statement</span></span>](../statements/delegate-statement.md)
- [<span data-ttu-id="775bb-114">Události</span><span class="sxs-lookup"><span data-stu-id="775bb-114">Events</span></span>](../../programming-guide/language-features/events/index.md)
