---
title: "Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti"
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
- flicker [Windows Forms], reducing by manually rendering graphics
- graphics [Windows Forms], rendering
ms.assetid: 5192295e-bd8e-45f7-8bd6-5c4f6bd21e61
caps.latest.revision: "10"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d3a5d06da3a398782b0285fb55807df5832cf771
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-manually-render-buffered-graphics"></a><span data-ttu-id="58da2-102">Postupy: Ruční zobrazení grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="58da2-102">How to: Manually Render Buffered Graphics</span></span>
<span data-ttu-id="58da2-103">Pokud spravujete vlastní grafiky ve vyrovnávací paměti, musíte být schopná vytvořit a vykreslení grafiky vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="58da2-103">If you are managing your own buffered graphics, you will need to be able to create and render graphics buffers.</span></span> <span data-ttu-id="58da2-104">Můžete vytvořit instance <xref:System.Drawing.BufferedGraphics> třídu, která souvisí s kreslení povrchy na vaší obrazovce voláním <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="58da2-104">You can create instances of the <xref:System.Drawing.BufferedGraphics> class that is associated with drawing surfaces on your screen by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method.</span></span> <span data-ttu-id="58da2-105">Tato metoda vytvoří <xref:System.Drawing.BufferedGraphics> instance, který je přidružen konkrétní vykreslování prostor, jako jsou formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="58da2-105">This method creates a <xref:System.Drawing.BufferedGraphics> instance that is associated with a particular rendering surface, such as a form or control.</span></span> <span data-ttu-id="58da2-106">Po vytvoření <xref:System.Drawing.BufferedGraphics> instance, při kreslení grafiky do vyrovnávací paměti reprezentuje prostřednictvím <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="58da2-106">After you have created a <xref:System.Drawing.BufferedGraphics> instance, you can draw graphics to the buffer it represents through the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="58da2-107">Po provedení všech grafické operace, můžete zkopírovat obsah vyrovnávací paměti na obrazovku voláním <xref:System.Drawing.BufferedGraphics.Render%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="58da2-107">After you have performed all graphics operations, you can copy the contents of the buffer to the screen by calling the <xref:System.Drawing.BufferedGraphics.Render%2A> method.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="58da2-108">Pokud provádíte vlastní vykreslování, využití paměti zvýší, když zvýšení může být pouze mírné.</span><span class="sxs-lookup"><span data-stu-id="58da2-108">If you perform your own rendering, memory consumption will increase, though the increase may only be slight.</span></span>  
  
### <a name="to-manually-display-buffered-graphics"></a><span data-ttu-id="58da2-109">Chcete-li ručně zobrazit uložená do vyrovnávací paměti grafiky</span><span class="sxs-lookup"><span data-stu-id="58da2-109">To manually display buffered graphics</span></span>  
  
1.  <span data-ttu-id="58da2-110">Získat odkaz na instanci <xref:System.Drawing.BufferedGraphicsContext> třídy.</span><span class="sxs-lookup"><span data-stu-id="58da2-110">Obtain a reference to an instance of the <xref:System.Drawing.BufferedGraphicsContext> class.</span></span> <span data-ttu-id="58da2-111">Další informace najdete v tématu [postupy: ruční správa grafiky uložená do vyrovnávací paměti](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="58da2-111">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
2.  <span data-ttu-id="58da2-112">Vytvoření instance <xref:System.Drawing.BufferedGraphics> třída voláním <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> metoda, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="58da2-112">Create an instance of the <xref:System.Drawing.BufferedGraphics> class by calling the <xref:System.Drawing.BufferedGraphicsContext.Allocate%2A> method, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#21)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#21)]  
  
3.  <span data-ttu-id="58da2-113">Kreslení grafiky do vyrovnávací paměti grafiky nastavením <xref:System.Drawing.BufferedGraphics.Graphics%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="58da2-113">Draw graphics to the graphics buffer by setting the <xref:System.Drawing.BufferedGraphics.Graphics%2A> property.</span></span> <span data-ttu-id="58da2-114">Příklad:</span><span class="sxs-lookup"><span data-stu-id="58da2-114">For example:</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#22)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#22)]  
  
4.  <span data-ttu-id="58da2-115">Pokud jste vyplnili všechny kreslení operací do vyrovnávací paměti grafiky, volání <xref:System.Drawing.BufferedGraphics.Render%2A> metoda k vykreslení vyrovnávací paměť, buď kreslicí plochy spojené s této vyrovnávací paměti, nebo na kreslicí plochy, jak je znázorněno v následujícím příkladu kódu.</span><span class="sxs-lookup"><span data-stu-id="58da2-115">When you have completed all of your drawing operations to the graphics buffer, call the <xref:System.Drawing.BufferedGraphics.Render%2A> method to render the buffer, either to the drawing surface associated with that buffer, or to a specified drawing surface, as shown in the following code example.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#23)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#23)]  
  
5.  <span data-ttu-id="58da2-116">Po dokončení vykreslování grafiky volání `Dispose` metodu <xref:System.Drawing.BufferedGraphics> instance uvolnit systémové prostředky.</span><span class="sxs-lookup"><span data-stu-id="58da2-116">After you are finished rendering graphics, call the `Dispose` method on the <xref:System.Drawing.BufferedGraphics> instance to free system resources.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#24)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#24)]  
  
## <a name="see-also"></a><span data-ttu-id="58da2-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="58da2-117">See Also</span></span>  
 <xref:System.Drawing.BufferedGraphicsContext>  
 <xref:System.Drawing.BufferedGraphics>  
 [<span data-ttu-id="58da2-118">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="58da2-118">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="58da2-119">Postupy: Ruční správa grafiky uložené do vyrovnávací paměti</span><span class="sxs-lookup"><span data-stu-id="58da2-119">How to: Manually Manage Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md)
