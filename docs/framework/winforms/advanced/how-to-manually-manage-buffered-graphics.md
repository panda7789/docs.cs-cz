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
ms.openlocfilehash: 6010d52750b20c07db51917621f8643e9d9b47d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69968604"
---
# <a name="how-to-manually-manage-buffered-graphics"></a><span data-ttu-id="9215b-102">Postupy: Ruční správa grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="9215b-102">How to: Manually Manage Buffered Graphics</span></span>
<span data-ttu-id="9215b-103">Pro pokročilejší scénáře s dvojitou vyrovnávací pamětí můžete použít třídy .NET Framework k implementaci vlastní logiky s dvojitou vyrovnávací pamětí.</span><span class="sxs-lookup"><span data-stu-id="9215b-103">For more advanced double buffering scenarios, you can use the .NET Framework classes to implement your own double-buffering logic.</span></span> <span data-ttu-id="9215b-104">Třída zodpovědná za přidělení a správu jednotlivých vyrovnávacích pamětí grafiky je <xref:System.Drawing.BufferedGraphicsContext> třída.</span><span class="sxs-lookup"><span data-stu-id="9215b-104">The class responsible for allocating and managing individual graphics buffers is the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="9215b-105">Každá aplikace má svou vlastní výchozí <xref:System.Drawing.BufferedGraphicsContext> hodnotu, která spravuje všechny výchozí dvojité ukládání do vyrovnávací paměti pro tuto aplikaci.</span><span class="sxs-lookup"><span data-stu-id="9215b-105">Every application has its own default <xref:System.Drawing.BufferedGraphicsContext> that manages all of the default double buffering for that application.</span></span> <span data-ttu-id="9215b-106">Odkaz na tuto instanci lze načíst voláním metody <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span><span class="sxs-lookup"><span data-stu-id="9215b-106">You can retrieve a reference to this instance by calling the <xref:System.Drawing.BufferedGraphicsManager.Current%2A>.</span></span>  
  
### <a name="to-obtain-a-reference-to-the-default-bufferedgraphicscontext"></a><span data-ttu-id="9215b-107">Získání odkazu na výchozí BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="9215b-107">To obtain a reference to the default BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="9215b-108"><xref:System.Drawing.BufferedGraphicsManager.Current%2A> Nastavte vlastnost, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="9215b-108">Set the <xref:System.Drawing.BufferedGraphicsManager.Current%2A> property, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#11)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#11](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#11)]  
  
    > [!NOTE]
    > <span data-ttu-id="9215b-109">Nemusíte volat `Dispose` metodu <xref:System.Drawing.BufferedGraphicsContext> na odkaz <xref:System.Drawing.BufferedGraphicsManager> , který obdržíte od třídy.</span><span class="sxs-lookup"><span data-stu-id="9215b-109">You do not need to call the `Dispose` method on the <xref:System.Drawing.BufferedGraphicsContext> reference that you receive from the <xref:System.Drawing.BufferedGraphicsManager> class.</span></span> <span data-ttu-id="9215b-110">Zpracovává veškerou alokaci a distribuci paměti pro výchozí <xref:System.Drawing.BufferedGraphicsContext> instance. <xref:System.Drawing.BufferedGraphicsManager></span><span class="sxs-lookup"><span data-stu-id="9215b-110">The <xref:System.Drawing.BufferedGraphicsManager> handles all of the memory allocation and distribution for default <xref:System.Drawing.BufferedGraphicsContext> instances.</span></span>  
  
     <span data-ttu-id="9215b-111">Pro graficky náročné aplikace, jako je například animace, můžete někdy zvýšit výkon pomocí vyhrazeného <xref:System.Drawing.BufferedGraphicsContext> místo <xref:System.Drawing.BufferedGraphicsContext> , které poskytuje <xref:System.Drawing.BufferedGraphicsManager>.</span><span class="sxs-lookup"><span data-stu-id="9215b-111">For graphically intensive applications such as animation, you can sometimes improve performance by using a dedicated <xref:System.Drawing.BufferedGraphicsContext> instead of the <xref:System.Drawing.BufferedGraphicsContext> provided by the <xref:System.Drawing.BufferedGraphicsManager>.</span></span> <span data-ttu-id="9215b-112">To umožňuje vytvářet a spravovat vyrovnávací paměti grafiky jednotlivě, aniž by došlo ke zvýšení výkonu při správě všech ostatních grafických objektů přidružených k vaší aplikaci, i když paměť spotřebovaná aplikací bude větší.</span><span class="sxs-lookup"><span data-stu-id="9215b-112">This enables you to create and manage graphics buffers individually, without incurring the performance overhead of managing all the other buffered graphics associated with your application, though the memory consumed by the application will be greater.</span></span>  
  
### <a name="to-create-a-dedicated-bufferedgraphicscontext"></a><span data-ttu-id="9215b-113">Vytvoření vyhrazeného BufferedGraphicsContext</span><span class="sxs-lookup"><span data-stu-id="9215b-113">To create a dedicated BufferedGraphicsContext</span></span>  
  
- <span data-ttu-id="9215b-114">Deklarujte a vytvořte novou instanci <xref:System.Drawing.BufferedGraphicsContext> třídy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="9215b-114">Declare and create a new instance of the <xref:System.Drawing.BufferedGraphicsContext> class, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#12)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#12](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#12)]  
  
## <a name="see-also"></a><span data-ttu-id="9215b-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9215b-115">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- [<span data-ttu-id="9215b-116">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="9215b-116">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="9215b-117">Postupy: Ruční vykreslování grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="9215b-117">How to: Manually Render Buffered Graphics</span></span>](how-to-manually-render-buffered-graphics.md)
