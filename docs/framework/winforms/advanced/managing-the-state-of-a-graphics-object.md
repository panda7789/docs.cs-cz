---
title: "Správa stavu grafického objektu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- graphics [Windows Forms], managing state
- graphics [Windows Forms], clipping
ms.assetid: 6207cad1-7a34-4bd6-bfc1-db823ca7a73e
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 438243d16d8031d99e27993cadb44fd58bbec0b0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="9f094-102">Správa stavu grafického objektu</span><span class="sxs-lookup"><span data-stu-id="9f094-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="9f094-103"><xref:System.Drawing.Graphics> Třída je jádrem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="9f094-103">The <xref:System.Drawing.Graphics> class is at the heart of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="9f094-104">Kreslení nic, můžete získat <xref:System.Drawing.Graphics> objektu, nastavte jeho vlastnosti a volat jeho metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>a podobně).</span><span class="sxs-lookup"><span data-stu-id="9f094-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="9f094-105">Následující příklad volání <xref:System.Drawing.Graphics.DrawRectangle%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="9f094-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="9f094-106">První argument předaný <xref:System.Drawing.Graphics.DrawRectangle%2A> je metoda <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="9f094-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="9f094-107">Stav grafiky</span><span class="sxs-lookup"><span data-stu-id="9f094-107">Graphics State</span></span>  
 <span data-ttu-id="9f094-108">A <xref:System.Drawing.Graphics> objekt více než zadejte kreslení metody, jako třeba <xref:System.Drawing.Graphics.DrawLine%2A> a <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f094-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="9f094-109">A <xref:System.Drawing.Graphics> objekt také udržuje grafiky stav, který je možné rozdělit do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="9f094-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
-   <span data-ttu-id="9f094-110">Nastavení kvality</span><span class="sxs-lookup"><span data-stu-id="9f094-110">Quality settings</span></span>  
  
-   <span data-ttu-id="9f094-111">Transformace</span><span class="sxs-lookup"><span data-stu-id="9f094-111">Transformations</span></span>  
  
