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
ms.openlocfilehash: a6655652a7c5dedb8e183356688972c07a705cbc
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931838"
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="36bce-102">Postupy: Ruční vykreslení grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="36bce-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="36bce-103">Pokud spravujete vlastní grafiku ve vyrovnávací paměti, budete muset vytvořit a vykreslit grafické vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="36bce-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="36bce-104">Můžete vytvořit instance <xref:System.Drawing.BufferedGraphics> třídy, které jsou spojeny s kreslicími plochami na obrazovce <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> voláním metody.</span><span class="sxs-lookup"><span data-stu-id="36bce-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="36bce-105">Tato metoda vytvoří <xref:System.Drawing.BufferedGraphics> instanci, která je přidružena k určité ploše vykreslování, jako je například formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="36bce-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="36bce-106">Po vytvoření <xref:System.Drawing.BufferedGraphics> instance můžete grafiku nakreslit do vyrovnávací paměti, kterou představuje <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="36bce-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="36bce-107">Po provedení všech grafických operací můžete zkopírovat obsah vyrovnávací paměti na obrazovku voláním <xref:System.Drawing.BufferedGraphics.Render%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="36bce-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="36bce-108">Pokud provedete vlastní vykreslování, spotřeba paměti se zvýší, i když zvýšení může být jen slabé.</span><span class="sxs-lookup"><span data-stu-id="36bce-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="36bce-109">Ruční zobrazení grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="36bce-109">To manually display buffered graphics</span></span>  
  
1. <span data-ttu-id="36bce-110">Získejte odkaz na instanci <xref:System.Drawing.BufferedGraphicsContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="36bce-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="36bce-111">Další informace najdete v tématu [jak: Ručně spravovat grafiku](how-to-manually-manage-buffered-graphics.md)uloženou v vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="36bce-111">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2. <span data-ttu-id="36bce-112">Vytvořte instanci <xref:System.Drawing.BufferedGraphics> třídy <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> voláním metody, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="36bce-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3. <span data-ttu-id="36bce-113">Nakreslete grafiku do vyrovnávací paměti grafiky nastavením <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="36bce-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="36bce-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="36bce-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4. <span data-ttu-id="36bce-115">Až dokončíte všechny operace kreslení do vyrovnávací paměti grafiky, zavolejte <xref:System.Drawing.BufferedGraphics.Render%2A> metodu pro vykreslení vyrovnávací paměti, buď na kreslicí plochu přidruženou k této vyrovnávací paměti, nebo na zadanou plochu kresby, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="36bce-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5. <span data-ttu-id="36bce-116">Po dokončení vykreslování grafiky zavolejte `Dispose` metodu <xref:System.Drawing.BufferedGraphics> v instanci, abyste uvolnili systémové prostředky.</span><span class="sxs-lookup"><span data-stu-id="36bce-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="36bce-117">Viz také:</span><span class="sxs-lookup"><span data-stu-id="36bce-117">See also</span></span>

- <xref:System.Drawing.BufferedGraphicsContext>
- <xref:System.Drawing.BufferedGraphics>
- [<span data-ttu-id="36bce-118">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="36bce-118">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="36bce-119">Postupy: Ruční správa grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="36bce-119">How to: Manually Manage Buffered Graphics</span></span>](how-to-manually-manage-buffered-graphics.md)
