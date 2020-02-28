---
title: Typy souřadnicových systémů
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- transformations [Windows Forms], page
- unit of measure
- world coordinate system
- page coordinate system
- page transformation
- device coordinate system
- world transformation
- coordinate systems
- transformations [Windows Forms], world
ms.assetid: c61ff50a-eb1d-4e6c-83cd-f7e9764cfa9f
ms.openlocfilehash: bbb0d4908d4a281499336d262c653d7b72f3ccdc
ms.sourcegitcommit: 00aa62e2f469c2272a457b04e66b4cc3c97a800b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/28/2020
ms.locfileid: "78159803"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="75fd1-102">Typy souřadnicových systémů</span><span class="sxs-lookup"><span data-stu-id="75fd1-102">Types of Coordinate Systems</span></span>
<span data-ttu-id="75fd1-103">GDI+ používá tři prostory souřadnic: World, Page a Device.</span><span class="sxs-lookup"><span data-stu-id="75fd1-103">GDI+ uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="75fd1-104">Světové souřadnice jsou souřadnice používané k modelování konkrétního grafického světa a jsou souřadnicemi, které předáváte metodám v .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="75fd1-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="75fd1-105">Souřadnice stránky odkazují na systém souřadnic používaný plochou kreslení, jako je například formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="75fd1-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="75fd1-106">Souřadnice zařízení jsou souřadnice používané fyzickým zařízením, které se vykresluje, jako je například obrazovka nebo list papíru.</span><span class="sxs-lookup"><span data-stu-id="75fd1-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="75fd1-107">Po provedení `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`volání jsou body, které předáte metodě <xref:System.Drawing.Graphics.DrawLine%2A> –`(0, 0)` a `(160, 80)`, umístěny v prostoru souřadnic World.</span><span class="sxs-lookup"><span data-stu-id="75fd1-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="75fd1-108">Předtím, než může rozhraní GDI+ vykreslit čáru na obrazovce, přejdou souřadnice posloupnosti transformací.</span><span class="sxs-lookup"><span data-stu-id="75fd1-108">Before GDI+ can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="75fd1-109">Jedna transformace, nazývaná světová transformace, převede Světové souřadnice na souřadnice stránky a jinou transformaci, která se nazývá transformace stránky, převede souřadnice stránky na souřadnice zařízení.</span><span class="sxs-lookup"><span data-stu-id="75fd1-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="75fd1-110">Transformace a koordinace systémů</span><span class="sxs-lookup"><span data-stu-id="75fd1-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="75fd1-111">Předpokládejme, že chcete pracovat se systémovou souřadnicí, která má svůj původ v těle oblasti klienta, nikoli v levém horním rohu.</span><span class="sxs-lookup"><span data-stu-id="75fd1-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="75fd1-112">Řekněme například, že chcete, aby počátek byl 100 pixelů od levého okraje klientské oblasti a 50 pixelů od horní části klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="75fd1-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="75fd1-113">Následující obrázek znázorňuje systém souřadnic.</span><span class="sxs-lookup"><span data-stu-id="75fd1-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="75fd1-114">![Systém souřadnic](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="75fd1-114">![Coordinate System](./media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="75fd1-115">Po provedení volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`získáte řádek na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="75fd1-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="75fd1-116">![Systém souřadnic](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="75fd1-116">![Coordinate System](./media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="75fd1-117">Souřadnice koncových bodů na řádku ve třech souřadnicových prostorech jsou následující:</span><span class="sxs-lookup"><span data-stu-id="75fd1-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75fd1-118">World</span><span class="sxs-lookup"><span data-stu-id="75fd1-118">World</span></span>|<span data-ttu-id="75fd1-119">(0, 0) až (160, 80)</span><span class="sxs-lookup"><span data-stu-id="75fd1-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="75fd1-120">Stránka</span><span class="sxs-lookup"><span data-stu-id="75fd1-120">Page</span></span>|<span data-ttu-id="75fd1-121">(100, 50) až (260, 130)</span><span class="sxs-lookup"><span data-stu-id="75fd1-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="75fd1-122">Zařízení</span><span class="sxs-lookup"><span data-stu-id="75fd1-122">Device</span></span>|<span data-ttu-id="75fd1-123">(100, 50) až (260, 130)</span><span class="sxs-lookup"><span data-stu-id="75fd1-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="75fd1-124">Všimněte si, že prostor souřadnic stránky má svůj počátek v levém horním rohu klientské oblasti. to bude mít vždycky tento případ.</span><span class="sxs-lookup"><span data-stu-id="75fd1-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="75fd1-125">Všimněte si také, že vzhledem k tomu, že jednotka míry je pixel, jsou souřadnice zařízení stejné jako souřadnice stránky.</span><span class="sxs-lookup"><span data-stu-id="75fd1-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="75fd1-126">Pokud nastavíte měrnou jednotku na jinou hodnotu než pixely (například palce), souřadnice zařízení se budou lišit od souřadnic stránky.</span><span class="sxs-lookup"><span data-stu-id="75fd1-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="75fd1-127">Transformace světa, která mapuje souřadnice světa na souřadnice stránky, je uložena ve vlastnosti <xref:System.Drawing.Graphics.Transform%2A> třídy <xref:System.Drawing.Graphics>.</span><span class="sxs-lookup"><span data-stu-id="75fd1-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="75fd1-128">V předchozím příkladu je transformace světa převodem jednotek 100 ve směru x a 50 jednotek ve směru y.</span><span class="sxs-lookup"><span data-stu-id="75fd1-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="75fd1-129">Následující příklad nastaví světovou transformaci objektu <xref:System.Drawing.Graphics> a poté pomocí tohoto objektu <xref:System.Drawing.Graphics> vykreslí řádek zobrazený na předchozím obrázku:</span><span class="sxs-lookup"><span data-stu-id="75fd1-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="75fd1-130">Transformace stránky mapuje souřadnice stránky na souřadnice zařízení.</span><span class="sxs-lookup"><span data-stu-id="75fd1-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="75fd1-131">Třída <xref:System.Drawing.Graphics> poskytuje vlastnosti <xref:System.Drawing.Graphics.PageUnit%2A> a <xref:System.Drawing.Graphics.PageScale%2A> pro manipulaci s transformací stránky.</span><span class="sxs-lookup"><span data-stu-id="75fd1-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="75fd1-132">Třída <xref:System.Drawing.Graphics> také poskytuje dvě vlastnosti jen pro čtení, <xref:System.Drawing.Graphics.DpiX%2A> a <xref:System.Drawing.Graphics.DpiY%2A>pro zkoumání vodorovných a svislých bodů na palec zobrazovacího zařízení.</span><span class="sxs-lookup"><span data-stu-id="75fd1-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="75fd1-133">Vlastnost <xref:System.Drawing.Graphics.PageUnit%2A> třídy <xref:System.Drawing.Graphics> můžete použít k určení měrné jednotky, která je jiná než pixel.</span><span class="sxs-lookup"><span data-stu-id="75fd1-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="75fd1-134">Vlastnost <xref:System.Drawing.Graphics.PageUnit%2A> nelze nastavit na hodnotu <xref:System.Drawing.GraphicsUnit.World>, protože se nejedná o fyzickou jednotku a vyvolá výjimku.</span><span class="sxs-lookup"><span data-stu-id="75fd1-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="75fd1-135">Následující příklad Kreslí čáru od (0, 0) do (2, 1), kde je bod (2, 1) 2 palců vpravo a 1 palec dolů od bodu (0, 0):</span><span class="sxs-lookup"><span data-stu-id="75fd1-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
> <span data-ttu-id="75fd1-136">Pokud při sestavování pera nezadáte šířku pera, v předchozím příkladu se nakreslí čára, která je o jednu palce široké.</span><span class="sxs-lookup"><span data-stu-id="75fd1-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="75fd1-137">Šířku pera můžete zadat v druhém argumentu <xref:System.Drawing.Pen> konstruktoru:</span><span class="sxs-lookup"><span data-stu-id="75fd1-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="75fd1-138">Pokud předpokládáme, že zobrazovací zařízení má 96 bodů na palec v horizontálním směru a 96 bodů na palec ve svislém směru, koncových bodů v předchozím příkladu mají následující souřadnice ve třech souřadnicových prostorech:</span><span class="sxs-lookup"><span data-stu-id="75fd1-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75fd1-139">World</span><span class="sxs-lookup"><span data-stu-id="75fd1-139">World</span></span>|<span data-ttu-id="75fd1-140">(0, 0) až (2, 1)</span><span class="sxs-lookup"><span data-stu-id="75fd1-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="75fd1-141">Stránka</span><span class="sxs-lookup"><span data-stu-id="75fd1-141">Page</span></span>|<span data-ttu-id="75fd1-142">(0, 0) až (2, 1)</span><span class="sxs-lookup"><span data-stu-id="75fd1-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="75fd1-143">Zařízení</span><span class="sxs-lookup"><span data-stu-id="75fd1-143">Device</span></span>|<span data-ttu-id="75fd1-144">(0, 0) až (192, 96)</span><span class="sxs-lookup"><span data-stu-id="75fd1-144">(0, 0) to (192, 96)</span></span>|  
  
 <span data-ttu-id="75fd1-145">Všimněte si, že vzhledem k tomu, že počátek prostoru souřadnic světa je v levém horním rohu klientské oblasti, souřadnice stránky jsou stejné jako u světových souřadnic.</span><span class="sxs-lookup"><span data-stu-id="75fd1-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="75fd1-146">K dosažení celé řady efektů můžete kombinovat svět a transformace stránek.</span><span class="sxs-lookup"><span data-stu-id="75fd1-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="75fd1-147">Předpokládejme například, že chcete použít palce jako měrnou jednotku a chcete, aby byl počátek souřadnicového systému 2 palce od levého okraje oblasti klienta a 1/2 palce od horní části klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="75fd1-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="75fd1-148">Následující příklad nastaví World a Page Transformers objektu <xref:System.Drawing.Graphics> a potom nakreslí čáru od (0, 0) do (2, 1):</span><span class="sxs-lookup"><span data-stu-id="75fd1-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="75fd1-149">Následující ilustrace znázorňuje systém řádku a souřadnic.</span><span class="sxs-lookup"><span data-stu-id="75fd1-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="75fd1-150">![Systém souřadnic](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="75fd1-150">![Coordinate System](./media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="75fd1-151">Pokud předpokládáme, že zobrazovací zařízení má 96 bodů na palec v horizontálním směru a 96 bodů na palec ve svislém směru, koncových bodů v předchozím příkladu mají následující souřadnice ve třech souřadnicových prostorech:</span><span class="sxs-lookup"><span data-stu-id="75fd1-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="75fd1-152">World</span><span class="sxs-lookup"><span data-stu-id="75fd1-152">World</span></span>|<span data-ttu-id="75fd1-153">(0, 0) až (2, 1)</span><span class="sxs-lookup"><span data-stu-id="75fd1-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="75fd1-154">Stránka</span><span class="sxs-lookup"><span data-stu-id="75fd1-154">Page</span></span>|<span data-ttu-id="75fd1-155">(2, 0,5) až (4, 1,5)</span><span class="sxs-lookup"><span data-stu-id="75fd1-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="75fd1-156">Zařízení</span><span class="sxs-lookup"><span data-stu-id="75fd1-156">Device</span></span>|<span data-ttu-id="75fd1-157">(192, 48) až (384, 144)</span><span class="sxs-lookup"><span data-stu-id="75fd1-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="75fd1-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="75fd1-158">See also</span></span>

- [<span data-ttu-id="75fd1-159">Systém souřadnic a transformace</span><span class="sxs-lookup"><span data-stu-id="75fd1-159">Coordinate Systems and Transformations</span></span>](coordinate-systems-and-transformations.md)
- [<span data-ttu-id="75fd1-160">Maticové znázornění transformací</span><span class="sxs-lookup"><span data-stu-id="75fd1-160">Matrix Representation of Transformations</span></span>](matrix-representation-of-transformations.md)
