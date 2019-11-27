---
title: 'Postupy: Deklarování vlastních událostí pro konzervaci paměti'
ms.date: 07/20/2015
helpviewer_keywords:
- declaring events [Visual Basic], custom
- events [Visual Basic], custom
- custom events [Visual Basic]
ms.assetid: 87ebee87-260c-462f-979c-407874debd19
ms.openlocfilehash: 3cc2d3ea57f1a8daf704c2c929baf3f2acf78c17
ms.sourcegitcommit: 17ee6605e01ef32506f8fdc686954244ba6911de
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/22/2019
ms.locfileid: "74345133"
---
# <a name="how-to-declare-custom-events-to-conserve-memory-visual-basic"></a><span data-ttu-id="b2e29-102">Postupy: Deklarování vlastních událostí pro konzervaci paměti (Visual Basic)</span><span class="sxs-lookup"><span data-stu-id="b2e29-102">How to: Declare Custom Events To Conserve Memory (Visual Basic)</span></span>
<span data-ttu-id="b2e29-103">V některých případech je důležité, aby aplikace zachovala využití paměti nízké.</span><span class="sxs-lookup"><span data-stu-id="b2e29-103">There are several circumstances when it is important that an application keep its memory usage low.</span></span> <span data-ttu-id="b2e29-104">Vlastní události umožňují, aby aplikace používala paměť pouze pro události, které zpracovává.</span><span class="sxs-lookup"><span data-stu-id="b2e29-104">Custom events allow the application to use memory only for the events that it handles.</span></span>  
  
 <span data-ttu-id="b2e29-105">Ve výchozím nastavení, když třída deklaruje událost, kompilátor přiděluje paměť pro pole k uložení informací o události.</span><span class="sxs-lookup"><span data-stu-id="b2e29-105">By default, when a class declares an event, the compiler allocates memory for a field to store the event information.</span></span> <span data-ttu-id="b2e29-106">Pokud má třída mnoho nepoužívaných událostí, zbytečně zabírat paměť.</span><span class="sxs-lookup"><span data-stu-id="b2e29-106">If a class has many unused events, they needlessly take up memory.</span></span>  
  
 <span data-ttu-id="b2e29-107">Místo použití výchozí implementace událostí, které Visual Basic poskytuje, můžete použít vlastní události a pečlivě spravovat využití paměti.</span><span class="sxs-lookup"><span data-stu-id="b2e29-107">Instead of using the default implementation of events that Visual Basic provides, you can use custom events to manage the memory usage more carefully.</span></span>  
  
## <a name="example"></a><span data-ttu-id="b2e29-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="b2e29-108">Example</span></span>  
 <span data-ttu-id="b2e29-109">V tomto příkladu třída používá jednu instanci třídy <xref:System.ComponentModel.EventHandlerList>, uloženou v poli `Events` pro ukládání informací o používaných událostech.</span><span class="sxs-lookup"><span data-stu-id="b2e29-109">In this example, the class uses one instance of the <xref:System.ComponentModel.EventHandlerList> class, stored in the `Events` field, to store information about the events in use.</span></span> <span data-ttu-id="b2e29-110">Třída <xref:System.ComponentModel.EventHandlerList> je optimalizovaná třída seznamu navržená tak, aby obsahovala delegáty.</span><span class="sxs-lookup"><span data-stu-id="b2e29-110">The <xref:System.ComponentModel.EventHandlerList> class is an optimized list class designed to hold delegates.</span></span>  
  
 <span data-ttu-id="b2e29-111">Všechny události ve třídě používají pole `Events` k udržení přehledu o tom, jaké metody zpracovávají jednotlivé události.</span><span class="sxs-lookup"><span data-stu-id="b2e29-111">All events in the class use the `Events` field to keep track of what methods are handling each event.</span></span>  
  
 [!code-vb[VbVbalrEvents#22](~/samples/snippets/visualbasic/VS_Snippets_VBCSharp/VbVbalrEvents/VB/Class1.vb#22)]  
  
## <a name="see-also"></a><span data-ttu-id="b2e29-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="b2e29-112">See also</span></span>

- <xref:System.ComponentModel.EventHandlerList>
- [<span data-ttu-id="b2e29-113">Události</span><span class="sxs-lookup"><span data-stu-id="b2e29-113">Events</span></span>](../../../../visual-basic/programming-guide/language-features/events/index.md)
- [<span data-ttu-id="b2e29-114">Postupy: Deklarování vlastních událostí k zabránění blokování</span><span class="sxs-lookup"><span data-stu-id="b2e29-114">How to: Declare Custom Events To Avoid Blocking</span></span>](../../../../visual-basic/programming-guide/language-features/events/how-to-declare-custom-events-to-avoid-blocking.md)
