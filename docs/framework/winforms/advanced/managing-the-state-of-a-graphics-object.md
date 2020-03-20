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
# <a name="managing-the-state-of-a-graphics-object"></a><span data-ttu-id="cc47a-102">Správa stavu grafického objektu</span><span class="sxs-lookup"><span data-stu-id="cc47a-102">Managing the State of a Graphics Object</span></span>
<span data-ttu-id="cc47a-103">Třída <xref:System.Drawing.Graphics> je v srdci GDI +.</span><span class="sxs-lookup"><span data-stu-id="cc47a-103">The <xref:System.Drawing.Graphics> class is at the heart of GDI+.</span></span> <span data-ttu-id="cc47a-104">Chcete-li něco nakreslit, <xref:System.Drawing.Graphics> získáte objekt, nastavte <xref:System.Drawing.Graphics.DrawLine%2A>jeho <xref:System.Drawing.Graphics.DrawImage%2A> <xref:System.Drawing.Graphics.DrawString%2A>vlastnosti a zavolejte jeho metody , , a podobně).</span><span class="sxs-lookup"><span data-stu-id="cc47a-104">To draw anything, you obtain a <xref:System.Drawing.Graphics> object, set its properties, and call its methods <xref:System.Drawing.Graphics.DrawLine%2A>, <xref:System.Drawing.Graphics.DrawImage%2A>, <xref:System.Drawing.Graphics.DrawString%2A>, and the like).</span></span>  
  
 <span data-ttu-id="cc47a-105">Následující příklad volá <xref:System.Drawing.Graphics.DrawRectangle%2A> metodu <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="cc47a-105">The following example calls the <xref:System.Drawing.Graphics.DrawRectangle%2A> method of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cc47a-106">První argument předaný metodě <xref:System.Drawing.Graphics.DrawRectangle%2A> je <xref:System.Drawing.Pen> objekt.</span><span class="sxs-lookup"><span data-stu-id="cc47a-106">The first argument passed to the <xref:System.Drawing.Graphics.DrawRectangle%2A> method is a <xref:System.Drawing.Pen> object.</span></span>  
  
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
  
## <a name="graphics-state"></a><span data-ttu-id="cc47a-107">Stav grafiky</span><span class="sxs-lookup"><span data-stu-id="cc47a-107">Graphics State</span></span>  
 <span data-ttu-id="cc47a-108">Objekt <xref:System.Drawing.Graphics> provádí více než více než <xref:System.Drawing.Graphics.DrawLine%2A> <xref:System.Drawing.Graphics.DrawRectangle%2A>poskytují metody kreslení, například a .</span><span class="sxs-lookup"><span data-stu-id="cc47a-108">A <xref:System.Drawing.Graphics> object does more than provide drawing methods, such as <xref:System.Drawing.Graphics.DrawLine%2A> and <xref:System.Drawing.Graphics.DrawRectangle%2A>.</span></span> <span data-ttu-id="cc47a-109">Objekt <xref:System.Drawing.Graphics> také udržuje grafický stav, který lze rozdělit do následujících kategorií:</span><span class="sxs-lookup"><span data-stu-id="cc47a-109">A <xref:System.Drawing.Graphics> object also maintains graphics state, which can be divided into the following categories:</span></span>  
  
- <span data-ttu-id="cc47a-110">Nastavení kvality</span><span class="sxs-lookup"><span data-stu-id="cc47a-110">Quality settings</span></span>  
  
- <span data-ttu-id="cc47a-111">Transformace</span><span class="sxs-lookup"><span data-stu-id="cc47a-111">Transformations</span></span>  
  
- <span data-ttu-id="cc47a-112">Oblast oříznutí</span><span class="sxs-lookup"><span data-stu-id="cc47a-112">Clipping region</span></span>  
  
