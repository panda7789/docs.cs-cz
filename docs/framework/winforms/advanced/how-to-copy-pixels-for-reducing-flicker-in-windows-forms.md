---
title: 'Postup: Kopírování pixelů pro snížení blikání'
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
ms.openlocfilehash: a25295532d7123d92bcacc6828d3e8cfcc839d6e
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182586"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="4f05b-102">Postupy: Kopírování pixelů pro omezení blikání v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f05b-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="4f05b-103">Při animaci jednoduché grafiky se uživatelé mohou někdy setkat s blikáním nebo jinými nežádoucími vizuálními efekty.</span><span class="sxs-lookup"><span data-stu-id="4f05b-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="4f05b-104">Jedním ze způsobů, jak omezit tento problém, je použití procesu "bitblt" na obrázku.</span><span class="sxs-lookup"><span data-stu-id="4f05b-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="4f05b-105">Bitblt je "přenos bitových bloků" barevných dat z původního obdélníku obrazových bodů do cílového obdélníku obrazových bodů.</span><span class="sxs-lookup"><span data-stu-id="4f05b-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="4f05b-106">S Windows Forms bitblt se <xref:System.Drawing.Graphics.CopyFromScreen%2A> provádí pomocí <xref:System.Drawing.Graphics> metody třídy.</span><span class="sxs-lookup"><span data-stu-id="4f05b-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="4f05b-107">V parametrech metody určíte zdroj a cíl (jako body), velikost oblasti, která má být zkopírována, a grafický objekt použitý k nakreslení nového tvaru.</span><span class="sxs-lookup"><span data-stu-id="4f05b-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="4f05b-108">V níže uvedeném příkladu je obrazec <xref:System.Windows.Forms.Control.Paint> nakreslena na formuláři v jeho obslužné rutině události.</span><span class="sxs-lookup"><span data-stu-id="4f05b-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="4f05b-109">Poté se <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda použije k duplikování obrazce.</span><span class="sxs-lookup"><span data-stu-id="4f05b-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="4f05b-110">Nastavení <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnosti formuláře `true` bude grafický kód v <xref:System.Windows.Forms.Control.Paint> události dvojité vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="4f05b-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="4f05b-111">I když to nebude mít žádné zřetelné zvýšení výkonu při použití níže uvedeného kódu, je něco, co je třeba mít na paměti při práci s složitější kód manipulace s grafikou.</span><span class="sxs-lookup"><span data-stu-id="4f05b-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4f05b-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="4f05b-112">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="4f05b-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="4f05b-113">Compiling the Code</span></span>  
 <span data-ttu-id="4f05b-114">Výše uvedený kód je spuštěn <xref:System.Windows.Forms.Control.Paint> v obslužné rutině události formuláře tak, aby grafika přetrvávala při překreslování formuláře.</span><span class="sxs-lookup"><span data-stu-id="4f05b-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="4f05b-115">Jako takové nevolejte metody související s <xref:System.Windows.Forms.Form.Load> grafikou v obslužné rutině události, protože nakreslený obsah nebude překreslen, pokud je velikost formuláře nebo zakrytí jiným formulářem.</span><span class="sxs-lookup"><span data-stu-id="4f05b-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="4f05b-116">Viz také</span><span class="sxs-lookup"><span data-stu-id="4f05b-116">See also</span></span>

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="4f05b-117">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="4f05b-117">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="4f05b-118">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="4f05b-118">Using a Pen to Draw Lines and Shapes</span></span>](using-a-pen-to-draw-lines-and-shapes.md)
