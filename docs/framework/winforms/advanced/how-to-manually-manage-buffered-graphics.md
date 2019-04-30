---
title: 'Postupy: Ruční správa grafiky uložené do vyrovnávací paměti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
ms.openlocfilehash: 965e3225f8cf1af6d61b81434089ebacac8ad13a
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61781313"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="e6b0f-102">Postupy: Ruční správa grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e6b0f-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="e6b0f-103">Pro pokročilejší scénáře dvojité vyrovnávací paměti, můžete použít [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy implementovat vlastní logiku na dvojité ukládání do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-103">For more advanced double buffering scenarios, you can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="e6b0f-104">Je třída, která je zodpovědná za přidělení a správa jednotlivých grafické vyrovnávací paměti <xref:System.Drawing.BufferedGraphicsContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="e6b0f-105">Každá aplikace má vlastní výchozí <xref:System.Drawing.BufferedGraphicsContext> , který spravuje všechny výchozí dvojité ukládání do vyrovnávací paměti pro příslušnou aplikaci.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="e6b0f-106">Odkaz na tuto instanci lze načíst voláním <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="e6b0f-107">K získání odkazu na výchozí hodnotu BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="e6b0f-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="e6b0f-108">Nastavte <xref:System.Drawing.BufferedGraphicsManager.Current%2A> vlastnost, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="e6b0f-109">Není potřeba volat `Dispose` metodu <xref:System.Drawing.BufferedGraphicsContext> odkaz, který jste dostali z <xref:System.Drawing.BufferedGraphicsManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="e6b0f-110"><xref:System.Drawing.BufferedGraphicsManager> Zpracovává všechna přidělení paměti a distribuce pro výchozí <xref:System.Drawing.BufferedGraphicsContext> instancí.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="e6b0f-111">Pro graficky náročné aplikace, jako je animace, můžete někdy výkon lze zvýšit pomocí vyhrazené <xref:System.Drawing.BufferedGraphicsContext> místo <xref:System.Drawing.BufferedGraphicsContext> poskytované <xref:System.Drawing.BufferedGraphicsManager>.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="e6b0f-112">To umožňuje vytvářet a spravovat grafické vyrovnávací paměti jednotlivě, aniž by platili správy všechny ostatní ve vyrovnávací paměti grafiky přidruženého k aplikaci, když paměti spotřebované aplikací bude větší nároky na výkon.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="e6b0f-113">Chcete-li vytvořit vyhrazený BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="e6b0f-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="e6b0f-114">Deklarace a vytvořit novou instanci třídy <xref:System.Drawing.BufferedGraphicsContext> třídy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="e6b0f-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="e6b0f-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="e6b0f-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="e6b0f-116">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="e6b0f-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="e6b0f-117">Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="e6b0f-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
