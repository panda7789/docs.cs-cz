---
title: Událost '<eventname1>' nemůže implementovat událost '<eventname2>' v rozhraní '<interface>' , protože se neshodují jejich typy delegátů '<delegate1>' a '<delegate2>'.
ms.date: 07/20/2015
f1_keywords:
- vbc31423
- bc31423
helpviewer_keywords:
- BC31423
ms.assetid: 2e754b66-5836-48ff-9697-b9c0d7085f18
ms.openlocfilehash: d6b85124b4408df532623f7c14a76e936ea28572
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625547"
---
# <a name="event-eventname1-cannot-implement-event-eventname2-on-interface-interface-because-their-delegate-types-delegate1-and-delegate2-do-not-match"></a><span data-ttu-id="35918-102">Události "\<eventname1 >' nemůže implementovat událost '\<eventname2 >" na rozhraní "\<rozhraní >" vzhledem k tomu, jejich typy delegátů\<delegate1 > "a"\<delegate2 >' se neshodují s</span><span class="sxs-lookup"><span data-stu-id="35918-102">Event '\<eventname1>' cannot implement event '\<eventname2>' on interface '\<interface>' because their delegate types '\<delegate1>' and '\<delegate2>' do not match</span></span>
<span data-ttu-id="35918-103">Visual Basic nemůže implementovat událost, protože typ delegáta události neodpovídá typu delegáta události v rozhraní.</span><span class="sxs-lookup"><span data-stu-id="35918-103">Visual Basic cannot implement an event because the delegate type of the event does not match the delegate type of the event in the interface.</span></span> <span data-ttu-id="35918-104">Této chybě může dojít při definování více událostí v rozhraní a pak pokus o jejich implementaci společně se stejnou událost.</span><span class="sxs-lookup"><span data-stu-id="35918-104">This error can occur when you define multiple events in an interface and then attempt to implement them together with the same event.</span></span> <span data-ttu-id="35918-105">Událost můžete implementovat dvě nebo více událostí pouze v případě, že vše je implementováno události jsou deklarovány pomocí `As` syntaxe a zadejte stejný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="35918-105">An event can implement two or more events only if all implemented events are declared using the `As` syntax and specify the same delegate type.</span></span>  
  
 <span data-ttu-id="35918-106">**ID chyby:** BC31423</span><span class="sxs-lookup"><span data-stu-id="35918-106">**Error ID:** BC31423</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="35918-107">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="35918-107">To correct this error</span></span>  
  
- <span data-ttu-id="35918-108">Implementace události samostatně.</span><span class="sxs-lookup"><span data-stu-id="35918-108">Implement the events separately.</span></span>  
  
     <span data-ttu-id="35918-109">—nebo—</span><span class="sxs-lookup"><span data-stu-id="35918-109">—or—</span></span>  
  
- <span data-ttu-id="35918-110">Definování události pomocí rozhraní `As` syntaxe a zadejte stejný typ delegáta.</span><span class="sxs-lookup"><span data-stu-id="35918-110">Define the events in the interface using the `As` syntax and specify the same delegate type.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="35918-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="35918-111">See also</span></span>

- [<span data-ttu-id="35918-112">Příkaz Event</span><span class="sxs-lookup"><span data-stu-id="35918-112">Event Statement</span></span>](../../../visual-basic/language-reference/statements/event-statement.md)
- [<span data-ttu-id="35918-113">Příkaz Delegate</span><span class="sxs-lookup"><span data-stu-id="35918-113">Delegate Statement</span></span>](../../../visual-basic/language-reference/statements/delegate-statement.md)
- [<span data-ttu-id="35918-114">Události</span><span class="sxs-lookup"><span data-stu-id="35918-114">Events</span></span>](../../../visual-basic/programming-guide/language-features/events/index.md)
