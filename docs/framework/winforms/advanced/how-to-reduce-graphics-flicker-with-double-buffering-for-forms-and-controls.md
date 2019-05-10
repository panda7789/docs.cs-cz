---
title: 'Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: a719381863d560a5666c7fc1a5e7260a1d4c4823
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64650901"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="2a513-102">Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="2a513-102">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="2a513-103">K vyřešení blikání problémy související s více operací malířského dvojité ukládání do vyrovnávací paměti používá vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2a513-103">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="2a513-104">Pokud dvojité ukládání do vyrovnávací paměti je povolená, všechny operace Malování vykresleny nejprve do vyrovnávací paměti namísto na návrhovém povrchu na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="2a513-104">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="2a513-105">Po dokončení všechny operace Malování vyrovnávací paměť je zkopírován přímo do na návrhovém povrchu s ním spojená.</span><span class="sxs-lookup"><span data-stu-id="2a513-105">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="2a513-106">Protože pouze jediného grafického operace se provádí na obrazovce, image blikání spojené s operacemi komplexní Malování se odstraní. Pro většinu aplikací, výchozí dvojité ukládání do vyrovnávací paměti poskytované [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] poskytne nejlepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="2a513-106">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] will provide the best results.</span></span> <span data-ttu-id="2a513-107">Standardní ovládací prvky Windows Forms jsou dvojité vyrovnávací paměti ve výchozím nastavení.</span><span class="sxs-lookup"><span data-stu-id="2a513-107">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="2a513-108">Můžete povolit výchozí dvojité ukládání do vyrovnávací paměti do svých formulářů a je také autorem ovládací prvky dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="2a513-108">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="2a513-109">Můžete buď nastaven <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true`, nebo můžete volat <xref:System.Windows.Forms.Control.SetStyle%2A> metody nastavte <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznak, který `true`.</span><span class="sxs-lookup"><span data-stu-id="2a513-109">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="2a513-110">Obě metody povolí výchozí dvojité ukládání do vyrovnávací paměti pro formuláře nebo ovládacího prvku a zadejte vykreslování bez blikání grafiky.</span><span class="sxs-lookup"><span data-stu-id="2a513-110">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="2a513-111">Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metoda se doporučuje jenom pro vlastní ovládací prvky, pro které jste napsali v kódu vykreslování.</span><span class="sxs-lookup"><span data-stu-id="2a513-111">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="2a513-112">Pro pokročilejší dvojité vyrovnávací paměti scénáře, jako je například animace nebo rozšířené paměti pro správu můžete implementovat vlastní logiku dvojité vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="2a513-112">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="2a513-113">Další informace najdete v tématu [jak: Ruční správa grafiky uložené do vyrovnávací paměti](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="2a513-113">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="2a513-114">Abyste snížili blikání</span><span class="sxs-lookup"><span data-stu-id="2a513-114">To reduce flicker</span></span>  
  
- <span data-ttu-id="2a513-115">Nastavte <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="2a513-115">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="2a513-116">\- nebo –</span><span class="sxs-lookup"><span data-stu-id="2a513-116">\- or -</span></span>  
  
- <span data-ttu-id="2a513-117">Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metody nastavte <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznak `true`.</span><span class="sxs-lookup"><span data-stu-id="2a513-117">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="2a513-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2a513-118">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="2a513-119">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="2a513-119">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="2a513-120">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="2a513-120">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
