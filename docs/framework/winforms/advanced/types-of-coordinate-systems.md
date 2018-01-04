---
title: "Typy souřadnicových systémů"
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
caps.latest.revision: "15"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 287b1c9eddef882041d9e4eac44a06190f3585a4
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="types-of-coordinate-systems"></a><span data-ttu-id="95713-102">Typy souřadnicových systémů</span><span class="sxs-lookup"><span data-stu-id="95713-102">Types of Coordinate Systems</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="95713-103">používá tři souřadnice mezery: world, stránky a zařízení.</span><span class="sxs-lookup"><span data-stu-id="95713-103"> uses three coordinate spaces: world, page, and device.</span></span> <span data-ttu-id="95713-104">Souřadnice World jsou použita k modelování konkrétní grafické world souřadnice a souřadnice, které můžete předat metody v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="95713-104">World coordinates are the coordinates used to model a particular graphic world and are the coordinates you pass to methods in the .NET Framework.</span></span> <span data-ttu-id="95713-105">Stránka souřadnice naleznete souřadnicový systém používán kreslicí plochy, jako jsou formuláře nebo ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="95713-105">Page coordinates refer to the coordinate system used by a drawing surface, such as a form or control.</span></span> <span data-ttu-id="95713-106">Souřadnice zařízení jsou souřadnice používané fyzického zařízení přitahuje, jako je obrazovky nebo list papíru.</span><span class="sxs-lookup"><span data-stu-id="95713-106">Device coordinates are the coordinates used by the physical device being drawn on, such as a screen or sheet of paper.</span></span> <span data-ttu-id="95713-107">Pokud provedete volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, body, které můžete předat <xref:System.Drawing.Graphics.DrawLine%2A> metoda –`(0, 0)` a `(160, 80)`– jsou v prostoru souřadnic world.</span><span class="sxs-lookup"><span data-stu-id="95713-107">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, the points that you pass to the <xref:System.Drawing.Graphics.DrawLine%2A> method—`(0, 0)` and `(160, 80)`—are in the world coordinate space.</span></span> <span data-ttu-id="95713-108">Před [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] můžete nakreslení čáry na obrazovce, souřadnice předávat posloupnost transformace.</span><span class="sxs-lookup"><span data-stu-id="95713-108">Before [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] can draw the line on the screen, the coordinates pass through a sequence of transformations.</span></span> <span data-ttu-id="95713-109">Jeden transformace, názvem Světové transformace převede world souřadnice jiného a jiné transformace, názvem transformace stránky převede souřadnice stránky na zařízení souřadnice.</span><span class="sxs-lookup"><span data-stu-id="95713-109">One transformation, called the world transformation, converts world coordinates to page coordinates, and another transformation, called the page transformation, converts page coordinates to device coordinates.</span></span>  
  
