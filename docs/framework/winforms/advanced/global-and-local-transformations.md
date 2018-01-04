---
title: "Globální a místní transformace"
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
- matrices [Windows Forms], using transformations
- transformations [Windows Forms], global
- transformations [Windows Forms], local
ms.assetid: b601d66d-d572-4f11-9d2e-92f0dc8893f3
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8e8d05bd0c3e76d643d56b652c8849eef1045ea8
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="global-and-local-transformations"></a><span data-ttu-id="92148-102">Globální a místní transformace</span><span class="sxs-lookup"><span data-stu-id="92148-102">Global and Local Transformations</span></span>
<span data-ttu-id="92148-103">Globální transformaci je transformaci, která platí pro každou položku vykreslovány pomocí danou <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="92148-103">A global transformation is a transformation that applies to every item drawn by a given <xref:System.Drawing.Graphics> object.</span></span> <span data-ttu-id="92148-104">Místní transformace spočívá v tom, transformaci, která platí pro konkrétní položky, které se mají vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="92148-104">In contrast, a local transformation is a transformation that applies to a specific item to be drawn.</span></span>  
  
## <a name="global-transformations"></a><span data-ttu-id="92148-105">Globální transformace</span><span class="sxs-lookup"><span data-stu-id="92148-105">Global Transformations</span></span>  
 <span data-ttu-id="92148-106">Pokud chcete vytvořit globální transformace, vytvořit <xref:System.Drawing.Graphics> objektu a poté pracovat s jeho <xref:System.Drawing.Graphics.Transform%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="92148-106">To create a global transformation, construct a <xref:System.Drawing.Graphics> object, and then manipulate its <xref:System.Drawing.Graphics.Transform%2A> property.</span></span> <span data-ttu-id="92148-107"><xref:System.Drawing.Graphics.Transform%2A> Vlastnost je <xref:System.Drawing.Drawing2D.Matrix> objektu, takže může uchovávat žádné pořadí afinní transformace.</span><span class="sxs-lookup"><span data-stu-id="92148-107">The <xref:System.Drawing.Graphics.Transform%2A> property is a <xref:System.Drawing.Drawing2D.Matrix> object, so it can hold any sequence of affine transformations.</span></span> <span data-ttu-id="92148-108">Transformace uložené v <xref:System.Drawing.Graphics.Transform%2A> vlastnost nazývá Světové transformace.</span><span class="sxs-lookup"><span data-stu-id="92148-108">The transformation stored in the <xref:System.Drawing.Graphics.Transform%2A> property is called the world transformation.</span></span> <span data-ttu-id="92148-109"><xref:System.Drawing.Graphics> Třída poskytuje několik metod pro vytváření kompozitních Světové transformace: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, a <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span><span class="sxs-lookup"><span data-stu-id="92148-109">The <xref:System.Drawing.Graphics> class provides several methods for building up a composite world transformation: <xref:System.Drawing.Graphics.MultiplyTransform%2A>, <xref:System.Drawing.Graphics.RotateTransform%2A>, <xref:System.Drawing.Graphics.ScaleTransform%2A>, and <xref:System.Drawing.Graphics.TranslateTransform%2A>.</span></span> <span data-ttu-id="92148-110">Následující příklad nevykresluje elipsy dvakrát: jednou před vytvořením Světové transformace a jednou po.</span><span class="sxs-lookup"><span data-stu-id="92148-110">The following example draws an ellipse twice: once before creating a world transformation and once after.</span></span> <span data-ttu-id="92148-111">Transformace nejprve škáluje faktorem 0,5 ve směru osy y, pak překládá 50 jednotky ve směru osy x a pak otočí 30 stupňů.</span><span class="sxs-lookup"><span data-stu-id="92148-111">The transformation first scales by a factor of 0.5 in the y direction, then translates 50 units in the x direction, and then rotates 30 degrees.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.CoordinateSystems#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#21)]  
  
 <span data-ttu-id="92148-112">Následující obrázek znázorňuje matic zahrnutých v transformaci.</span><span class="sxs-lookup"><span data-stu-id="92148-112">The following illustration shows the matrices involved in the transformation.</span></span>  
  
 <span data-ttu-id="92148-113">![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span><span class="sxs-lookup"><span data-stu-id="92148-113">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art14.gif "AboutGdip05_art14")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="92148-114">V předchozím příkladu se třemi tečkami otočen o původu souřadnicový systém, který je v levém horním rohu klientské oblasti.</span><span class="sxs-lookup"><span data-stu-id="92148-114">In the preceding example, the ellipse is rotated about the origin of the coordinate system, which is at the upper-left corner of the client area.</span></span> <span data-ttu-id="92148-115">To vytváří jiné výsledky než otáčení se třemi tečkami o vlastní center.</span><span class="sxs-lookup"><span data-stu-id="92148-115">This produces a different result than rotating the ellipse about its own center.</span></span>  
  
