---
title: 'Postupy: Kopírování pixelů pro omezení blikání v modelu Windows Forms'
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
ms.openlocfilehash: cdcb64588f91ece02f1e7f446d4020d68262c93d
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54559447"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a><span data-ttu-id="d7549-102">Postupy: Kopírování pixelů pro omezení blikání v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7549-102">How to: Copy Pixels for Reducing Flicker in Windows Forms</span></span>
<span data-ttu-id="d7549-103">Při animaci jednoduchý obrázek uživatele může někdy dojít blikání nebo jiné nežádoucí vizuálních efektů.</span><span class="sxs-lookup"><span data-stu-id="d7549-103">When you animate a simple graphic, users can sometimes encounter flicker or other undesirable visual effects.</span></span> <span data-ttu-id="d7549-104">Jeden způsob, jak omezit tento problém je použití procesu "přenos bitových bloků" na obrázku.</span><span class="sxs-lookup"><span data-stu-id="d7549-104">One way to limit this problem is to use a "bitblt" process on the graphic.</span></span> <span data-ttu-id="d7549-105">Přenos bitových bloků je "bitového bloku přenos" barvy dat ze původu obdélník pixelů do cílového obdélníku v pixelech.</span><span class="sxs-lookup"><span data-stu-id="d7549-105">Bitblt is the "bit-block transfer" of the color data from an origin rectangle of pixels to a destination rectangle of pixels.</span></span>  
  
 <span data-ttu-id="d7549-106">Pomocí Windows Forms, přenos bitových bloků využívá se při něm <xref:System.Drawing.Graphics.CopyFromScreen%2A> metodu <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="d7549-106">With Windows Forms, bitblt is accomplished using the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="d7549-107">V parametrech metody je třeba zadat zdroj a cíl (jako body), velikost oblasti, které se mají zkopírovat a grafiky objekt použitý k vykreslení nový tvar.</span><span class="sxs-lookup"><span data-stu-id="d7549-107">In the parameters of the method, you specify the source and destination (as points), the size of the area to be copied, and the graphics object used to draw the new shape.</span></span>  
  
 <span data-ttu-id="d7549-108">V následujícím příkladu je vykreslen obrazec na formulář v nástrojích pro jeho <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="d7549-108">In the example below, a shape is drawn on the form in its <xref:System.Windows.Forms.Control.Paint> event handler.</span></span> <span data-ttu-id="d7549-109">Pak, bude <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda se používá k duplicitní tvaru.</span><span class="sxs-lookup"><span data-stu-id="d7549-109">Then, the <xref:System.Drawing.Graphics.CopyFromScreen%2A> method is used to duplicate the shape.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="d7549-110">Nastavení formuláře <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true` způsobí, že kód založený na grafickém v <xref:System.Windows.Forms.Control.Paint> událost být dvojitou vyrovnávací pamětí.</span><span class="sxs-lookup"><span data-stu-id="d7549-110">Setting the form's <xref:System.Windows.Forms.Control.DoubleBuffered%2A> property to `true` will make graphics-based code in the <xref:System.Windows.Forms.Control.Paint> event be double-buffered.</span></span> <span data-ttu-id="d7549-111">Při použití níže uvedeného kódu to nebude mít žádné zvýšení výkonu a jasně, je něco, co vzít v úvahu při práci s složitější grafiky manipulace s kódem.</span><span class="sxs-lookup"><span data-stu-id="d7549-111">While this will not have any discernible performance gains when using the code below, it is something to keep in mind when working with more complex graphics-manipulation code.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d7549-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="d7549-112">Example</span></span>  
  
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
  
## <a name="compiling-the-code"></a><span data-ttu-id="d7549-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d7549-113">Compiling the Code</span></span>  
 <span data-ttu-id="d7549-114">Výše uvedený kód běží v formuláře <xref:System.Windows.Forms.Control.Paint> obslužná rutina události tak, aby grafiky zachovat při překreslení formuláře.</span><span class="sxs-lookup"><span data-stu-id="d7549-114">The code above is run in the form's <xref:System.Windows.Forms.Control.Paint> event handler so that the graphics persist when the form is redrawn.</span></span> <span data-ttu-id="d7549-115">V důsledku toho nebude volat metody související grafiky <xref:System.Windows.Forms.Form.Load> obslužná rutina události, protože vykreslený obsah nebude překreslení, pokud je velikost nebo zakryto jiný formulář. formuláře.</span><span class="sxs-lookup"><span data-stu-id="d7549-115">As such, do not call graphics-related methods in the <xref:System.Windows.Forms.Form.Load> event handler, because the drawn content will not be redrawn if the form is resized or obscured by another form.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d7549-116">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d7549-116">See also</span></span>
- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [<span data-ttu-id="d7549-117">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="d7549-117">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="d7549-118">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="d7549-118">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
