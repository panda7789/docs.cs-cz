---
title: "Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)"
ms.custom: 
ms.date: 07/20/2015
ms.prod: .net
ms.reviewer: 
ms.suite: 
ms.technology: devlang-visual-basic
ms.topic: article
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
ms.openlocfilehash: eec9a2fc687f481ab40313e35cbde81c25b81ae8
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="37ac2-102">Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="37ac2-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="37ac2-103">Pokud je důležité, aby aplikace byl jeho využití paměti nízkou existuje několik okolností.</span><span class="sxs-lookup"><span data-stu-id="37ac2-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="37ac2-104">Vlastní události povolit aplikaci používat pouze pro události, které zpracovává paměti.</span><span class="sxs-lookup"><span data-stu-id="37ac2-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="37ac2-105">Ve výchozím nastavení když třída deklaruje událost, kompilátor přidělí paměť pro pole pro uložení informací o události.</span><span class="sxs-lookup"><span data-stu-id="37ac2-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="37ac2-106">Pokud třída má mnoho nepoužívané událostí, zbytečnému zabírají paměť.</span><span class="sxs-lookup"><span data-stu-id="37ac2-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="37ac2-107">Místo použití výchozí implementace událostí, které poskytuje jazyka Visual Basic, můžete použít vlastní události ke správě více pečlivě využití paměti.</span><span class="sxs-lookup"><span data-stu-id="37ac2-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="37ac2-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="37ac2-108">Example</span></span>  
 <span data-ttu-id="37ac2-109">V tomto příkladu třída používá jednu instanci <xref:System.ComponentModel.EventHandlerList> třídy, které jsou uložené v `Events` pro ukládání informací o událostech v použití pole.</span><span class="sxs-lookup"><span data-stu-id="37ac2-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="37ac2-110"><xref:System.ComponentModel.EventHandlerList> Třídy je třída optimalizované seznamu navržený tak, aby udržení delegáti.</span><span class="sxs-lookup"><span data-stu-id="37ac2-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="37ac2-111">Všechny události v použití třídy `Events` pole ke sledování jaké metody se zpracování jednotlivých událostí.</span><span class="sxs-lookup"><span data-stu-id="37ac2-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](../../../../visual-basic/language-reference/statements/codesnippet/VisualBasic/how-to-declare-custom-events-to-conserve-memory_1.vb)]  
  
## <a name="see-also"></a><span data-ttu-id="37ac2-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="37ac2-112">See Also</span></span>  
 <xref:System.ComponentModel.EventHandlerList>  
 [<span data-ttu-id="37ac2-113">Události</span><span class="sxs-lookup"><span data-stu-id="37ac2-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)  
 [<span data-ttu-id="37ac2-114">Postupy: deklarování vlastních událostí k zabránění blokování</span><span class="sxs-lookup"><span data-stu-id="37ac2-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