### <a name="quality-settings"></a><span data-ttu-id="cc47a-113">Nastavení kvality</span><span class="sxs-lookup"><span data-stu-id="cc47a-113">Quality Settings</span></span>  
 <span data-ttu-id="cc47a-114">Objekt <xref:System.Drawing.Graphics> má několik vlastností, které ovlivňují kvalitu položek, které jsou kresleny.</span><span class="sxs-lookup"><span data-stu-id="cc47a-114">A <xref:System.Drawing.Graphics> object has several properties that influence the quality of the items that are drawn.</span></span> <span data-ttu-id="cc47a-115">Můžete například nastavit <xref:System.Drawing.Graphics.TextRenderingHint%2A> vlastnost tak, aby určovala typ vyhlazení (pokud existuje) aplikovaný na text.</span><span class="sxs-lookup"><span data-stu-id="cc47a-115">For example, you can set the <xref:System.Drawing.Graphics.TextRenderingHint%2A> property to specify the type of antialiasing (if any) applied to text.</span></span> <span data-ttu-id="cc47a-116">Další vlastnosti, <xref:System.Drawing.Graphics.SmoothingMode%2A>které <xref:System.Drawing.Graphics.CompositingMode%2A> <xref:System.Drawing.Graphics.CompositingQuality%2A>ovlivňují <xref:System.Drawing.Graphics.InterpolationMode%2A>kvalitu, jsou , , a .</span><span class="sxs-lookup"><span data-stu-id="cc47a-116">Other properties that influence quality are <xref:System.Drawing.Graphics.SmoothingMode%2A>, <xref:System.Drawing.Graphics.CompositingMode%2A>, <xref:System.Drawing.Graphics.CompositingQuality%2A>, and <xref:System.Drawing.Graphics.InterpolationMode%2A>.</span></span>  
  
 <span data-ttu-id="cc47a-117">Následující příklad nakreslí dvě elipsy, jednu s <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> nastaveným režimem vyhlazení <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>a druhou s režimem vyhlazení nastaveným na :</span><span class="sxs-lookup"><span data-stu-id="cc47a-117">The following example draws two ellipses, one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.AntiAlias> and one with the smoothing mode set to <xref:System.Drawing.Drawing2D.SmoothingMode.HighSpeed>:</span></span>  
  
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
  
### <a name="transformations"></a><span data-ttu-id="cc47a-118">Transformace</span><span class="sxs-lookup"><span data-stu-id="cc47a-118">Transformations</span></span>  
 <span data-ttu-id="cc47a-119">Objekt <xref:System.Drawing.Graphics> udržuje dvě transformace (svět a stránku), které jsou <xref:System.Drawing.Graphics> použity na všechny položky nakreslené tímto objektem.</span><span class="sxs-lookup"><span data-stu-id="cc47a-119">A <xref:System.Drawing.Graphics> object maintains two transformations (world and page) that are applied to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cc47a-120">Jakákoli vanatá transformace může být uložena ve světové transformaci.</span><span class="sxs-lookup"><span data-stu-id="cc47a-120">Any affine transformation can be stored in the world transformation.</span></span> <span data-ttu-id="cc47a-121">Mezi podobné transformace patří změna měřítka, otočení, zrcadlení, zkosení a překlady.</span><span class="sxs-lookup"><span data-stu-id="cc47a-121">Affine transformations include scaling, rotating, reflecting, skewing, and translating.</span></span> <span data-ttu-id="cc47a-122">Transformaci stránky lze použít pro změnu měřítka a pro změnu jednotek (například obrazové body na palce).</span><span class="sxs-lookup"><span data-stu-id="cc47a-122">The page transformation can be used for scaling and for changing units (for example, pixels to inches).</span></span> <span data-ttu-id="cc47a-123">Další informace naleznete [v tématu Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span><span class="sxs-lookup"><span data-stu-id="cc47a-123">For more information, see [Coordinate Systems and Transformations](coordinate-systems-and-transformations.md).</span></span>  
  
 <span data-ttu-id="cc47a-124">Následující příklad nastaví transformace světa a <xref:System.Drawing.Graphics> stránky objektu.</span><span class="sxs-lookup"><span data-stu-id="cc47a-124">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cc47a-125">Transformace světa je nastavena na 30stupňovou rotaci.</span><span class="sxs-lookup"><span data-stu-id="cc47a-125">The world transformation is set to a 30-degree rotation.</span></span> <span data-ttu-id="cc47a-126">Transformace stránky je nastavena tak, aby <xref:System.Drawing.Graphics.DrawEllipse%2A> souřadnice předané druhému byly považovány za milimetry namísto obrazových bodů.</span><span class="sxs-lookup"><span data-stu-id="cc47a-126">The page transformation is set so that the coordinates passed to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> will be treated as millimeters instead of pixels.</span></span> <span data-ttu-id="cc47a-127">Kód provede dvě identická volání <xref:System.Drawing.Graphics.DrawEllipse%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cc47a-127">The code makes two identical calls to the <xref:System.Drawing.Graphics.DrawEllipse%2A> method.</span></span> <span data-ttu-id="cc47a-128">Transformace světa se použije <xref:System.Drawing.Graphics.DrawEllipse%2A> na první volání a obě transformace (svět a <xref:System.Drawing.Graphics.DrawEllipse%2A> stránka) se použijí na druhé volání.</span><span class="sxs-lookup"><span data-stu-id="cc47a-128">The world transformation is applied to the first <xref:System.Drawing.Graphics.DrawEllipse%2A> call, and both transformations (world and page) are applied to the second <xref:System.Drawing.Graphics.DrawEllipse%2A> call.</span></span>  
  
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
  
 <span data-ttu-id="cc47a-129">Následující obrázek znázorňuje dvě elipsy.</span><span class="sxs-lookup"><span data-stu-id="cc47a-129">The following illustration shows the two ellipses.</span></span> <span data-ttu-id="cc47a-130">Všimněte si, že otočení o 30 stupňů je o původu souřadnicového systému (levý horní roh klientské oblasti), nikoli o středech elips.</span><span class="sxs-lookup"><span data-stu-id="cc47a-130">Note that the 30-degree rotation is about the origin of the coordinate system (upper-left corner of the client area), not about the centers of the ellipses.</span></span> <span data-ttu-id="cc47a-131">Všimněte si také, že šířka pera 1 znamená 1 pixel pro první elipsu a 1 milimetr pro druhou elipsu.</span><span class="sxs-lookup"><span data-stu-id="cc47a-131">Also note that the pen width of 1 means 1 pixel for the first ellipse and 1 millimeter for the second ellipse.</span></span>  
  
 ![Obrázek, který znázorňuje dvě elipsy: otočení a šířku pera.](./media/managing-the-state-of-a-graphics-object/set-rotation-pen-width-drawellipse-method.png)  
  
