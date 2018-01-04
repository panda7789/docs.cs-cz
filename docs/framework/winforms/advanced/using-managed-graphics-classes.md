---
title: "Použití spravovaných grafických tříd"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- GDI+, managed classes
- graphics [Windows Forms], using in Windows Forms
- graphics [Windows Forms], managed classes
ms.assetid: e6d1a42d-2100-46aa-97e6-a5ddc0baaae5
caps.latest.revision: "21"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 2a34e2726182c194882d94fe4b8d1164993d8284
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="using-managed-graphics-classes"></a><span data-ttu-id="06ac1-102">Použití spravovaných grafických tříd</span><span class="sxs-lookup"><span data-stu-id="06ac1-102">Using Managed Graphics Classes</span></span>
<span data-ttu-id="06ac1-103">Následující témata popisují postup použití [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] rozhraní API v rámci spravované třídy.</span><span class="sxs-lookup"><span data-stu-id="06ac1-103">The following topics describe how to use the [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] API in the managed class framework.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="06ac1-104">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="06ac1-104">In This Section</span></span>  
 [<span data-ttu-id="06ac1-105">Začínáme s programováním grafiky</span><span class="sxs-lookup"><span data-stu-id="06ac1-105">Getting Started with Graphics Programming</span></span>](../../../../docs/framework/winforms/advanced/getting-started-with-graphics-programming.md)  
 <span data-ttu-id="06ac1-106">Popisuje, jak provádět základní úlohy s [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span><span class="sxs-lookup"><span data-stu-id="06ac1-106">Describes how to accomplish basic tasks with [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)].</span></span>  
  
 [<span data-ttu-id="06ac1-107">Kreslení čar a obrazců pomocí pera</span><span class="sxs-lookup"><span data-stu-id="06ac1-107">Using a Pen to Draw Lines and Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-pen-to-draw-lines-and-shapes.md)  
 <span data-ttu-id="06ac1-108">Demonstruje postup vytvoření pera a použít ho k vykreslení celou řadu čar a tvarů.</span><span class="sxs-lookup"><span data-stu-id="06ac1-108">Demonstrates how to construct a pen and use it to draw a variety of lines and shapes.</span></span>  
  
 [<span data-ttu-id="06ac1-109">Použití štětce k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="06ac1-109">Using a Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-brush-to-fill-shapes.md)  
 <span data-ttu-id="06ac1-110">Ukazuje, jak vytvořit štětce a vyplňte tvarů s různými účinky.</span><span class="sxs-lookup"><span data-stu-id="06ac1-110">Demonstrates how to construct a brush and fill shapes with a variety of effects.</span></span>  
  
 [<span data-ttu-id="06ac1-111">Použití štětce přechodu k vyplnění obrazců</span><span class="sxs-lookup"><span data-stu-id="06ac1-111">Using a Gradient Brush to Fill Shapes</span></span>](../../../../docs/framework/winforms/advanced/using-a-gradient-brush-to-fill-shapes.md)  
 <span data-ttu-id="06ac1-112">Ukazuje, jak vytvořit a používat různé typy štětce přechodu.</span><span class="sxs-lookup"><span data-stu-id="06ac1-112">Shows how to create and use different types of gradient brushes.</span></span>  
  
 [<span data-ttu-id="06ac1-113">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="06ac1-113">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="06ac1-114">Ukazuje, jak vytvořit a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="06ac1-114">Demonstrates how to construct and manipulate images.</span></span>  
  
 [<span data-ttu-id="06ac1-115">Alfa míchání čar a výplní</span><span class="sxs-lookup"><span data-stu-id="06ac1-115">Alpha Blending Lines and Fills</span></span>](../../../../docs/framework/winforms/advanced/alpha-blending-lines-and-fills.md)  
 <span data-ttu-id="06ac1-116">Ukazuje, jak zajistit průhlednost pro tvarů a řádky.</span><span class="sxs-lookup"><span data-stu-id="06ac1-116">Demonstrates how to achieve transparency for shapes and lines.</span></span>  
  
 [<span data-ttu-id="06ac1-117">Použití písem a textu</span><span class="sxs-lookup"><span data-stu-id="06ac1-117">Using Fonts and Text</span></span>](../../../../docs/framework/winforms/advanced/using-fonts-and-text.md)  
 <span data-ttu-id="06ac1-118">Ukazuje, jak kreslení textu a použití písem a rodiny písem.</span><span class="sxs-lookup"><span data-stu-id="06ac1-118">Shows how to draw text and use fonts and font families.</span></span>  
  
 [<span data-ttu-id="06ac1-119">Sestavování a kreslení křivek</span><span class="sxs-lookup"><span data-stu-id="06ac1-119">Constructing and Drawing Curves</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-curves.md)  
 <span data-ttu-id="06ac1-120">Ukazuje, jak kreslení základních a Bézierovy křivky.</span><span class="sxs-lookup"><span data-stu-id="06ac1-120">Shows how to draw Cardinal and Bezier splines.</span></span>  
  
 [<span data-ttu-id="06ac1-121">Sestavování a kreslení cest</span><span class="sxs-lookup"><span data-stu-id="06ac1-121">Constructing and Drawing Paths</span></span>](../../../../docs/framework/winforms/advanced/constructing-and-drawing-paths.md)  
 <span data-ttu-id="06ac1-122">Ukazuje, jak vytváření obrázků pomocí cesty.</span><span class="sxs-lookup"><span data-stu-id="06ac1-122">Shows how to create figures using paths.</span></span>  
  
 [<span data-ttu-id="06ac1-123">Použití transformací ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="06ac1-123">Using Transformations in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-transformations-in-managed-gdi.md)  
 <span data-ttu-id="06ac1-124">Demonstruje maticové transformace.</span><span class="sxs-lookup"><span data-stu-id="06ac1-124">Demonstrates matrix transformations.</span></span>  
  
 [<span data-ttu-id="06ac1-125">Použití grafických kontejnerů</span><span class="sxs-lookup"><span data-stu-id="06ac1-125">Using Graphics Containers</span></span>](../../../../docs/framework/winforms/advanced/using-graphics-containers.md)  
 <span data-ttu-id="06ac1-126">Ukazuje, jak spravovat grafiky objekt stavu a vnořených grafických kontejnerů.</span><span class="sxs-lookup"><span data-stu-id="06ac1-126">Shows how to manage graphics object state and nested graphics containers.</span></span>  
  
 [<span data-ttu-id="06ac1-127">Použití oblastí</span><span class="sxs-lookup"><span data-stu-id="06ac1-127">Using Regions</span></span>](../../../../docs/framework/winforms/advanced/using-regions.md)  
 <span data-ttu-id="06ac1-128">Demonstruje přístupů testování a výstřižek s oblastí.</span><span class="sxs-lookup"><span data-stu-id="06ac1-128">Demonstrates hit testing and clipping with regions.</span></span>  
  
 [<span data-ttu-id="06ac1-129">Přebarvení obrázků</span><span class="sxs-lookup"><span data-stu-id="06ac1-129">Recoloring Images</span></span>](../../../../docs/framework/winforms/advanced/recoloring-images.md)  
 <span data-ttu-id="06ac1-130">Ukazuje různé aspekty manipulace s barvy.</span><span class="sxs-lookup"><span data-stu-id="06ac1-130">Demonstrates various aspects of manipulating colors.</span></span>  
  
 [<span data-ttu-id="06ac1-131">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="06ac1-131">Using Image Encoders and Decoders in Managed GDI+</span></span>](../../../../docs/framework/winforms/advanced/using-image-encoders-and-decoders-in-managed-gdi.md)  
 <span data-ttu-id="06ac1-132">Zobrazit použití kodérů a dekodérů k manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="06ac1-132">Show how to use image encoders and decoders to manipulate images.</span></span>  
  
 [<span data-ttu-id="06ac1-133">Grafiky s dvojitou vyrovnávací pamětí</span><span class="sxs-lookup"><span data-stu-id="06ac1-133">Double Buffered Graphics</span></span>](../../../../docs/framework/winforms/advanced/double-buffered-graphics.md)  
 <span data-ttu-id="06ac1-134">Ukazuje, jak snížit blikání pomocí dvojité vyrovnávací paměti.</span><span class="sxs-lookup"><span data-stu-id="06ac1-134">Demonstrates how to reduce flicker with double buffering.</span></span>
