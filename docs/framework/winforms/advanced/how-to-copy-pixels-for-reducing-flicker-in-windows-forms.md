---
title: 'Postupy: Kopírování pixelů pro omezení blikání v rozhraní Windows Forms'
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
ms.openlocfilehash: 65428132c885191b62c3b4a76c8937bf8f3f6732
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33522041"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Postupy: Kopírování pixelů pro omezení blikání v rozhraní Windows Forms
Při animaci jednoduchý obrázek uživatelů může někdy dojít blikání nebo jiných nežádoucího vizuálních efektů. Jeden způsob, jak omezit tento problém je použití procesu "přenos bitových bloků" na na obrázku. Přenos bitových bloků je "bitového bloku přenos" Barva dat z počátku obdélníku pixelů na cílovém obdélník pixelů.  
  
 S Windows Forms přenos bitových bloků se provádí pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metodu <xref:System.Drawing.Graphics> třída. Parametry metody zadejte zdrojový a cílový (jako body), velikost oblasti, které se mají zkopírovat a grafiky objekt použitý k vykreslení nový tvar.  
  
 V následujícím příkladu se nevykreslí obrazce na formuláři v jeho <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Potom, <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda se používá k duplicitní tvaru.  
  
> [!NOTE]
>  Nastavení formuláře <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost, která má `true` bude na základě grafiky kód <xref:System.Windows.Forms.Control.Paint> událostí být dvojitou vyrovnávací pamětí. Pokud to nebude mít žádné zvýšení výkonu discernable při použití kódu níže, je něco třeba vzít v úvahu při práci s kódem složitější grafiky manipulaci.  
  
## <a name="example"></a>Příklad  
  
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
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Výše uvedený kód běží v formuláře <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události tak, aby grafiky zachována, když bude překreslen formuláře. Jako takový Nevolejte související grafika metody <xref:System.Windows.Forms.Form.Load> obslužné rutiny události, protože vykresleného obsah nebude překreslen, pokud formuláře je po změně velikosti nebo po jiného formuláře skryt.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Drawing.CopyPixelOperation>  
 <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>  
 [Grafika a kreslení v modelu Windows Forms](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [Kreslení čar a obrazců pomocí pera](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)
