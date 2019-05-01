---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: e4132f51f4dd85ad964042d05f7c5bc0a2e6e3cd
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61973157"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="c534b-102">Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="c534b-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="c534b-103">Existují několika případech, kdy je důležité, aby aplikace byl jeho využití paměti nízké.</span><span class="sxs-lookup"><span data-stu-id="c534b-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="c534b-104">Vlastní události, aby aplikace použít pouze pro události, které zpracovává paměti.</span><span class="sxs-lookup"><span data-stu-id="c534b-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="c534b-105">Ve výchozím nastavení když třída deklaruje událost, kompilátor přiděluje paměť pro pole k ukládání informací o události.</span><span class="sxs-lookup"><span data-stu-id="c534b-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="c534b-106">Pokud třída má mnoho událostí nevyužité, zbytečně zabírají paměti.</span><span class="sxs-lookup"><span data-stu-id="c534b-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="c534b-107">Místo použití výchozí implementace události, které poskytuje Visual Basic, můžete použít vlastní události více pečlivě spravovat využití paměti.</span><span class="sxs-lookup"><span data-stu-id="c534b-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c534b-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c534b-108">Example</span></span>  
 <span data-ttu-id="c534b-109">V tomto příkladu třída používá jednu instanci <xref:System.ComponentModel.EventHandlerList> třídy, které jsou uložené v `Events` pole k ukládání informací o událostech používá.</span><span class="sxs-lookup"><span data-stu-id="c534b-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="c534b-110"><xref:System.ComponentModel.EventHandlerList> Třídy je třída optimalizované seznam navržených pro ukládání delegátů.</span><span class="sxs-lookup"><span data-stu-id="c534b-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="c534b-111">Všechny události v třídy `Events` pole, které chcete sledovat, jaké metody se zpracování každé události.</span><span class="sxs-lookup"><span data-stu-id="c534b-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="c534b-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c534b-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="c534b-113">Události</span><span class="sxs-lookup"><span data-stu-id="c534b-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="c534b-114">Postupy: Deklarování vlastních událostí k zabránění blokování</span><span class="sxs-lookup"><span data-stu-id="c534b-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
