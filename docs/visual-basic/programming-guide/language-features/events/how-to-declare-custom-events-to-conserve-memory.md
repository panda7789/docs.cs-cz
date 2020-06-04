---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: c9a049d3f15d5620152f064888a97bd0be5d46b0
ms.sourcegitcommit: f8c270376ed905f6a8896ce0fe25b4f4b38ff498
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/04/2020
ms.locfileid: "84405128"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="e6986-102">Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="e6986-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="e6986-103">V některých případech je důležité, aby aplikace zachovala využití paměti nízké.</span><span class="sxs-lookup"><span data-stu-id="e6986-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="e6986-104">Vlastní události umožňují, aby aplikace používala paměť pouze pro události, které zpracovává.</span><span class="sxs-lookup"><span data-stu-id="e6986-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="e6986-105">Ve výchozím nastavení, když třída deklaruje událost, kompilátor přiděluje paměť pro pole k uložení informací o události.</span><span class="sxs-lookup"><span data-stu-id="e6986-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="e6986-106">Pokud má třída mnoho nepoužívaných událostí, zbytečně zabírat paměť.</span><span class="sxs-lookup"><span data-stu-id="e6986-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="e6986-107">Místo použití výchozí implementace událostí, které Visual Basic poskytuje, můžete použít vlastní události a pečlivě spravovat využití paměti.</span><span class="sxs-lookup"><span data-stu-id="e6986-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e6986-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="e6986-108">Example</span></span>  
 <span data-ttu-id="e6986-109">V tomto příkladu třída používá jednu instanci <xref:System.ComponentModel.EventHandlerList> třídy uloženou v `Events` poli pro ukládání informací o používaných událostech.</span><span class="sxs-lookup"><span data-stu-id="e6986-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="e6986-110"><xref:System.ComponentModel.EventHandlerList>Třída je optimalizovaná třída seznamu navržená tak, aby obsahovala delegáty.</span><span class="sxs-lookup"><span data-stu-id="e6986-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="e6986-111">Všechny události ve třídě používají `Events` pole k udržení přehledu o tom, jaké metody zpracovávají jednotlivé události.</span><span class="sxs-lookup"><span data-stu-id="e6986-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="e6986-112">Viz také</span><span class="sxs-lookup"><span data-stu-id="e6986-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="e6986-113">Události</span><span class="sxs-lookup"><span data-stu-id="e6986-113">Events</span></span>](index.md)
- [<span data-ttu-id="e6986-114">Postupy: Deklarování vlastních událostí k zabránění blokování</span><span class="sxs-lookup"><span data-stu-id="e6986-114">How to: Declare Custom Events To Avoid Blocking</span></span>](how-to-declare-custom-events-to-avoid-blocking.md)
