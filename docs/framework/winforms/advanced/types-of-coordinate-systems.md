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
ms.openlocfilehash: 783e258f64633a4ddf7f3bbad858d6633256b97e
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54590374"
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="c85ab-102">Typy souřadnicových systémů</span><span class="sxs-lookup"><span data-stu-id="c85ab-102">Types of Coordinate Systems</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="c85ab-103">používá tři souřadnicových prostorech: world, stránky a zařízení.</span><span class="sxs-lookup"><span data-stu-id="c85ab-103">uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="c85ab-104">Světové souřadnice jsou souřadnice používají k modelování zvláštního grafického světa a souřadnice, které můžete předat do metody v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="c85ab-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="c85ab-105">Souřadnice stránky najdete souřadnicový systém používá povrchem výkresu, jako je například formulář nebo ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="c85ab-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="c85ab-106">Souřadnice zařízení jsou souřadnice použít fyzické zařízení, které je cílem vykreslování, jako je obrazovka nebo list papíru.</span><span class="sxs-lookup"><span data-stu-id="c85ab-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="c85ab-107">Když nastavíte volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, body, které můžete předat <xref:System.Drawing.Graphics.DrawLine%2A> metoda –`(0, 0)` a `(160, 80)`– jsou v souřadnicového prostoru světa.</span><span class="sxs-lookup"><span data-stu-id="c85ab-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="c85ab-108">Před [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete na obrazovce nakreslí čáru, souřadnice předávání sekvence transformací.</span><span class="sxs-lookup"><span data-stu-id="c85ab-108">Before [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="c85ab-109">Jedna transformace, volá Světové transformace převede Světové souřadnice na souřadnice stránky, a jinou transformaci, volá transformace stránky převede souřadnice stránky na souřadnice zařízení.</span><span class="sxs-lookup"><span data-stu-id="c85ab-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="c85ab-110">Transformace a souřadnicových systémů</span><span class="sxs-lookup"><span data-stu-id="c85ab-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="c85ab-111">Předpokládejme, že budete chtít pracovat s souřadnicový systém, který má původ v těle klientské oblasti spíše než levém horním rohu.</span><span class="sxs-lookup"><span data-stu-id="c85ab-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="c85ab-112">Řekněme například, že chcete, aby původu 100 pixelů od levého okraje oblasti klienta a 50 pixelů od horního okraje oblasti klienta.</span><span class="sxs-lookup"><span data-stu-id="c85ab-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="c85ab-113">Následující obrázek znázorňuje souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="c85ab-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="c85ab-114">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="c85ab-114">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="c85ab-115">Když nastavíte volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, zobrazí se řádek je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="c85ab-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="c85ab-116">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="c85ab-116">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="c85ab-117">Souřadnice z koncových bodů vaší řádku v tři souřadnicových prostorech jsou následující:</span><span class="sxs-lookup"><span data-stu-id="c85ab-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c85ab-118">World</span><span class="sxs-lookup"><span data-stu-id="c85ab-118">World</span></span>|<span data-ttu-id="c85ab-119">(0, 0) na (160, 80)</span><span class="sxs-lookup"><span data-stu-id="c85ab-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="c85ab-120">Stránka</span><span class="sxs-lookup"><span data-stu-id="c85ab-120">Page</span></span>|<span data-ttu-id="c85ab-121">(100, 50) na (260, 130)</span><span class="sxs-lookup"><span data-stu-id="c85ab-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="c85ab-122">Zařízení</span><span class="sxs-lookup"><span data-stu-id="c85ab-122">Device</span></span>|<span data-ttu-id="c85ab-123">(100, 50) na (260, 130)</span><span class="sxs-lookup"><span data-stu-id="c85ab-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="c85ab-124">Mějte na paměti, že má souřadnicového prostoru stránku původu v levém horním rohu oblasti klienta; to bude vždy probíhat případu.</span><span class="sxs-lookup"><span data-stu-id="c85ab-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="c85ab-125">Všimněte si také, protože je jednotka měření je pixel, souřadnice zařízení jsou stejné jako souřadnice stránky.</span><span class="sxs-lookup"><span data-stu-id="c85ab-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="c85ab-126">Pokud nastavíte měrnou jednotku na něco jiného než pixelů (například palce), bude se liší od souřadnice stránky souřadnice zařízení.</span><span class="sxs-lookup"><span data-stu-id="c85ab-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="c85ab-127">Světové transformace, která mapuje Světové souřadnice na souřadnice stránky, se nachází v <xref:System.Drawing.Graphics.Transform%2A> vlastnost <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="c85ab-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="c85ab-128">V předchozím příkladu je Světové transformace 100 jednotek překladu ve směru osy x a 50 jednotek ve směru osy y.</span><span class="sxs-lookup"><span data-stu-id="c85ab-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="c85ab-129">Následující příklad nastaví Světové transformace <xref:System.Drawing.Graphics> objekt a potom použije <xref:System.Drawing.Graphics> objekt nakreslení čáry je vidět na předchozím obrázku:</span><span class="sxs-lookup"><span data-stu-id="c85ab-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="c85ab-130">Transformace stránky mapuje na souřadnice zařízení souřadnice stránky.</span><span class="sxs-lookup"><span data-stu-id="c85ab-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="c85ab-131"><xref:System.Drawing.Graphics> Třída poskytuje <xref:System.Drawing.Graphics.PageUnit%2A> a <xref:System.Drawing.Graphics.PageScale%2A> vlastnosti pro manipulaci s transformace stránky.</span><span class="sxs-lookup"><span data-stu-id="c85ab-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="c85ab-132"><xref:System.Drawing.Graphics> Třída rovněž poskytuje dvě vlastnosti jen pro čtení, <xref:System.Drawing.Graphics.DpiX%2A> a <xref:System.Drawing.Graphics.DpiY%2A>, zkoumat vodorovného a svislého bodů na palec zobrazovacího zařízení.</span><span class="sxs-lookup"><span data-stu-id="c85ab-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="c85ab-133">Můžete použít <xref:System.Drawing.Graphics.PageUnit%2A> vlastnost <xref:System.Drawing.Graphics> tak, aby určovala jednotka měření, než je pixel.</span><span class="sxs-lookup"><span data-stu-id="c85ab-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="c85ab-134">Nelze nastavit <xref:System.Drawing.Graphics.PageUnit%2A> vlastnost <xref:System.Drawing.GraphicsUnit.World>, protože to není fyzické jednotky a způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="c85ab-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="c85ab-135">Následující příklad nakreslí čáru z (0, 0) na (2, 1), kde je bod (2, 1) 2 palce napravo a 1 palce dolů z bodu (0, 0):</span><span class="sxs-lookup"><span data-stu-id="c85ab-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="c85ab-136">Pokud nezadáte Šířka pera při konstrukci pera, bude v předchozím příkladu nakreslit čáru, která je jednu palec široké.</span><span class="sxs-lookup"><span data-stu-id="c85ab-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="c85ab-137">Můžete určit šířku pera v druhý argument <xref:System.Drawing.Pen> konstruktor:</span><span class="sxs-lookup"><span data-stu-id="c85ab-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="c85ab-138">Pokud předpokládáme, že zařízení má 96 přichycováním k pixelům ve vodorovném směru a 96 přichycováním k pixelům ve svislém směru, koncové body čáry v předchozím příkladu mají tyto souřadnice v tři souřadnice mezery:</span><span class="sxs-lookup"><span data-stu-id="c85ab-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c85ab-139">World</span><span class="sxs-lookup"><span data-stu-id="c85ab-139">World</span></span>|<span data-ttu-id="c85ab-140">(0, 0) na (2, 1)</span><span class="sxs-lookup"><span data-stu-id="c85ab-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="c85ab-141">Stránka</span><span class="sxs-lookup"><span data-stu-id="c85ab-141">Page</span></span>|<span data-ttu-id="c85ab-142">(0, 0) na (2, 1)</span><span class="sxs-lookup"><span data-stu-id="c85ab-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="c85ab-143">Zařízení</span><span class="sxs-lookup"><span data-stu-id="c85ab-143">Device</span></span>|<span data-ttu-id="c85ab-144">(0, 0, do (192, 96)</span><span class="sxs-lookup"><span data-stu-id="c85ab-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="c85ab-145">Všimněte si, že v levém horním rohu klientské oblasti je počátek souřadnicového prostoru světa, souřadnice stránky jsou stejné jako Světové souřadnice.</span><span class="sxs-lookup"><span data-stu-id="c85ab-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="c85ab-146">Můžete kombinovat transformace světa a stránky k dosažení různé účinky.</span><span class="sxs-lookup"><span data-stu-id="c85ab-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="c85ab-147">Předpokládejme například, kterou chcete použít jako jednotka měření palců a chcete počátek souřadnic systému 2 palcích od levého okraje oblasti klienta a 1/2 palce od horního okraje oblasti klienta.</span><span class="sxs-lookup"><span data-stu-id="c85ab-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="c85ab-148">Následující příklad nastaví transformace světa a stránka <xref:System.Drawing.Graphics> objekt a potom nakreslí čáru z (0, 0) na (2, 1):</span><span class="sxs-lookup"><span data-stu-id="c85ab-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="c85ab-149">Následující obrázek znázorňuje řádku a systém souřadnic.</span><span class="sxs-lookup"><span data-stu-id="c85ab-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="c85ab-150">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="c85ab-150">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="c85ab-151">Pokud předpokládáme, že zařízení má 96 přichycováním k pixelům ve vodorovném směru a 96 přichycováním k pixelům ve svislém směru, koncové body čáry v předchozím příkladu mají tyto souřadnice v tři souřadnice mezery:</span><span class="sxs-lookup"><span data-stu-id="c85ab-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="c85ab-152">World</span><span class="sxs-lookup"><span data-stu-id="c85ab-152">World</span></span>|<span data-ttu-id="c85ab-153">(0, 0) na (2, 1)</span><span class="sxs-lookup"><span data-stu-id="c85ab-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="c85ab-154">Stránka</span><span class="sxs-lookup"><span data-stu-id="c85ab-154">Page</span></span>|<span data-ttu-id="c85ab-155">(2, 0,5) na (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="c85ab-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="c85ab-156">Zařízení</span><span class="sxs-lookup"><span data-stu-id="c85ab-156">Device</span></span>|<span data-ttu-id="c85ab-157">(192, 48) na (384, 144)</span><span class="sxs-lookup"><span data-stu-id="c85ab-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="c85ab-158">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c85ab-158">See also</span></span>
- [<span data-ttu-id="c85ab-159">Systém souřadnic a transformace</span><span class="sxs-lookup"><span data-stu-id="c85ab-159">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)
- [<span data-ttu-id="c85ab-160">Maticové znázornění transformací</span><span class="sxs-lookup"><span data-stu-id="c85ab-160">Matrix Representation of Transformations</span></span>](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
