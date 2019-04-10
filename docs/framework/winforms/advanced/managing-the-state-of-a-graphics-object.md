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
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="c18f8-102">Správa stavu grafického objektu</span><span class="sxs-lookup"><span data-stu-id="c18f8-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="c18f8-103"><xref:System.Drawing.Graphics> Třída je srdcem [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="c18f8-103">The <xref:System.Drawing.Graphics> class is at the heart of [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span> <span data-ttu-id="c18f8-104">Chcete-li nakreslit nic, můžete získat <xref:System.Drawing.Graphics> objektu, vlastností a volat jeho metody <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>a podobně).</span><span class="sxs-lookup"><span data-stu-id="c18f8-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="c18f8-105">Následující příklad volá <xref:System.Drawing.Graphics.DrawRectangle%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="c18f8-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c18f8-106">První argument předaný metodě <xref:System.Drawing.Graphics.DrawRectangle%2A> je metoda <xref:System.Drawing.Pen> objektu.</span><span class="sxs-lookup"><span data-stu-id="c18f8-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="c18f8-107">Stav grafiky</span><span class="sxs-lookup"><span data-stu-id="c18f8-107">Graphics State</span></span>  
 <span data-ttu-id="c18f8-108">A <xref:System.Drawing.Graphics> objekt více než zadejte výkresu metody, jako třeba <xref:System.Drawing.Graphics.DrawLine%2A> a <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span><span class="sxs-lookup"><span data-stu-id="c18f8-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="c18f8-109">A <xref:System.Drawing.Graphics> objekt také uchovává stav grafiky, které je možné rozdělit do těchto kategorií:</span><span class="sxs-lookup"><span data-stu-id="c18f8-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
-   <span data-ttu-id="c18f8-110">Nastavení kvality</span><span class="sxs-lookup"><span data-stu-id="c18f8-110">Quality settings</span></span>  
  
-   <span data-ttu-id="c18f8-111">Transformace</span><span class="sxs-lookup"><span data-stu-id="c18f8-111">Transformations</span></span>  
  
-   <span data-ttu-id="c18f8-112">Oblast ořezu</span><span class="sxs-lookup"><span data-stu-id="c18f8-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="c18f8-113">Nastavení kvality</span><span class="sxs-lookup"><span data-stu-id="c18f8-113">Quality Settings</span></span>  
 <span data-ttu-id="c18f8-114">A <xref:System.Drawing.Graphics> objekt má několik vlastností, které ovlivňují kvality položky, které jsou zpracovány.</span><span class="sxs-lookup"><span data-stu-id="c18f8-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="c18f8-115">Například můžete nastavit <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnosti k určení typu (pokud existuje) antialiasingu použitý pro text.</span><span class="sxs-lookup"><span data-stu-id="c18f8-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="c18f8-116">Další vlastnosti, které ovlivňují kvalitu jsou <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, a <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="c18f8-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="c18f8-117">Následující příklad nakreslí dva symbol tří teček, jednu s nastavit na režim vyhlazování <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> a jeden u nastavit na režim vyhlazování <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span><span class="sxs-lookup"><span data-stu-id="c18f8-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="c18f8-118">Transformace</span><span class="sxs-lookup"><span data-stu-id="c18f8-118">Transformations</span></span>  
 <span data-ttu-id="c18f8-119">A <xref:System.Drawing.Graphics> objektu udržuje dvě transformace (světa a stránky), které se použijí u všech položek, které vykreslené <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="c18f8-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c18f8-120">Žádné afinní transformace mohou být uloženy v Světové transformace.</span><span class="sxs-lookup"><span data-stu-id="c18f8-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="c18f8-121">Afinní transformace patří škálování, otáčení, odráží, zkreslení a překladu.</span><span class="sxs-lookup"><span data-stu-id="c18f8-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="c18f8-122">Transformace stránky lze použít pro škálování a pro změnu jednotky (například pixelů cm).</span><span class="sxs-lookup"><span data-stu-id="c18f8-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="c18f8-123">Další informace najdete v tématu [systém souřadnic a transformace](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="c18f8-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="c18f8-124">Následující příklad nastaví transformace světa a stránka <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="c18f8-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c18f8-125">Světové transformace je nastavena na otočení kolem osy 30stupňů.</span><span class="sxs-lookup"><span data-stu-id="c18f8-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="c18f8-126">Transformace stránky nastavená tak, aby souřadnice předat druhé <xref:System.Drawing.Graphics.DrawEllipse%2A> , bude zacházeno jako milimetrech místo pixelů.</span><span class="sxs-lookup"><span data-stu-id="c18f8-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="c18f8-127">Kód volá dva identické <xref:System.Drawing.Graphics.DrawEllipse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c18f8-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="c18f8-128">Světové transformace se použije pro první <xref:System.Drawing.Graphics.DrawEllipse%2A> volání a obě transformace (světa a stránky) se použijí k druhému <xref:System.Drawing.Graphics.DrawEllipse%2A> volání.</span><span class="sxs-lookup"><span data-stu-id="c18f8-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="c18f8-129">Následující obrázek znázorňuje dvě symbol tří teček.</span><span class="sxs-lookup"><span data-stu-id="c18f8-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="c18f8-130">Všimněte si, otočení kolem osy z 30stupňů o původu souřadnicovém systému (levého horního rohu oblasti klienta), ne o centrech symbol tří teček.</span><span class="sxs-lookup"><span data-stu-id="c18f8-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="c18f8-131">Všimněte si také, že šířka pera 1 znamená, že 1 pixelu pro první tři tečky a 1 milimetru pro druhý elipsy.</span><span class="sxs-lookup"><span data-stu-id="c18f8-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![Obrázek, který ukazuje dvě symbol tří teček: šířka rotace a psaní perem.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="c18f8-133">Oblast ořezu</span><span class="sxs-lookup"><span data-stu-id="c18f8-133">Clipping Region</span></span>  
 <span data-ttu-id="c18f8-134">A <xref:System.Drawing.Graphics> objektu udržuje výstřižek oblast, která se vztahuje na všechny položky, které vykreslené <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="c18f8-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c18f8-135">Můžete nastavit oblast ořezu voláním <xref:System.Drawing.Graphics.SetClip%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="c18f8-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="c18f8-136">Následující příklad vytvoří ve tvaru plus oblast tvořící sjednocení dvou obdélníků.</span><span class="sxs-lookup"><span data-stu-id="c18f8-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="c18f8-137">Tuto oblast je vyhrazená jako oblast ořezu z <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="c18f8-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="c18f8-138">Kód poté nakreslí dva řádky, které jsou omezené na vnitřní oblast ořezu.</span><span class="sxs-lookup"><span data-stu-id="c18f8-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="c18f8-139">Následující obrázek znázorňuje zkrácený řádky:</span><span class="sxs-lookup"><span data-stu-id="c18f8-139">The following illustration shows the clipped lines:</span></span>  
  
 ![Diagram zobrazující oblast ústřižku omezené.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="c18f8-141">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c18f8-141">See also</span></span>

- [<span data-ttu-id="c18f8-142">Grafika a kreslení v rozhraní Windows Forms</span><span class="sxs-lookup"><span data-stu-id="c18f8-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="c18f8-143">Použití vnořených grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="c18f8-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
