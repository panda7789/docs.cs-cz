---
title: 'Postupy: kopírování pixelů pro redukci blikání'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- bitblt
- graphics [Windows Forms], copying
- flicker [Windows Forms], reducing in Windows Forms
- graphics [Windows Forms], reducing flicker
- pixels [Windows Forms], copying
- flicker
- bit-block transfer
ms.assetid: 33b76910-13a3-4521-be98-5c097341ae3b
ms.openlocfilehash: 299041e7038d5bd5b9824d668b3f47d842030ac7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746485"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="4f441-102">Postupy: Kopírování pixelů pro omezení blikání v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f441-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="4f441-103">Při animaci jednoduché grafiky mohou uživatelé někdy narazit na blikání nebo jiné nežádoucí vizuální efekty.</span><span class="sxs-lookup"><span data-stu-id="4f441-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="4f441-104">Jedním ze způsobů, jak tento problém omezit, je použití procesu "BitBlt" na obrázku.</span><span class="sxs-lookup"><span data-stu-id="4f441-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="4f441-105">BitBlt je přenos "bitového bloku" dat barvy z počátečního obdélníku v pixelech na cílový obdélník pixelů.</span><span class="sxs-lookup"><span data-stu-id="4f441-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="4f441-106">Pomocí model Windows Forms je BitBlt provedeno pomocí metody <xref:System.Drawing.Graphics.CopyFromScreen%2A> třídy <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="4f441-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="4f441-107">V parametrech metody zadáte zdroj a cíl (jako body), velikost oblasti, která se má zkopírovat, a objekt Graphics, který se používá k vykreslení nového obrazce.</span><span class="sxs-lookup"><span data-stu-id="4f441-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="4f441-108">V následujícím příkladu je tvar vykreslen ve formuláři v obslužné rutině události <xref:System.Windows.Forms.Control.Paint>.</span><span class="sxs-lookup"><span data-stu-id="4f441-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="4f441-109">Pak je použita metoda <xref:System.Drawing.Graphics.CopyFromScreen%2A> k duplikaci tvaru.</span><span class="sxs-lookup"><span data-stu-id="4f441-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f441-110">Když nastavíte vlastnost <xref:System.Windows.Forms.Control.DoubleBuffered%2A> formuláře na `true`, bude se u grafického kódu v události <xref:System.Windows.Forms.Control.Paint> pokládat dvojitě do vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4f441-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="4f441-111">I když při použití níže uvedeného kódu nebudou discernible žádné zvýšení výkonu, je třeba vzít v úvahu, že při práci s komplexnějším kódem pro manipulaci s grafikou nemusíte mít na paměti něco.</span><span class="sxs-lookup"><span data-stu-id="4f441-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f441-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f441-112">Example</span></span>  
  
```vb  
Private Sub Form1_Paint(ByVal sender As Object, ByVal e As _  
    System.Windows.Forms.PaintEventArgs) Handles MyBase.Paint  
    ' Draw a circle with a bar on top.  
        e.Graphics.FillEllipse(Brushes.DarkBlue, New Rectangle _  
             (10, 10, 60, 60))  
        e.Graphics.FillRectangle(Brushes.Khaki, New Rectangle _  
             (20, 30, 60, 10))  
    ' Copy the graphic to a new location.  
        e.Graphics.CopyFromScreen(New Point(10, 10), New Point _  
             (100, 100), New Size(70, 70))  
End Sub  
```  
  
```csharp  
private void Form1_Paint(System.Object sender,  
    System.Windows.Forms.PaintEventArgs e)  
        {  
        e.Graphics.FillEllipse(Brushes.DarkBlue, new  
            Rectangle(10,10,60,60));  
        e.Graphics.FillRectangle(Brushes.Khaki, new  
            Rectangle(20,30,60,10));  
        e.Graphics.CopyFromScreen(new Point(10, 10), new Point(100, 100),   
            new Size(70, 70));  
}  
```  
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f441-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4f441-113">Compiling the Code</span></span>  
 <span data-ttu-id="4f441-114">Výše uvedený kód je spuštěn v obslužné rutině události <xref:System.Windows.Forms.Control.Paint> formuláře, aby grafika zůstala při překreslení formuláře zachovaná.</span><span class="sxs-lookup"><span data-stu-id="4f441-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="4f441-115">V takovém případě Nevolejte metody související s grafikou v obslužné rutině <xref:System.Windows.Forms.Form.Load> události, protože vykreslený obsah nebude překreslen, pokud je tvar změněna na velikost nebo zakrytý jiným formulářem.</span><span class="sxs-lookup"><span data-stu-id="4f441-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f441-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f441-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4f441-117">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f441-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="4f441-118">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="4f441-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
