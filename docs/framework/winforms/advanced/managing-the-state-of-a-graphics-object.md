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
ms.openlocfilehash: d1e7e6eac775ca779fb68605adcc9bc2b9915e49
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79182458"
---
# <a name="managing-the-state-of-a-graphics-object"></a>Správa stavu grafického objektu
Třída <xref:System.Drawing.Graphics> je v srdci GDI +. Chcete-li něco nakreslit, <xref:System.Drawing.Graphics> získáte objekt, nastavte <xref:System.Drawing.Graphics.DrawLine%2A>jeho <xref:System.Drawing.Graphics.DrawImage%2A> <xref:System.Drawing.Graphics.DrawString%2A>vlastnosti a zavolejte jeho metody , , a podobně).  
  
 Následující příklad volá <xref:System.Drawing.Graphics.DrawRectangle%2A> metodu <xref:System.Drawing.Graphics> objektu. První argument předaný metodě <xref:System.Drawing.Graphics.DrawRectangle%2A> je <xref:System.Drawing.Pen> objekt.  
  
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
 Objekt <xref:System.Drawing.Graphics> provádí více než více než <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawRectangle%2A>poskytují metody kreslení, například a . Objekt <xref:System.Drawing.Graphics> také udržuje grafický stav, který lze rozdělit do následujících kategorií:  
  
- Nastavení kvality  
  
- Transformace  
  
- Oblast oříznutí  
  
### <a name="quality-settings"></a>Nastavení kvality  
 Objekt <xref:System.Drawing.Graphics> má několik vlastností, které ovlivňují kvalitu položek, které jsou kresleny. Můžete například nastavit <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnost tak, aby určovala typ vyhlazení (pokud existuje) aplikovaný na text. Další vlastnosti, <xref:System.Drawing.Graphics.SmoothingMode%2A>které <xref:System.Drawing.Graphics.CompositingMode%2A> <xref:System.Drawing.Graphics.CompositingQuality%2A>ovlivňují <xref:System.Drawing.Graphics.InterpolationMode%2A>kvalitu, jsou , , a .  
  
 Následující příklad nakreslí dvě elipsy, jednu s <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> nastaveným režimem vyhlazení <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>a druhou s režimem vyhlazení nastaveným na :  
  
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
 Objekt <xref:System.Drawing.Graphics> udržuje dvě transformace (svět a stránku), které jsou <xref:System.Drawing.Graphics> použity na všechny položky nakreslené tímto objektem. Jakákoli vanatá transformace může být uložena ve světové transformaci. Mezi podobné transformace patří změna měřítka, otočení, zrcadlení, zkosení a překlady. Transformaci stránky lze použít pro změnu měřítka a pro změnu jednotek (například obrazové body na palce). Další informace naleznete [v tématu Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).  
  
 Následující příklad nastaví transformace světa a <xref:System.Drawing.Graphics> stránky objektu. Transformace světa je nastavena na 30stupňovou rotaci. Transformace stránky je nastavena tak, aby <xref:System.Drawing.Graphics.DrawEllipse%2A> souřadnice předané druhému byly považovány za milimetry namísto obrazových bodů. Kód provede dvě identická volání <xref:System.Drawing.Graphics.DrawEllipse%2A> metody. Transformace světa se použije <xref:System.Drawing.Graphics.DrawEllipse%2A> na první volání a obě transformace (svět a <xref:System.Drawing.Graphics.DrawEllipse%2A> stránka) se použijí na druhé volání.  
  
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
  
 Následující obrázek znázorňuje dvě elipsy. Všimněte si, že otočení o 30 stupňů je o původu souřadnicového systému (levý horní roh klientské oblasti), nikoli o středech elips. Všimněte si také, že šířka pera 1 znamená 1 pixel pro první elipsu a 1 milimetr pro druhou elipsu.  
  
 ![Obrázek, který znázorňuje dvě elipsy: otočení a šířku pera.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a>Oblast oříznutí  
 Objekt <xref:System.Drawing.Graphics> udržuje oblast oříznutí, která se vztahuje na <xref:System.Drawing.Graphics> všechny položky nakreslené tímto objektem. Oblast oříznutí můžete nastavit voláním <xref:System.Drawing.Graphics.SetClip%2A> metody.  
  
 Následující příklad vytvoří oblast ve tvaru plus vytvořením spojení dvou obdélníků. Tato oblast je označena jako <xref:System.Drawing.Graphics> oblast oříznutí objektu. Potom kód nakreslí dva řádky, které jsou omezeny na vnitřní oblasti oříznutí.  
  
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
  
 Následující obrázek znázorňuje oříznuté řádky:  
  
 ![Diagram, který zobrazuje omezenou oblast klipu.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a>Viz také

- [Grafika a kreslení v modelu Windows Forms](graphics-and-drawing-in-windows-forms.md)
- [Použití vnořených grafických kontejnerů](using-nested-graphics-containers.md)
