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
ms.openlocfilehash: 5a18539153c64a5059d8079f6e245115b026bb91
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69950139"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Postupy: Kopírování pixelů pro omezení blikání v modelu Windows Forms
Při animaci jednoduché grafiky mohou uživatelé někdy narazit na blikání nebo jiné nežádoucí vizuální efekty. Jedním ze způsobů, jak tento problém omezit, je použití procesu "BitBlt" na obrázku. BitBlt je přenos "bitového bloku" dat barvy z počátečního obdélníku v pixelech na cílový obdélník pixelů.  
  
 Pomocí model Windows Forms je BitBlt provedeno pomocí <xref:System.Drawing.Graphics.CopyFromScreen%2A> metody <xref:System.Drawing.Graphics> třídy. V parametrech metody zadáte zdroj a cíl (jako body), velikost oblasti, která se má zkopírovat, a objekt Graphics, který se používá k vykreslení nového obrazce.  
  
 V následujícím příkladu je tvar vykreslen ve formuláři v jeho <xref:System.Windows.Forms.Control.Paint> obslužné rutině události. Pak je metoda použita k duplikaci tvaru. <xref:System.Drawing.Graphics.CopyFromScreen%2A>  
  
> [!NOTE]
> Nastavením <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnosti formuláře na nastavíte `true` , aby byl kód založený na grafickém <xref:System.Windows.Forms.Control.Paint> objektu v události dvakrát uložený do vyrovnávací paměti. I když při použití níže uvedeného kódu nebudou discernible žádné zvýšení výkonu, je třeba vzít v úvahu, že při práci s komplexnějším kódem pro manipulaci s grafikou nemusíte mít na paměti něco.  
  
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
 Výše uvedený kód je spuštěn v obslužné rutině <xref:System.Windows.Forms.Control.Paint> události formuláře, aby grafika zůstala při překreslení formuláře zachovaná. V takovém případě Nevolejte metody související s grafikou v <xref:System.Windows.Forms.Form.Load> obslužné rutině události, protože vykreslený obsah nebude překreslen v případě, že dojde ke změně velikosti formuláře nebo jeho skrytí jiným formulářem.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
