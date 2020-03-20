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
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Postupy: Kopírování pixelů pro omezení blikání v rozhraní Windows Forms
Při animaci jednoduché grafiky se uživatelé mohou někdy setkat s blikáním nebo jinými nežádoucími vizuálními efekty. Jedním ze způsobů, jak omezit tento problém, je použití procesu "bitblt" na obrázku. Bitblt je "přenos bitových bloků" barevných dat z původního obdélníku obrazových bodů do cílového obdélníku obrazových bodů.  
  
 S Windows Forms bitblt se <xref:System.Drawing.Graphics.CopyFromScreen%2A> provádí pomocí <xref:System.Drawing.Graphics> metody třídy. V parametrech metody určíte zdroj a cíl (jako body), velikost oblasti, která má být zkopírována, a grafický objekt použitý k nakreslení nového tvaru.  
  
 V níže uvedeném příkladu je obrazec <xref:System.Windows.Forms.Control.Paint> nakreslena na formuláři v jeho obslužné rutině události. Poté se <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda použije k duplikování obrazce.  
  
> [!NOTE]
> Nastavení <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnosti formuláře `true` bude grafický kód v <xref:System.Windows.Forms.Control.Paint> události dvojité vyrovnávací paměti. I když to nebude mít žádné zřetelné zvýšení výkonu při použití níže uvedeného kódu, je něco, co je třeba mít na paměti při práci s složitější kód manipulace s grafikou.  
  
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
 Výše uvedený kód je spuštěn <xref:System.Windows.Forms.Control.Paint> v obslužné rutině události formuláře tak, aby grafika přetrvávala při překreslování formuláře. Jako takové nevolejte metody související s <xref:System.Windows.Forms.Form.Load> grafikou v obslužné rutině události, protože nakreslený obsah nebude překreslen, pokud je velikost formuláře nebo zakrytí jiným formulářem.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
