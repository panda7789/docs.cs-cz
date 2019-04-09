---
title: 'Postupy: Ruční vykreslení grafiky uložené do vyrovnávací paměti'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
ms.openlocfilehash: b01e10ff0f65b3abfe1e60d84d66447968a310c8
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59097948"
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="808ab-102">Postupy: Ruční vykreslení grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="808ab-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="808ab-103">Pokud spravujete ve vyrovnávací paměti grafiky, musíte být schopni vytvořit a vykreslit grafické vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="808ab-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="808ab-104">Můžete vytvořit instance <xref:System.Drawing.BufferedGraphics> třídu, která je přidružený k vykreslení plochy na obrazovce voláním <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="808ab-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="808ab-105">Tato metoda vytvoří <xref:System.Drawing.BufferedGraphics> instanci, která souvisí s konkrétním vykreslovací plochu, jako je například formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="808ab-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="808ab-106">Po vytvoření <xref:System.Drawing.BufferedGraphics> instance, můžete nakreslit grafiky do vyrovnávací paměti představuje prostřednictvím <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="808ab-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="808ab-107">Po provedení všech operací grafiky, můžete zkopírovat obsah vyrovnávací paměti na obrazovku voláním <xref:System.Drawing.BufferedGraphics.Render%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="808ab-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="808ab-108">Pokud provádíte vlastní vykreslování, zvýší využití paměti, ale zvýšení může být pouze mírné.</span><span class="sxs-lookup"><span data-stu-id="808ab-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="808ab-109">Chcete-li ručně zobrazit ukládány do vyrovnávací paměti grafiky</span><span class="sxs-lookup"><span data-stu-id="808ab-109">To manually display buffered graphics</span></span>  
  
1.  <span data-ttu-id="808ab-110">Získání odkazu na instanci <xref:System.Drawing.BufferedGraphicsContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="808ab-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="808ab-111">Další informace najdete v tématu [jak: Ruční správa grafiky uložené do vyrovnávací paměti](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="808ab-111">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2.  <span data-ttu-id="808ab-112">Vytvoření instance <xref:System.Drawing.BufferedGraphics> třídy voláním <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> způsob, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="808ab-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="808ab-113">Vykreslení grafiky do vyrovnávací paměti grafiky nastavením <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="808ab-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="808ab-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="808ab-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  <span data-ttu-id="808ab-115">Po dokončení všech operací vykreslování do vyrovnávací paměti grafiky, zavolejte <xref:System.Drawing.BufferedGraphics.Render%2A> metoda k vykreslení vyrovnávací paměti, buď na návrhovém povrchu spojené s vyrovnávací paměti nebo na návrhovém povrchu, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="808ab-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  <span data-ttu-id="808ab-116">Po dokončení vykreslování grafiky volání `Dispose` metodu <xref:System.Drawing.BufferedGraphics> instance uvolnit systémové prostředky.</span><span class="sxs-lookup"><span data-stu-id="808ab-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="808ab-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="808ab-117">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="808ab-118">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="808ab-118">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="808ab-119">Postupy: Ruční správa grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="808ab-119">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)
