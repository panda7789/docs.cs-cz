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
ms.openlocfilehash: e3d1c2b681e98dc7c45467683924dd4022eb377e
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61937745"
---
# <a name="how-to-copy-pixels-for-reducing-flicker-in-windows-forms"></a>Postupy: Kopírování pixelů pro omezení blikání v modelu Windows Forms
Při animaci jednoduchý obrázek uživatele může někdy dojít blikání nebo jiné nežádoucí vizuálních efektů. Jeden způsob, jak omezit tento problém je použití procesu "přenos bitových bloků" na obrázku. Přenos bitových bloků je "bitového bloku přenos" barvy dat ze původu obdélník pixelů do cílového obdélníku v pixelech.  
  
 Pomocí Windows Forms, přenos bitových bloků využívá se při něm <xref:System.Drawing.Graphics.CopyFromScreen%2A> metodu <xref:System.Drawing.Graphics> třídy. V parametrech metody je třeba zadat zdroj a cíl (jako body), velikost oblasti, které se mají zkopírovat a grafiky objekt použitý k vykreslení nový tvar.  
  
 V následujícím příkladu je vykreslen obrazec na formulář v nástrojích pro jeho <xref:System.Windows.Forms.Control.Paint> obslužné rutiny události. Pak, bude <xref:System.Drawing.Graphics.CopyFromScreen%2A> metoda se používá k duplicitní tvaru.  
  
> [!NOTE]
>  Nastavení formuláře <xref:System.Windows.Forms.Control.DoubleBuffered%2A> vlastnost `true` způsobí, že kód založený na grafickém v <xref:System.Windows.Forms.Control.Paint> událost být dvojitou vyrovnávací pamětí. Při použití níže uvedeného kódu to nebude mít žádné zvýšení výkonu a jasně, je něco, co vzít v úvahu při práci s složitější grafiky manipulace s kódem.  
  
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
 Výše uvedený kód běží v formuláře <xref:System.Windows.Forms.Control.Paint> obslužná rutina události tak, aby grafiky zachovat při překreslení formuláře. V důsledku toho nebude volat metody související grafiky <xref:System.Windows.Forms.Form.Load> obslužná rutina události, protože vykreslený obsah nebude překreslení, pokud je velikost nebo zakryto jiný formulář. formuláře.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Drawing.CopyPixelOperation>
- <xref:System.Drawing.Graphics.FillRectangle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.Control.OnPaint%2A?displayProperty=nameWithType>
- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Kreslení čar a obrazců pomocí pera](using-a-pen-to-draw-lines-and-shapes.md)
