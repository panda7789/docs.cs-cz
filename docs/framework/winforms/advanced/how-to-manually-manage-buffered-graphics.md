---
title: "Postupy: Ruční správa grafiky uložené do vyrovnávací"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually managing graphics
- graphics [Windows Forms], managing buffered
ms.assetid: 4c2a90ee-bbbe-4ff6-9170-1b06c195c918
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 4f545cf4689a2c8058e77f4b4721788ffb0e7247
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="3bf95-102">Postupy: Ruční správa grafiky uložené do vyrovnávací</span><span class="sxs-lookup"><span data-stu-id="3bf95-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="3bf95-103">Pro pokročilejší scénáře dvojité vyrovnávací paměti, můžete použít [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] třídy k implementaci vlastní logiky dvojité ukládání do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="3bf95-103">For more advanced double buffering scenarios, you can use the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="3bf95-104">Je třída, která přidělování a správa vyrovnávací paměti jednotlivých grafiky <xref:System.Drawing.BufferedGraphicsContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="3bf95-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="3bf95-105">Každá aplikace má svou vlastní výchozí <xref:System.Drawing.BufferedGraphicsContext> který spravuje všechny výchozí dvojité ukládání do vyrovnávací paměti pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="3bf95-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="3bf95-106">Odkaz na tuto instanci můžete načíst pomocí volání <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="3bf95-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="3bf95-107">Chcete-li získat odkaz na výchozí BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="3bf95-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="3bf95-108">Nastavte <xref:System.Drawing.BufferedGraphicsManager.Current%2A> vlastnost, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3bf95-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    >  <span data-ttu-id="3bf95-109">Není potřeba volat `Dispose` metodu <xref:System.Drawing.BufferedGraphicsContext> odkaz, který jste dostali od <xref:System.Drawing.BufferedGraphicsManager> třídy.</span><span class="sxs-lookup"><span data-stu-id="3bf95-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="3bf95-110"><xref:System.Drawing.BufferedGraphicsManager> Zpracovává všechny přidělování paměti a distribuci pro výchozí <xref:System.Drawing.BufferedGraphicsContext> instance.</span><span class="sxs-lookup"><span data-stu-id="3bf95-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="3bf95-111">Pro graficky náročné aplikace, jako je například animace, může někdy zlepšit výkon pomocí vyhrazená <xref:System.Drawing.BufferedGraphicsContext> místo <xref:System.Drawing.BufferedGraphicsContext> poskytované <xref:System.Drawing.BufferedGraphicsManager>.</span><span class="sxs-lookup"><span data-stu-id="3bf95-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="3bf95-112">To umožňuje vytvářet a spravovat vyrovnávací paměti grafiky samostatně, aniž by docházelo k správy všechny ostatní ve vyrovnávací paměti obrázky přidružené aplikace, když bude paměť spotřebovávají aplikace větší nároky na výkon.</span><span class="sxs-lookup"><span data-stu-id="3bf95-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="3bf95-113">Chcete-li vytvořit vyhrazený BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="3bf95-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
-   <span data-ttu-id="3bf95-114">Deklarace a vytvořit novou instanci třídy <xref:System.Drawing.BufferedGraphicsContext> třídy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="3bf95-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="3bf95-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="3bf95-115">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 [<span data-ttu-id="3bf95-116">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="3bf95-116">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="3bf95-117">Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="3bf95-117">How to: Manually Render Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-render-buffered-graphics.md)
