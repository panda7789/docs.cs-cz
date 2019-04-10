---
title: Správa stavu grafického objektu
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
ms.openlocfilehash: 8fc92bf84def50bed54a054ae634a8a08c8835c2
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59212450"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Správa stavu grafického objektu
<xref:System.Drawing.Graphics> Třída je srdcem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]. Chcete-li nakreslit nic, můžete získat <xref:System.Drawing.Graphics> objektu, vlastností a volat jeho metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>a podobně).  
  
 Následující příklad volá <xref:System.Drawing.Graphics.DrawRectangle%2A> metodu <xref:System.Drawing.Graphics> objektu. První argument předaný metodě <xref:System.Drawing.Graphics.DrawRectangle%2A> je metoda <xref:System.Drawing.Pen> objektu.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue) ' Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  // Opaque blue  
graphics.DrawRectangle(pen, 10, 10, 200, 100);  
```  
  
## <a name="graphics-state"></a>Stav grafiky  
 A <xref:System.Drawing.Graphics> objekt více než zadejte výkresu metody, jako třeba <xref:System.Drawing.Graphics.DrawLine%2A> a <xref:System.Drawing.Graphics.DrawRectangle%2A>. A <xref:System.Drawing.Graphics> objekt také uchovává stav grafiky, které je možné rozdělit do těchto kategorií:  
  
-   Nastavení kvality  
  
-   Transformace  
  
-   Oblast ořezu  
  
### <a name="quality-settings"></a>Nastavení kvality  
 A <xref:System.Drawing.Graphics> objekt má několik vlastností, které ovlivňují kvality položky, které jsou zpracovány. Například můžete nastavit <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnosti k určení typu (pokud existuje) antialiasingu použitý pro text. Další vlastnosti, které ovlivňují kvalitu jsou <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, a <xref:System.Drawing.Graphics.InterpolationMode%2A>.  
  
 Následující příklad nakreslí dva symbol tří teček, jednu s nastavit na režim vyhlazování <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> a jeden u nastavit na režim vyhlazování <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Blue)  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias  
graphics.DrawEllipse(pen, 0, 0, 200, 100)  
graphics.SmoothingMode = SmoothingMode.HighSpeed  
graphics.DrawEllipse(pen, 0, 150, 200, 100)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Blue);  
  
graphics.SmoothingMode = SmoothingMode.AntiAlias;  
graphics.DrawEllipse(pen, 0, 0, 200, 100);  
graphics.SmoothingMode = SmoothingMode.HighSpeed;  
graphics.DrawEllipse(pen, 0, 150, 200, 100);  
```  
  
### <a name="transformations"></a>Transformace  
 A <xref:System.Drawing.Graphics> objektu udržuje dvě transformace (světa a stránky), které se použijí u všech položek, které vykreslené <xref:System.Drawing.Graphics> objektu. Žádné afinní transformace mohou být uloženy v Světové transformace. Afinní transformace patří škálování, otáčení, odráží, zkreslení a překladu. Transformace stránky lze použít pro škálování a pro změnu jednotky (například pixelů cm). Další informace najdete v tématu [systém souřadnic a transformace](coordinate-systems-and-transformations.md).  
  
 Následující příklad nastaví transformace světa a stránka <xref:System.Drawing.Graphics> objektu. Světové transformace je nastavena na otočení kolem osy 30stupňů. Transformace stránky nastavená tak, aby souřadnice předat druhé <xref:System.Drawing.Graphics.DrawEllipse%2A> , bude zacházeno jako milimetrech místo pixelů. Kód volá dva identické <xref:System.Drawing.Graphics.DrawEllipse%2A> metody. Světové transformace se použije pro první <xref:System.Drawing.Graphics.DrawEllipse%2A> volání a obě transformace (světa a stránky) se použijí k druhému <xref:System.Drawing.Graphics.DrawEllipse%2A> volání.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
Dim pen As New Pen(Color.Red)  
  
graphics.ResetTransform()  
graphics.RotateTransform(30) ' world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
graphics.PageUnit = GraphicsUnit.Millimeter ' page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
Pen pen = new Pen(Color.Red);   
  
graphics.ResetTransform();  
graphics.RotateTransform(30);                    // world transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
graphics.PageUnit = GraphicsUnit.Millimeter;     // page transformation  
graphics.DrawEllipse(pen, 0, 0, 100, 50);  
```  
  
 Následující obrázek znázorňuje dvě symbol tří teček. Všimněte si, otočení kolem osy z 30stupňů o původu souřadnicovém systému (levého horního rohu oblasti klienta), ne o centrech symbol tří teček. Všimněte si také, že šířka pera 1 znamená, že 1 pixelu pro první tři tečky a 1 milimetru pro druhý elipsy.  
  
 ![Obrázek, který ukazuje dvě symbol tří teček: šířka rotace a psaní perem.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Oblast ořezu  
 A <xref:System.Drawing.Graphics> objektu udržuje výstřižek oblast, která se vztahuje na všechny položky, které vykreslené <xref:System.Drawing.Graphics> objektu. Můžete nastavit oblast ořezu voláním <xref:System.Drawing.Graphics.SetClip%2A> metody.  
  
 Následující příklad vytvoří ve tvaru plus oblast tvořící sjednocení dvou obdélníků. Tuto oblast je vyhrazená jako oblast ořezu z <xref:System.Drawing.Graphics> objektu. Kód poté nakreslí dva řádky, které jsou omezené na vnitřní oblast ořezu.  
  
```vb  
Dim graphics As Graphics = e.Graphics  
  
' Opaque red, width 5  
Dim pen As New Pen(Color.Red, 5)  
  
' Opaque aqua  
Dim brush As New SolidBrush(Color.FromArgb(255, 180, 255, 255))  
  
' Create a plus-shaped region by forming the union of two rectangles.  
Dim [region] As New [Region](New Rectangle(50, 0, 50, 150))  
[region].Union(New Rectangle(0, 50, 150, 50))  
graphics.FillRegion(brush, [region])  
  
' Set the clipping region.  
graphics.SetClip([region], CombineMode.Replace)  
  
' Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160)  
graphics.DrawLine(pen, 40, 20, 190, 150)  
```  
  
```csharp  
Graphics graphics = e.Graphics;  
  
// Opaque red, width 5  
Pen pen = new Pen(Color.Red, 5);    
  
// Opaque aqua  
SolidBrush brush = new SolidBrush(Color.FromArgb(255, 180, 255, 255));    
  
// Create a plus-shaped region by forming the union of two rectangles.  
Region region = new Region(new Rectangle(50, 0, 50, 150));  
region.Union(new Rectangle(0, 50, 150, 50));  
graphics.FillRegion(brush, region);  
  
// Set the clipping region.  
graphics.SetClip(region, CombineMode.Replace);  
  
// Draw two clipped lines.  
graphics.DrawLine(pen, 0, 30, 150, 160);  
graphics.DrawLine(pen, 40, 20, 190, 150);  
```  
  
 Následující obrázek znázorňuje zkrácený řádky:  
  
 ![Diagram zobrazující oblast ústřižku omezené.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Viz také:

- [Grafika a kreslení v rozhraní Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Použití vnořených grafických kontejnerů](using-nested-graphics-containers.md)
