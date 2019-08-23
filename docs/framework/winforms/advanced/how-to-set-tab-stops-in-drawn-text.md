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
ms.openlocfilehash: 8821f6170b8ba588e3197ef54eab14c2719a6cc3
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69947823"
---
# <a name="how-to-set-tab-stops-in-drawn-text"></a><span data-ttu-id="94cf2-102">Postupy: Nastavení zarážek v kresleném textu</span><span class="sxs-lookup"><span data-stu-id="94cf2-102">How to: Set Tab Stops in Drawn Text</span></span>
<span data-ttu-id="94cf2-103">Můžete nastavit zarážky tabulátoru pro text voláním <xref:System.Drawing.StringFormat.SetTabStops%2A> metody <xref:System.Drawing.StringFormat> objektu a následným <xref:System.Drawing.Graphics.DrawString%2A> předáním tohoto <xref:System.Drawing.StringFormat> objektu metodě <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="94cf2-103">You can set tab stops for text by calling the <xref:System.Drawing.StringFormat.SetTabStops%2A> method of a <xref:System.Drawing.StringFormat> object and then passing that <xref:System.Drawing.StringFormat> object to the <xref:System.Drawing.Graphics.DrawString%2A> method of the <xref:System.Drawing.Graphics> class.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="94cf2-104">Nepodporuje přidání zarážek tabulátoru do vykresleného textu, i když můžete rozbalit existující zarážku tabulátoru <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> pomocí příznaku. <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType></span><span class="sxs-lookup"><span data-stu-id="94cf2-104">The <xref:System.Windows.Forms.TextRenderer?displayProperty=nameWithType> does not support adding tab stops to drawn text, although you can expand existing tab stops using the <xref:System.Windows.Forms.TextFormatFlags.ExpandTabs?displayProperty=nameWithType> flag.</span></span>  
  
## <a name="example"></a><span data-ttu-id="94cf2-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="94cf2-105">Example</span></span>  
 <span data-ttu-id="94cf2-106">Následující příklad nastaví zarážky tabulátoru na 150, 250 a 350.</span><span class="sxs-lookup"><span data-stu-id="94cf2-106">The following example sets tab stops at 150, 250, and 350.</span></span> <span data-ttu-id="94cf2-107">Kód pak zobrazuje seznam názvů a hodnocení testů s kartami.</span><span class="sxs-lookup"><span data-stu-id="94cf2-107">Then, the code displays a tabbed list of names and test scores.</span></span>  
  
 <span data-ttu-id="94cf2-108">Následující ilustrace znázorňuje text s kartami:</span><span class="sxs-lookup"><span data-stu-id="94cf2-108">The following illustration shows the tabbed text:</span></span>  
  
 ![Snímek obrazovky zobrazující seznam názvů a skóre s kartami](./media/how-to-set-tab-stops-in-drawn-text/tab-list-names-test-scores.png)  
  
 <span data-ttu-id="94cf2-110">Následující kód předá do <xref:System.Drawing.StringFormat.SetTabStops%2A> metody dva argumenty.</span><span class="sxs-lookup"><span data-stu-id="94cf2-110">The following code passes two arguments to the <xref:System.Drawing.StringFormat.SetTabStops%2A> method.</span></span> <span data-ttu-id="94cf2-111">Druhým argumentem je pole, které obsahuje posuny tabulátoru.</span><span class="sxs-lookup"><span data-stu-id="94cf2-111">The second argument is an array that contains tab offsets.</span></span> <span data-ttu-id="94cf2-112">První argument předaný do <xref:System.Drawing.StringFormat.SetTabStops%2A> je 0, což znamená, že první posun v poli je měřen od pozice 0, levého okraje ohraničovacího rámečku.</span><span class="sxs-lookup"><span data-stu-id="94cf2-112">The first argument passed to <xref:System.Drawing.StringFormat.SetTabStops%2A> is 0, which indicates that the first offset in the array is measured from position 0, the left edge of the bounding rectangle.</span></span>  
  
 [!code-csharp[System.Drawing.FontsAndText#41](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.FontsAndText/CS/Class1.cs#41)]
 [!code-vb[System.Drawing.FontsAndText#41](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.FontsAndText/VB/Class1.vb#41)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="94cf2-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="94cf2-113">Compiling the Code</span></span>  
  
- <span data-ttu-id="94cf2-114">Předchozí příklad je navržen pro použití s model Windows Forms a vyžaduje <xref:System.Windows.Forms.PaintEventArgs> `e`, <xref:System.Windows.Forms.PaintEventHandler>což je parametr.</span><span class="sxs-lookup"><span data-stu-id="94cf2-114">The preceding example is designed for use with Windows Forms, and it requires <xref:System.Windows.Forms.PaintEventArgs> `e`, which is a parameter of <xref:System.Windows.Forms.PaintEventHandler>.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94cf2-115">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94cf2-115">See also</span></span>

- [<span data-ttu-id="94cf2-116">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="94cf2-116">Using Fonts and Text</span></span>](using-fonts-and-text.md)
- [<span data-ttu-id="94cf2-117">Postupy: Nakreslit text pomocí GDI</span><span class="sxs-lookup"><span data-stu-id="94cf2-117">How to: Draw Text with GDI</span></span>](how-to-draw-text-with-gdi.md)