-   <span data-ttu-id="9f094-112">Oblast ořezu</span><span class="sxs-lookup"><span data-stu-id="9f094-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="9f094-113">Nastavení kvality</span><span class="sxs-lookup"><span data-stu-id="9f094-113">Quality Settings</span></span>  
 <span data-ttu-id="9f094-114">A <xref:System.Drawing.Graphics> objekt má několik vlastností, které ovlivňují kvalitu položky, které se mají vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="9f094-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="9f094-115">Například můžete nastavit <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnosti a určit typ vyhlazení (pokud existuje) použít na text.</span><span class="sxs-lookup"><span data-stu-id="9f094-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="9f094-116">Další vlastnosti, které ovlivňují kvality jsou <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, a <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="9f094-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="9f094-117">Následující příklad nevykresluje dvě výpustky, jeden s vyhlazování režim nastavený na <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> a jednu s vyhlazování režim nastavený na <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="9f094-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="9f094-118">Transformace</span><span class="sxs-lookup"><span data-stu-id="9f094-118">Transformations</span></span>  
 <span data-ttu-id="9f094-119">A <xref:System.Drawing.Graphics> objekt udržuje dvě transformace (world a stránky), které se použijí pro všechny položky, které jsou vykreslovány v tomto <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="9f094-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="9f094-120">Všechny afinní transformace mohou být uloženy ve Světové transformace.</span><span class="sxs-lookup"><span data-stu-id="9f094-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="9f094-121">Afinní transformace zahrnují změny velikosti, otáčení, která znázorňuje, zkosení a překladu.</span><span class="sxs-lookup"><span data-stu-id="9f094-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="9f094-122">Transformace stránky lze použít pro škálování a změna jednotky (například pixelů k palce).</span><span class="sxs-lookup"><span data-stu-id="9f094-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="9f094-123">Další informace najdete v tématu [systém souřadnic a transformace](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="9f094-123">For more information, see [Coordinate Systems and Transformations](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="9f094-124">Následující příklad ilustruje world a stránka transformace z <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="9f094-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="9f094-125">Světové transformace nastavena na rotaci 30 stupňů.</span><span class="sxs-lookup"><span data-stu-id="9f094-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="9f094-126">Transformace stránky je nastaven tak, aby souřadnice předat druhým <xref:System.Drawing.Graphics.DrawEllipse%2A> budou považovány za milimetry místo pixelů.</span><span class="sxs-lookup"><span data-stu-id="9f094-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="9f094-127">Kód vytvoří dvě identické volání <xref:System.Drawing.Graphics.DrawEllipse%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9f094-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="9f094-128">Světové transformace se použije pro první <xref:System.Drawing.Graphics.DrawEllipse%2A> volání a obě transformace (world a stránka) se použijí pro druhý <xref:System.Drawing.Graphics.DrawEllipse%2A> volání.</span><span class="sxs-lookup"><span data-stu-id="9f094-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="9f094-129">Následující obrázek znázorňuje dva výpustky.</span><span class="sxs-lookup"><span data-stu-id="9f094-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="9f094-130">Upozorňujeme, že se 30 stupeň otočení o původu souřadnicový systém (levého horního rohu klientské oblasti), nikoli o středy na symbol tří teček.</span><span class="sxs-lookup"><span data-stu-id="9f094-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="9f094-131">Všimněte si také, že pera šířku 1 znamená 1 pixel pro první elipsy a 1 milimetru pro druhý třemi tečkami.</span><span class="sxs-lookup"><span data-stu-id="9f094-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 <span data-ttu-id="9f094-132">![Elipsy](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")</span><span class="sxs-lookup"><span data-stu-id="9f094-132">![Ovals](../../../../docs/framework/winforms/advanced/media/csgraphicsascon1.png "csgraphicsascon1")</span></span>  
  
### <a name="clipping-region"></a><span data-ttu-id="9f094-133">Oblast ořezu</span><span class="sxs-lookup"><span data-stu-id="9f094-133">Clipping Region</span></span>  
 <span data-ttu-id="9f094-134">A <xref:System.Drawing.Graphics> objekt udržuje oblast ořezu, která se použije pro všechny položky, které jsou vykreslovány v tomto <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="9f094-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="9f094-135">Oblast ořezu můžete nastavit tak, že zavoláte <xref:System.Drawing.Graphics.SetClip%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="9f094-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="9f094-136">Následující příklad vytvoří oblast ve tvaru plus tvořících sjednocení dvou tvaru.</span><span class="sxs-lookup"><span data-stu-id="9f094-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="9f094-137">Tuto oblast je určený jako oblast výstřižek <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="9f094-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="9f094-138">Potom kód nevykresluje dva řádky, které jsou omezeny na vnitřek oblast ořezu.</span><span class="sxs-lookup"><span data-stu-id="9f094-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="9f094-139">Následující obrázek znázorňuje oříznutí řádky.</span><span class="sxs-lookup"><span data-stu-id="9f094-139">The following illustration shows the clipped lines.</span></span>  
  
 <span data-ttu-id="9f094-140">![Omezené oblasti klip](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")</span><span class="sxs-lookup"><span data-stu-id="9f094-140">![Limited Clip Region](../../../../docs/framework/winforms/advanced/media/graphicsascon2.png "graphicsascon2")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9f094-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="9f094-141">See Also</span></span>  
 [<span data-ttu-id="9f094-142">Grafika a kreslení v systému Windows Forms</span><span class="sxs-lookup"><span data-stu-id="9f094-142">Graphics and Drawing in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/graphics-and-drawing-in-windows-forms.md)  
 [<span data-ttu-id="9f094-143">Použití vnořených grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="9f094-143">Using Nested Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-nested-graphics-containers.md)
