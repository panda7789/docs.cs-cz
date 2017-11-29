---
title: "Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky"
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
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6d1b22babcc653f999ff500a5e52a12616fc1ae4
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="24fdf-102">Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="24fdf-102">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="24fdf-103">Chcete-li vyřešit blikání problémy spojené s více operací Malování dvojité ukládání do vyrovnávací paměti používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="24fdf-103">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="24fdf-104">Pokud dvojité ukládání do vyrovnávací paměti je povoleno, všechny operace Malování vykresleny nejprve do vyrovnávací paměti místo kreslicí plochy na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="24fdf-104">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="24fdf-105">Po dokončení všech operací Malování vyrovnávací paměť je zkopírovat přímo do kreslicí plochy s ním spojená.</span><span class="sxs-lookup"><span data-stu-id="24fdf-105">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="24fdf-106">Vzhledem k tomu, že pouze jeden grafické operace na obrazovce, blikání bitové kopie přidružený komplexní vykreslovací operace odstranění. Pro většinu aplikací, výchozí dvojité ukládání do vyrovnávací paměti zajišťuje [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] bude poskytovat nejlepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="24fdf-106">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] will provide the best results.</span></span> <span data-ttu-id="24fdf-107">Standardní ovládací prvky Windows Forms jsou dvojité vyrovnávací paměti ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="24fdf-107">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="24fdf-108">Můžete povolit výchozí dvojité ukládání do vyrovnávací paměti do svých formulářů a vytvořené ovládací prvky dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="24fdf-108">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="24fdf-109">Můžete buď sadu <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true`, nebo můžete volat <xref:System.Windows.Forms.Control.SetStyle%2A> metodu a nastavit <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznak, který `true`.</span><span class="sxs-lookup"><span data-stu-id="24fdf-109">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="24fdf-110">Obě metody povolí, výchozí dvojité ukládání do vyrovnávací paměti pro formuláře nebo ovládacího prvku a poskytují blikání grafiky vykreslování.</span><span class="sxs-lookup"><span data-stu-id="24fdf-110">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="24fdf-111">Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metoda se doporučuje jenom pro vlastní ovládací prvky, pro které jste napsali všechny kód vykreslování.</span><span class="sxs-lookup"><span data-stu-id="24fdf-111">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="24fdf-112">Pro pokročilejší dvojité vyrovnávací paměti scénáře, jako je například animace nebo Správa rozšířené paměti můžete implementovat vlastní logiky dvojité vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="24fdf-112">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="24fdf-113">Další informace najdete v tématu [postupy: ruční správa grafiky uložená do vyrovnávací paměti](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="24fdf-113">For more information, see [How to: Manually Manage Buffered Graphics](../../../../docs/framework/winforms/advanced/how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="24fdf-114">Ke snížení blikání</span><span class="sxs-lookup"><span data-stu-id="24fdf-114">To reduce flicker</span></span>  
  
-   <span data-ttu-id="24fdf-115">Nastavte <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="24fdf-115">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="24fdf-116">\-nebo –</span><span class="sxs-lookup"><span data-stu-id="24fdf-116">\- or -</span></span>  
  
-   <span data-ttu-id="24fdf-117">Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metodu a nastavit <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznak, který `true`.</span><span class="sxs-lookup"><span data-stu-id="24fdf-117">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="24fdf-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="24fdf-118">See Also</span></span>  
 <xref:System.Windows.Forms.Control.DoubleBuffered%2A>  
 <xref:System.Windows.Forms.Control.SetStyle%2A>  
 [<span data-ttu-id="24fdf-119">Dvojité grafiky uložené do vyrovnávací</span><span class="sxs-lookup"><span data-stu-id="24fdf-119">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 [<span data-ttu-id="24fdf-120">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="24fdf-120">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
