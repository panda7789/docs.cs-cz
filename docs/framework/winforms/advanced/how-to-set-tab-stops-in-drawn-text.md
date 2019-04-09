---
title: 'Postupy: Nastavení zarážek v kresleném textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [Windows Forms], drawing with tab stops
- tabs [Windows Forms], drawn text
ms.assetid: 64878f98-39ba-4303-b63f-0859ab682eeb
ms.openlocfilehash: 68dbebfc4fab773fe749f9443d0c61883099d2ab
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59197487"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="1f251-102">Postupy: Nastavení zarážek v kresleném textu</span><span class="sxs-lookup"><span data-stu-id="1f251-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="1f251-103">Tabulátoru pro text můžete nastavit pomocí volání <xref:System.Drawing.StringFormat.SetTabStops%2A> metodu <xref:System.Drawing.StringFormat> objektu a následné předání, který <xref:System.Drawing.StringFormat> objektu <xref:System.Drawing.Graphics.DrawString%2A> metodu <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="1f251-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="1f251-104"><xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> Fakturuje se nepodporuje přidání zarážky kresleném textu, i když rozšiřujete existující kartu přestane používat <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> příznak.</span><span class="sxs-lookup"><span data-stu-id="1f251-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1f251-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f251-105">Example</span></span>  
 <span data-ttu-id="1f251-106">Následující příklad nastaví zarážek na 150, 250 a 350.</span><span class="sxs-lookup"><span data-stu-id="1f251-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="1f251-107">Potom kód zobrazí seznam s kartami názvy a skóre v testech.</span><span class="sxs-lookup"><span data-stu-id="1f251-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="1f251-108">Následující obrázek znázorňuje následující text:</span><span class="sxs-lookup"><span data-stu-id="1f251-108">The following illustration shows the tabbed text:</span></span>  
  
 ![Snímek obrazovky zobrazující seznam s kartami názvy a skóre.](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 <span data-ttu-id="1f251-110">Následující kód předá dva argumenty <xref:System.Drawing.StringFormat.SetTabStops%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="1f251-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="1f251-111">Druhý argument je pole, která obsahuje kartu posunů.</span><span class="sxs-lookup"><span data-stu-id="1f251-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="1f251-112">První argument předaný metodě <xref:System.Drawing.StringFormat.SetTabStops%2A> je 0, což znamená, že první posunutí v poli se měří z pozice 0, je levý okraj ohraničující obdélník.</span><span class="sxs-lookup"><span data-stu-id="1f251-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1f251-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1f251-113">Compiling the Code</span></span>  
  
-   <span data-ttu-id="1f251-114">V předchozím příkladu je určený k použití pomocí Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, což je parametr <xref:System.Windows.Forms.PaintEventHandler>.</span><span class="sxs-lookup"><span data-stu-id="1f251-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1f251-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f251-115">See also</span></span>

- [<span data-ttu-id="1f251-116">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="1f251-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="1f251-117">Postupy: Kreslení textu pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="1f251-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