## <a name="transforms-and-coordinate-systems"></a><span data-ttu-id="95713-110">Systémy souřadnic a transformace</span><span class="sxs-lookup"><span data-stu-id="95713-110">Transforms and Coordinate Systems</span></span>  
 <span data-ttu-id="95713-111">Předpokládejme, že chcete pro práci s souřadnicový systém, který má původ v těle klientské oblasti místo levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="95713-111">Suppose you want to work with a coordinate system that has its origin in the body of the client area rather than the upper-left corner.</span></span> <span data-ttu-id="95713-112">Řekněme například, které chcete počátek 100 pixelů od levého okraje klientské oblasti a 50 pixelů z horní části oblasti klienta.</span><span class="sxs-lookup"><span data-stu-id="95713-112">Say, for example, that you want the origin to be 100 pixels from the left edge of the client area and 50 pixels from the top of the client area.</span></span> <span data-ttu-id="95713-113">Následující obrázek znázorňuje souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="95713-113">The following illustration shows such a coordinate system.</span></span>  
  
 <span data-ttu-id="95713-114">![Systém souřadnic](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span><span class="sxs-lookup"><span data-stu-id="95713-114">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art01.gif "AboutGdip05_art01")</span></span>  
  
 <span data-ttu-id="95713-115">Pokud provedete volání `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, získání řádku vidět na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="95713-115">When you make the call `myGraphics.DrawLine(myPen, 0, 0, 160, 80)`, you get the line shown in the following illustration.</span></span>  
  
 <span data-ttu-id="95713-116">![Systém souřadnic](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span><span class="sxs-lookup"><span data-stu-id="95713-116">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art02.gif "AboutGdip05_art02")</span></span>  
  
 <span data-ttu-id="95713-117">Souřadnice z koncových bodů vaší čáry v tři souřadnice prostory jsou následující:</span><span class="sxs-lookup"><span data-stu-id="95713-117">The coordinates of the endpoints of your line in the three coordinate spaces are as follows:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95713-118">World</span><span class="sxs-lookup"><span data-stu-id="95713-118">World</span></span>|<span data-ttu-id="95713-119">(0, 0) na (160, 80)</span><span class="sxs-lookup"><span data-stu-id="95713-119">(0, 0) to (160, 80)</span></span>|  
|<span data-ttu-id="95713-120">Stránka</span><span class="sxs-lookup"><span data-stu-id="95713-120">Page</span></span>|<span data-ttu-id="95713-121">(100, 50) na (260, 130)</span><span class="sxs-lookup"><span data-stu-id="95713-121">(100, 50) to (260, 130)</span></span>|  
|<span data-ttu-id="95713-122">Zařízení</span><span class="sxs-lookup"><span data-stu-id="95713-122">Device</span></span>|<span data-ttu-id="95713-123">(100, 50) na (260, 130)</span><span class="sxs-lookup"><span data-stu-id="95713-123">(100, 50) to (260, 130)</span></span>|  
  
 <span data-ttu-id="95713-124">Upozorňujeme, že stránka souřadnicového prostoru má původ v levém horním rohu klientské oblasti; vždy to bude v případě.</span><span class="sxs-lookup"><span data-stu-id="95713-124">Note that the page coordinate space has its origin at the upper-left corner of the client area; this will always be the case.</span></span> <span data-ttu-id="95713-125">Všimněte si také, že Měrná jednotka je pixelech, a proto souřadnice zařízení jsou stejné jako souřadnice stránky.</span><span class="sxs-lookup"><span data-stu-id="95713-125">Also note that because the unit of measure is the pixel, the device coordinates are the same as the page coordinates.</span></span> <span data-ttu-id="95713-126">Pokud nastavíte Měrná jednotka služby něco jiného než pixelů (například palce), pak budou liší od souřadnice stránky souřadnice zařízení.</span><span class="sxs-lookup"><span data-stu-id="95713-126">If you set the unit of measure to something other than pixels (for example, inches), then the device coordinates will be different from the page coordinates.</span></span>  
  
 <span data-ttu-id="95713-127">Světové transformace, která se mapuje na stránce souřadnice world souřadnice, trvá v <xref:System.Drawing.Graphics.Transform%2A> vlastnost <xref:System.Drawing.Graphics> třídy.</span><span class="sxs-lookup"><span data-stu-id="95713-127">The world transformation, which maps world coordinates to page coordinates, is held in the <xref:System.Drawing.Graphics.Transform%2A> property of the <xref:System.Drawing.Graphics> class.</span></span> <span data-ttu-id="95713-128">V předchozím příkladu je Světové transformace 100 jednotky překladu ve směru osy x a 50 jednotky ve směru osy y.</span><span class="sxs-lookup"><span data-stu-id="95713-128">In the preceding example, the world transformation is a translation 100 units in the x direction and 50 units in the y direction.</span></span> <span data-ttu-id="95713-129">Následující příklad ilustruje Světové transformace <xref:System.Drawing.Graphics> objektu, který používá <xref:System.Drawing.Graphics> objekt kreslení čáry vidět na předchozím obrázku:</span><span class="sxs-lookup"><span data-stu-id="95713-129">The following example sets the world transformation of a <xref:System.Drawing.Graphics> object and then uses that <xref:System.Drawing.Graphics> object to draw the line shown in the preceding figure:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#31)]
 [!code-vb[System.Drawing.CoordinateSystems#31](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#31)]  
  
 <span data-ttu-id="95713-130">Transformace stránky mapuje stránky souřadnice souřadnice zařízení.</span><span class="sxs-lookup"><span data-stu-id="95713-130">The page transformation maps page coordinates to device coordinates.</span></span> <span data-ttu-id="95713-131"><xref:System.Drawing.Graphics> Třída poskytuje <xref:System.Drawing.Graphics.PageUnit%2A> a <xref:System.Drawing.Graphics.PageScale%2A> vlastnosti pro manipulaci s transformace stránky.</span><span class="sxs-lookup"><span data-stu-id="95713-131">The <xref:System.Drawing.Graphics> class provides the <xref:System.Drawing.Graphics.PageUnit%2A> and <xref:System.Drawing.Graphics.PageScale%2A> properties for manipulating the page transformation.</span></span> <span data-ttu-id="95713-132"><xref:System.Drawing.Graphics> Třída rovněž poskytuje dvě vlastnosti jen pro čtení, <xref:System.Drawing.Graphics.DpiX%2A> a <xref:System.Drawing.Graphics.DpiY%2A>, pro zkoumání vodorovného a svislého bodů na palec zobrazení zařízení.</span><span class="sxs-lookup"><span data-stu-id="95713-132">The <xref:System.Drawing.Graphics> class also provides two read-only properties, <xref:System.Drawing.Graphics.DpiX%2A> and <xref:System.Drawing.Graphics.DpiY%2A>, for examining the horizontal and vertical dots per inch of the display device.</span></span>  
  
 <span data-ttu-id="95713-133">Můžete použít <xref:System.Drawing.Graphics.PageUnit%2A> vlastnost <xref:System.Drawing.Graphics> třídy zadejte jednotku míry než pixelech.</span><span class="sxs-lookup"><span data-stu-id="95713-133">You can use the <xref:System.Drawing.Graphics.PageUnit%2A> property of the <xref:System.Drawing.Graphics> class to specify a unit of measure other than the pixel.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="95713-134">Nelze nastavit <xref:System.Drawing.Graphics.PageUnit%2A> vlastnost <xref:System.Drawing.GraphicsUnit.World>, protože to není fyzické jednotky a způsobí výjimku.</span><span class="sxs-lookup"><span data-stu-id="95713-134">You cannot set the <xref:System.Drawing.Graphics.PageUnit%2A> property to <xref:System.Drawing.GraphicsUnit.World>, as this is not a physical unit and will cause an exception.</span></span>  
  
 <span data-ttu-id="95713-135">Následující příklad nevykresluje řádek ze (0, 0) na (2, 1), kde je bod (2, 1) je 2 palce vpravo a 1 palec dolů z bodu (0, 0):</span><span class="sxs-lookup"><span data-stu-id="95713-135">The following example draws a line from (0, 0) to (2, 1), where the point (2, 1) is 2 inches to the right and 1 inch down from the point (0, 0):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#32)]
 [!code-vb[System.Drawing.CoordinateSystems#32](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#32)]  
  
> [!NOTE]
>  <span data-ttu-id="95713-136">Pokud nezadáte šířku při vytvoření pera, bude v předchozím příkladu nakreslit čáru, která je jeden palec široké.</span><span class="sxs-lookup"><span data-stu-id="95713-136">If you don't specify a pen width when you construct your pen, the preceding example will draw a line that is one inch wide.</span></span> <span data-ttu-id="95713-137">Můžete zadat šířku pera v druhý argument <xref:System.Drawing.Pen> konstruktor:</span><span class="sxs-lookup"><span data-stu-id="95713-137">You can specify the pen width in the second argument to the <xref:System.Drawing.Pen> constructor:</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#33)]
 [!code-vb[System.Drawing.CoordinateSystems#33](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#33)]  
  
 <span data-ttu-id="95713-138">Pokud předpokládáme, že má zařízení zobrazení 96 bodů na palec ve vodorovném směru a 96 bodů na palec ve svislém směru, koncové body řádek v předchozím příkladu mají následující souřadnice do prostorů tři souřadnice:</span><span class="sxs-lookup"><span data-stu-id="95713-138">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95713-139">World</span><span class="sxs-lookup"><span data-stu-id="95713-139">World</span></span>|<span data-ttu-id="95713-140">(0, 0) na (2, 1)</span><span class="sxs-lookup"><span data-stu-id="95713-140">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="95713-141">Stránka</span><span class="sxs-lookup"><span data-stu-id="95713-141">Page</span></span>|<span data-ttu-id="95713-142">(0, 0) na (2, 1)</span><span class="sxs-lookup"><span data-stu-id="95713-142">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="95713-143">Zařízení</span><span class="sxs-lookup"><span data-stu-id="95713-143">Device</span></span>|<span data-ttu-id="95713-144">(0, 0, do (192, 96)</span><span class="sxs-lookup"><span data-stu-id="95713-144">(0, 0, to (192, 96)</span></span>|  
  
 <span data-ttu-id="95713-145">Upozorňujeme, že vzhledem k tomu počátek souřadnicového prostoru world v levém horním rohu klientské oblasti, souřadnice stránky jsou stejné jako souřadnice world.</span><span class="sxs-lookup"><span data-stu-id="95713-145">Note that because the origin of the world coordinate space is at the upper-left corner of the client area, the page coordinates are the same as the world coordinates.</span></span>  
  
 <span data-ttu-id="95713-146">Můžete kombinovat world a stránka transformace k dosažení různé efekty.</span><span class="sxs-lookup"><span data-stu-id="95713-146">You can combine the world and page transformations to achieve a variety of effects.</span></span> <span data-ttu-id="95713-147">Předpokládejme například, kterou chcete použít palce jako měrná jednotka služby a chcete původ systému souřadnice 2 palce od levého okraje klientské oblasti a 1/2 palce z horní části oblasti klienta.</span><span class="sxs-lookup"><span data-stu-id="95713-147">For example, suppose you want to use inches as the unit of measure and you want the origin of your coordinate system to be 2 inches from the left edge of the client area and 1/2 inch from the top of the client area.</span></span> <span data-ttu-id="95713-148">Následující příklad ilustruje world a stránka transformace z <xref:System.Drawing.Graphics> objektu a poté nakreslí řádek ze (0, 0) na (2, 1):</span><span class="sxs-lookup"><span data-stu-id="95713-148">The following example sets the world and page transformations of a <xref:System.Drawing.Graphics> object and then draws a line from (0, 0) to (2, 1):</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#34)]
 [!code-vb[System.Drawing.CoordinateSystems#34](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#34)]  
  
 <span data-ttu-id="95713-149">Následující obrázek znázorňuje řádku a souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="95713-149">The following illustration shows the line and coordinate system.</span></span>  
  
 <span data-ttu-id="95713-150">![Systém souřadnic](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span><span class="sxs-lookup"><span data-stu-id="95713-150">![Coordinate System](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art03.gif "AboutGdip05_art03")</span></span>  
  
 <span data-ttu-id="95713-151">Pokud předpokládáme, že má zařízení zobrazení 96 bodů na palec ve vodorovném směru a 96 bodů na palec ve svislém směru, koncové body řádek v předchozím příkladu mají následující souřadnice do prostorů tři souřadnice:</span><span class="sxs-lookup"><span data-stu-id="95713-151">If we assume that the display device has 96 dots per inch in the horizontal direction and 96 dots per inch in the vertical direction, the endpoints of the line in the preceding example have the following coordinates in the three coordinate spaces:</span></span>  
  
|||  
|-|-|  
|<span data-ttu-id="95713-152">World</span><span class="sxs-lookup"><span data-stu-id="95713-152">World</span></span>|<span data-ttu-id="95713-153">(0, 0) na (2, 1)</span><span class="sxs-lookup"><span data-stu-id="95713-153">(0, 0) to (2, 1)</span></span>|  
|<span data-ttu-id="95713-154">Stránka</span><span class="sxs-lookup"><span data-stu-id="95713-154">Page</span></span>|<span data-ttu-id="95713-155">(2, 0,5) na (4, 1.5)</span><span class="sxs-lookup"><span data-stu-id="95713-155">(2, 0.5) to (4, 1.5)</span></span>|  
|<span data-ttu-id="95713-156">Zařízení</span><span class="sxs-lookup"><span data-stu-id="95713-156">Device</span></span>|<span data-ttu-id="95713-157">(192, 48) na (384, 144)</span><span class="sxs-lookup"><span data-stu-id="95713-157">(192, 48) to (384, 144)</span></span>|  
  
## <a name="see-also"></a><span data-ttu-id="95713-158">Viz také</span><span class="sxs-lookup"><span data-stu-id="95713-158">See Also</span></span>  
 [<span data-ttu-id="95713-159">Systém souřadnic a transformace</span><span class="sxs-lookup"><span data-stu-id="95713-159">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="95713-160">Maticové znázornění transformací</span><span class="sxs-lookup"><span data-stu-id="95713-160">Matrix Representation of Transformations</span></span>](../../../../docs/framework/winforms/advanced/matrix-representation-of-transformations.md)
