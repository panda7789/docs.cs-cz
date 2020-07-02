---
title: 'Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky'
description: Naučte se snižovat blikání grafiky pomocí dvojího ukládání do vyrovnávací paměti pro model Windows Forms a používat ovládací prvky pro řešení problémů blikání přidružených k operacím vykreslování.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing double-buffered flicker
ms.assetid: 91083d3a-653f-4f15-a467-0f37b2aa39d6
ms.openlocfilehash: f7c0425729f8a1a780124621788a1c49e06e0c4e
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85618126"
---
# <a name="how-to-reduce-graphics-flicker-with-double-buffering-for-forms-and-controls"></a><span data-ttu-id="1820f-103">Postupy: Omezení blikání grafiky dvojitým uložením do vyrovnávací paměti pro formuláře a ovládací prvky</span><span class="sxs-lookup"><span data-stu-id="1820f-103">How to: Reduce Graphics Flicker with Double Buffering for Forms and Controls</span></span>
<span data-ttu-id="1820f-104">Dvojité ukládání do vyrovnávací paměti používá vyrovnávací paměť k řešení problémů blikání spojených s více operacemi malování.</span><span class="sxs-lookup"><span data-stu-id="1820f-104">Double buffering uses a memory buffer to address the flicker problems associated with multiple paint operations.</span></span> <span data-ttu-id="1820f-105">Pokud je povoleno dvojité ukládání do vyrovnávací paměti, všechny operace Malování se nejprve vykreslí do vyrovnávací paměti místo kresby na obrazovce.</span><span class="sxs-lookup"><span data-stu-id="1820f-105">When double buffering is enabled, all paint operations are first rendered to a memory buffer instead of the drawing surface on the screen.</span></span> <span data-ttu-id="1820f-106">Po dokončení všech operací Malování se vyrovnávací paměť zkopíruje přímo na kreslicí plochu, která je k ní přidružená.</span><span class="sxs-lookup"><span data-stu-id="1820f-106">After all paint operations are completed, the memory buffer is copied directly to the drawing surface associated with it.</span></span> <span data-ttu-id="1820f-107">Vzhledem k tomu, že se na obrazovce provádí jenom jedna operace grafiky, odstraní se blikání obrázku přidruženého k složitým operacím malování. U většiny aplikací nabízí výchozí dvojité ukládání do vyrovnávací paměti, které poskytuje .NET Framework, nejlepší výsledky.</span><span class="sxs-lookup"><span data-stu-id="1820f-107">Because only one graphics operation is performed on the screen, the image flickering associated with complex painting operations is eliminated.For most applications, the default double buffering provided by the .NET Framework will provide the best results.</span></span> <span data-ttu-id="1820f-108">Standardní ovládací prvky model Windows Forms jsou ve výchozím nastavení dvojitě uloženy do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1820f-108">Standard Windows Forms controls are double buffered by default.</span></span> <span data-ttu-id="1820f-109">Ve formulářích můžete povolit výchozí dvojité ukládání do vyrovnávací paměti a vytvořené ovládací prvky dvěma způsoby.</span><span class="sxs-lookup"><span data-stu-id="1820f-109">You can enable default double buffering in your forms and authored controls in two ways.</span></span> <span data-ttu-id="1820f-110">Můžete buď nastavit <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost na `true` , nebo můžete zavolat <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro nastavení <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznaku na `true` .</span><span class="sxs-lookup"><span data-stu-id="1820f-110">You can either set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`, or you can call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span> <span data-ttu-id="1820f-111">Obě metody povolí výchozí dvojité ukládání do vyrovnávací paměti pro formulář nebo ovládací prvek a poskytuje vykreslování grafiky bez blikání.</span><span class="sxs-lookup"><span data-stu-id="1820f-111">Both methods will enable default double buffering for your form or control and provide flicker-free graphics rendering.</span></span> <span data-ttu-id="1820f-112">Volání <xref:System.Windows.Forms.Control.SetStyle%2A> metody je doporučeno pouze pro vlastní ovládací prvky, pro které jste napsali veškerý kód vykreslování.</span><span class="sxs-lookup"><span data-stu-id="1820f-112">Calling the <xref:System.Windows.Forms.Control.SetStyle%2A> method is recommended only for custom controls for which you have written all the rendering code.</span></span>  
  
 <span data-ttu-id="1820f-113">Pro pokročilejší scénáře s dvojitou vyrovnávací pamětí, jako je například animace nebo Pokročilá správa paměti, můžete implementovat svou vlastní dvojitou logiku ukládání do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="1820f-113">For more advanced double buffering scenarios, such as animation or advanced memory management, you can implement your own double buffering logic.</span></span> <span data-ttu-id="1820f-114">Další informace naleznete v tématu [How to: manualed Graphics Buffered](how-to-manually-manage-buffered-graphics.md).</span><span class="sxs-lookup"><span data-stu-id="1820f-114">For more information, see [How to: Manually Manage Buffered Graphics](how-to-manually-manage-buffered-graphics.md).</span></span>  
  
### <a name="to-reduce-flicker"></a><span data-ttu-id="1820f-115">Snížení blikání</span><span class="sxs-lookup"><span data-stu-id="1820f-115">To reduce flicker</span></span>  
  
- <span data-ttu-id="1820f-116">Nastavte <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost na hodnotu `true` .</span><span class="sxs-lookup"><span data-stu-id="1820f-116">Set the <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#31)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#31)]  
  
 <span data-ttu-id="1820f-117">\-ani</span><span class="sxs-lookup"><span data-stu-id="1820f-117">\- or -</span></span>  
  
- <span data-ttu-id="1820f-118">Zavolejte <xref:System.Windows.Forms.Control.SetStyle%2A> metodu pro nastavení <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> příznaku na `true` .</span><span class="sxs-lookup"><span data-stu-id="1820f-118">Call the <xref:System.Windows.Forms.Control.SetStyle%2A> method to set the <xref:System.Windows.Forms.ControlStyles.OptimizedDoubleBuffer> flag to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/CS/Class1.cs#32)]
     [!code-vb[System.Windows.Forms.LegacyBufferedGraphics#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.LegacyBufferedGraphics/VB/Class1.vb#32)]  
  
## <a name="see-also"></a><span data-ttu-id="1820f-119">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1820f-119">See also</span></span>

- <xref:System.Windows.Forms.Control.DoubleBuffered%2A>
- <xref:System.Windows.Forms.Control.SetStyle%2A>
- [<span data-ttu-id="1820f-120">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="1820f-120">Double Buffered Graphics</span></span>](double-buffered-graphics.md)
- [<span data-ttu-id="1820f-121">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="1820f-121">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
