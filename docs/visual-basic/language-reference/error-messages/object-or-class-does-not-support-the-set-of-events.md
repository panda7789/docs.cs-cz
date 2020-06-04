---
title: Objekt nebo třída nepodporuje sadu událostí.
ms.date: 07/20/2015
f1_keywords:
- vbrID459
ms.assetid: 785df3f3-2aae-4a25-af36-1f9879d4e5fd
ms.openlocfilehash: bc75e031c2d05bea3aa64774a9d3817756e51e8b
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84409358"
---
# <a name="object-or-class-does-not-support-the-set-of-events"></a><span data-ttu-id="1a360-102">Objekt nebo třída nepodporuje sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="1a360-102">Object or class does not support the set of events</span></span>
<span data-ttu-id="1a360-103">Pokusili jste se použít `WithEvents` proměnnou s komponentou, která nemůže fungovat jako zdroj události pro zadanou sadu událostí.</span><span class="sxs-lookup"><span data-stu-id="1a360-103">You tried to use a `WithEvents` variable with a component that cannot work as an event source for the specified set of events.</span></span> <span data-ttu-id="1a360-104">Například jste chtěli zpracovat události objektu a pak vytvořit další objekt, který `Implements` je prvním objektem.</span><span class="sxs-lookup"><span data-stu-id="1a360-104">For example, you wanted to sink the events of an object, then create another object that `Implements` the first object.</span></span> <span data-ttu-id="1a360-105">I když byste si mohli představit události z implementovaného objektu, nejedná se vždy o případ.</span><span class="sxs-lookup"><span data-stu-id="1a360-105">Although you might think you could sink the events from the implemented object, this is not always the case.</span></span> <span data-ttu-id="1a360-106">`Implements`implementuje pouze rozhraní pro metody a vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1a360-106">`Implements` only implements an interface for methods and properties.</span></span> <span data-ttu-id="1a360-107">`WithEvents`není podporováno pro Private `UserControls` , protože informace o typu potřebné k vyvolání `ObjectEvent` není v době běhu k dispozici.</span><span class="sxs-lookup"><span data-stu-id="1a360-107">`WithEvents` is not supported for private `UserControls`, because the type info needed to raise the `ObjectEvent` is not available at run time.</span></span>  
  
## <a name="to-correct-this-error"></a><span data-ttu-id="1a360-108">Oprava této chyby</span><span class="sxs-lookup"><span data-stu-id="1a360-108">To correct this error</span></span>  
  
1. <span data-ttu-id="1a360-109">Pro komponentu, která nemá zdrojové události, nelze události jímky.</span><span class="sxs-lookup"><span data-stu-id="1a360-109">You cannot sink events for a component that does not source events.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1a360-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="1a360-110">See also</span></span>

- [<span data-ttu-id="1a360-111">WithEvents</span><span class="sxs-lookup"><span data-stu-id="1a360-111">WithEvents</span></span>](../modifiers/withevents.md)
- [<span data-ttu-id="1a360-112">Implements – Příkaz</span><span class="sxs-lookup"><span data-stu-id="1a360-112">Implements Statement</span></span>](../statements/implements-statement.md)