## <a name="local-transformations"></a><span data-ttu-id="92148-116">Místní transformace</span><span class="sxs-lookup"><span data-stu-id="92148-116">Local Transformations</span></span>  
 <span data-ttu-id="92148-117">Místní transformace platí pro konkrétní položky, které se mají vykreslovat.</span><span class="sxs-lookup"><span data-stu-id="92148-117">A local transformation applies to a specific item to be drawn.</span></span> <span data-ttu-id="92148-118">Například <xref:System.Drawing.Drawing2D.GraphicsPath> objekt má <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> metoda, která umožňuje transformovat datových bodů dané cesty.</span><span class="sxs-lookup"><span data-stu-id="92148-118">For example, a <xref:System.Drawing.Drawing2D.GraphicsPath> object has a <xref:System.Drawing.Drawing2D.GraphicsPath.Transform%2A> method that allows you to transform the data points of that path.</span></span> <span data-ttu-id="92148-119">Následující příklad nevykresluje obdélník se žádná transformace a cestu otočení transformace.</span><span class="sxs-lookup"><span data-stu-id="92148-119">The following example draws a rectangle with no transformation and a path with a rotation transformation.</span></span> <span data-ttu-id="92148-120">(Předpokládá, že neexistuje žádná Světové transformace malá a velká písmena.)</span><span class="sxs-lookup"><span data-stu-id="92148-120">(Assume that there is no world transformation.)</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#22)]
 [!code-vb[System.Drawing.CoordinateSystems#22](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#22)]  
  
 <span data-ttu-id="92148-121">Světové transformace s místní transformace k dosažení různých výsledků můžete kombinovat.</span><span class="sxs-lookup"><span data-stu-id="92148-121">You can combine the world transformation with local transformations to achieve a variety of results.</span></span> <span data-ttu-id="92148-122">Například můžete Světové transformace revidování souřadnicový systém a místní transformace použít otočit a škálovat objekty vykreslovat na nový systém souřadnic.</span><span class="sxs-lookup"><span data-stu-id="92148-122">For example, you can use the world transformation to revise the coordinate system and use local transformations to rotate and scale objects drawn on the new coordinate system.</span></span>  
  
 <span data-ttu-id="92148-123">Předpokládejme, že chcete souřadnicový systém, který má jeho počátek 200 pixelů od levého okraje klientské oblasti a 150 pixelů z horní části oblasti klienta.</span><span class="sxs-lookup"><span data-stu-id="92148-123">Suppose you want a coordinate system that has its origin 200 pixels from the left edge of the client area and 150 pixels from the top of the client area.</span></span> <span data-ttu-id="92148-124">Kromě toho předpokládá, že chcete jednotku, která se pixelů, s osou x tvořenou hodnotami odkazující na ose y míří nahoru a doprava.</span><span class="sxs-lookup"><span data-stu-id="92148-124">Furthermore, assume that you want the unit of measure to be the pixel, with the x-axis pointing to the right and the y-axis pointing up.</span></span> <span data-ttu-id="92148-125">Výchozí souřadnicový systém má osy y míří dolů, takže budete muset provádět odraz na vodorovné ose.</span><span class="sxs-lookup"><span data-stu-id="92148-125">The default coordinate system has the y-axis pointing down, so you need to perform a reflection across the horizontal axis.</span></span> <span data-ttu-id="92148-126">Následující obrázek znázorňuje matice takové reflexe.</span><span class="sxs-lookup"><span data-stu-id="92148-126">The following illustration shows the matrix of such a reflection.</span></span>  
  
 <span data-ttu-id="92148-127">![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span><span class="sxs-lookup"><span data-stu-id="92148-127">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art15.gif "AboutGdip05_art15")</span></span>  
  
 <span data-ttu-id="92148-128">V dalším kroku předpokládá, že je třeba provést 200 jednotky překladu napravo a 150 jednotky dolů.</span><span class="sxs-lookup"><span data-stu-id="92148-128">Next, assume you need to perform a translation 200 units to the right and 150 units down.</span></span>  
  
 <span data-ttu-id="92148-129">Následující příklad určuje souřadnicový systém právě popsaného nastavení Světové transformace <xref:System.Drawing.Graphics> objektu.</span><span class="sxs-lookup"><span data-stu-id="92148-129">The following example establishes the coordinate system just described by setting the world transformation of a <xref:System.Drawing.Graphics> object.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#23)]
 [!code-vb[System.Drawing.CoordinateSystems#23](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#23)]  
  
 <span data-ttu-id="92148-130">Následující kód (umístit na konci v předchozím příkladu) vytvoří cestu, která se skládá z jedné obdélníku s jeho levém dolním rohu na počátku nové souřadnicový systém.</span><span class="sxs-lookup"><span data-stu-id="92148-130">The following code (placed at the end of the preceding example) creates a path that consists of a single rectangle with its lower-left corner at the origin of the new coordinate system.</span></span> <span data-ttu-id="92148-131">Rámeček je vyplněna jednou se žádná místní transformace a jednou s místní transformace.</span><span class="sxs-lookup"><span data-stu-id="92148-131">The rectangle is filled once with no local transformation and once with a local transformation.</span></span> <span data-ttu-id="92148-132">Místní transformace se skládá z vodorovné škálování faktorem 2 následuje rotaci 30 stupňů.</span><span class="sxs-lookup"><span data-stu-id="92148-132">The local transformation consists of a horizontal scaling by a factor of 2 followed by a 30-degree rotation.</span></span>  
  
 [!code-csharp[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/CS/Class1.cs#24)]
 [!code-vb[System.Drawing.CoordinateSystems#24](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.CoordinateSystems/VB/Class1.vb#24)]  
  
 <span data-ttu-id="92148-133">Následující obrázek znázorňuje nový systém souřadnic a dva obdélníky.</span><span class="sxs-lookup"><span data-stu-id="92148-133">The following illustration shows the new coordinate system and the two rectangles.</span></span>  
  
 <span data-ttu-id="92148-134">![Transformace](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span><span class="sxs-lookup"><span data-stu-id="92148-134">![Transformations](../../../../docs/framework/winforms/advanced/media/aboutgdip05-art16.gif "AboutGdip05_art16")</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="92148-135">Viz také</span><span class="sxs-lookup"><span data-stu-id="92148-135">See Also</span></span>  
 [<span data-ttu-id="92148-136">Systém souřadnic a transformace</span><span class="sxs-lookup"><span data-stu-id="92148-136">Coordinate Systems and Transformations</span></span>](../../../../docs/framework/winforms/advanced/coordinate-systems-and-transformations.md)  
 [<span data-ttu-id="92148-137">Použití transformací ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="92148-137">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)