### <a name="clipping-region"></a><span data-ttu-id="cc47a-133">Oblast oříznutí</span><span class="sxs-lookup"><span data-stu-id="cc47a-133">Clipping Region</span></span>  
 <span data-ttu-id="cc47a-134">Objekt <xref:System.Drawing.Graphics> udržuje oblast oříznutí, která se vztahuje na <xref:System.Drawing.Graphics> všechny položky nakreslené tímto objektem.</span><span class="sxs-lookup"><span data-stu-id="cc47a-134">A <xref:System.Drawing.Graphics> object maintains a clipping region that applies to all items drawn by that <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cc47a-135">Oblast oříznutí můžete nastavit voláním <xref:System.Drawing.Graphics.SetClip%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="cc47a-135">You can set the clipping region by calling the <xref:System.Drawing.Graphics.SetClip%2A> method.</span></span>  
  
 <span data-ttu-id="cc47a-136">Následující příklad vytvoří oblast ve tvaru plus vytvořením spojení dvou obdélníků.</span><span class="sxs-lookup"><span data-stu-id="cc47a-136">The following example creates a plus-shaped region by forming the union of two rectangles.</span></span> <span data-ttu-id="cc47a-137">Tato oblast je označena jako <xref:System.Drawing.Graphics> oblast oříznutí objektu.</span><span class="sxs-lookup"><span data-stu-id="cc47a-137">That region is designated as the clipping region of a <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="cc47a-138">Potom kód nakreslí dva řádky, které jsou omezeny na vnitřní oblasti oříznutí.</span><span class="sxs-lookup"><span data-stu-id="cc47a-138">Then the code draws two lines that are restricted to the interior of the clipping region.</span></span>  
  
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
  
 <span data-ttu-id="cc47a-139">Následující obrázek znázorňuje oříznuté řádky:</span><span class="sxs-lookup"><span data-stu-id="cc47a-139">The following illustration shows the clipped lines:</span></span>  
  
 ![Diagram, který zobrazuje omezenou oblast klipu.](./media/managing-the-state-of-a-graphics-object/set-clipping-region-setclip-method.png)  
  
## <a name="see-also"></a><span data-ttu-id="cc47a-141">Viz také</span><span class="sxs-lookup"><span data-stu-id="cc47a-141">See also</span></span>

- [<span data-ttu-id="cc47a-142">Grafika a kreslení v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="cc47a-142">Graphics and Drawing in Windows Forms</span></span>](graphics-and-drawing-in-windows-forms.md)
- [<span data-ttu-id="cc47a-143">Použití vnořených grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="cc47a-143">Using Nested Graphics Containers</span></span>](using-nested-graphics-containers.md)
