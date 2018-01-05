---
title: "Práce s obrázky, rastrovými obrázky, ikonami a metasoubory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 29c8a4ef0a495d63c0263262857002f09d8c885a
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="05c3e-102">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="05c3e-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="05c3e-103">poskytuje `Bitmap` třídy pro práci s rastrových obrázků a `Metafile` třídy pro práci s obrázky vektoru.</span><span class="sxs-lookup"><span data-stu-id="05c3e-103"> provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="05c3e-104">`Bitmap` a `Metafile` obě třídy dědí `Image` třídy.</span><span class="sxs-lookup"><span data-stu-id="05c3e-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="05c3e-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="05c3e-105">In This Section</span></span>  
 [<span data-ttu-id="05c3e-106">Postupy: Nakreslení existujícího rastrového obrázku na obrazovku</span><span class="sxs-lookup"><span data-stu-id="05c3e-106">How to: Draw an Existing Bitmap to the Screen</span></span>](../../../../docs/framework/winforms/advanced/how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="05c3e-107">Popisuje, jak načíst a kreslení rastrové obrázky.</span><span class="sxs-lookup"><span data-stu-id="05c3e-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="05c3e-108">Postupy: Zavedení a zobrazení metasouborů</span><span class="sxs-lookup"><span data-stu-id="05c3e-108">How to: Load and Display Metafiles</span></span>](../../../../docs/framework/winforms/advanced/how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="05c3e-109">Ukazuje, jak načíst a kreslení metasoubory.</span><span class="sxs-lookup"><span data-stu-id="05c3e-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="05c3e-110">Oříznutí a změna měřítka obrázků v GDI+</span><span class="sxs-lookup"><span data-stu-id="05c3e-110">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="05c3e-111">Vysvětluje, jak oříznout a škálování vektoru a rastrových obrázků.</span><span class="sxs-lookup"><span data-stu-id="05c3e-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="05c3e-112">Postupy: Otáčení, převrácení a zkosení obrázků</span><span class="sxs-lookup"><span data-stu-id="05c3e-112">How to: Rotate, Reflect, and Skew Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="05c3e-113">Popisuje, jak k vykreslení otočený, reflektované a zkreslilo bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="05c3e-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="05c3e-114">Postupy: Použití režimu interpolace pro řízení kvality obrázku během změny měřítka</span><span class="sxs-lookup"><span data-stu-id="05c3e-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="05c3e-115">Ukazuje, jak používat <xref:System.Drawing.Drawing2D.InterpolationMode> výčtu Změna bitové kopie kvality.</span><span class="sxs-lookup"><span data-stu-id="05c3e-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="05c3e-116">Postupy: Vytváření miniatur obrázků</span><span class="sxs-lookup"><span data-stu-id="05c3e-116">How to: Create Thumbnail Images</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-thumbnail-images.md)  
 <span data-ttu-id="05c3e-117">Popisuje postup vytváření miniatur obrázků.</span><span class="sxs-lookup"><span data-stu-id="05c3e-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="05c3e-118">Postupy: Zvýšení výkonu zabráněním automatické změně měřítka</span><span class="sxs-lookup"><span data-stu-id="05c3e-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](../../../../docs/framework/winforms/advanced/how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="05c3e-119">Vysvětluje, jak kreslení obrázku bez automatického měřítka.</span><span class="sxs-lookup"><span data-stu-id="05c3e-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="05c3e-120">Postupy: Čtení metadat obrázku</span><span class="sxs-lookup"><span data-stu-id="05c3e-120">How to: Read Image Metadata</span></span>](../../../../docs/framework/winforms/advanced/how-to-read-image-metadata.md)  
 <span data-ttu-id="05c3e-121">Popisuje, jak číst metadata z bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="05c3e-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="05c3e-122">Postupy: Vytvoření rastrového obrázku za běhu</span><span class="sxs-lookup"><span data-stu-id="05c3e-122">How to: Create a Bitmap at Run Time</span></span>](../../../../docs/framework/winforms/advanced/how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="05c3e-123">Ukazuje, jak k vykreslení rastrového obrázku za běhu.</span><span class="sxs-lookup"><span data-stu-id="05c3e-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="05c3e-124">Postupy: Extrahování ikony přidružené k souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="05c3e-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](../../../../docs/framework/winforms/advanced/how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="05c3e-125">Popisuje, jak extrahovat ikonu, která je vložený prostředek souboru.</span><span class="sxs-lookup"><span data-stu-id="05c3e-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="05c3e-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="05c3e-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="05c3e-127">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="05c3e-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="05c3e-128">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="05c3e-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="05c3e-129">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="05c3e-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="05c3e-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="05c3e-130">Related Sections</span></span>  
 [<span data-ttu-id="05c3e-131">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="05c3e-131">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="05c3e-132">Obsahuje odkazy na témata, která popisují různé typy rastrové obrázky a manipulace s nimi ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="05c3e-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
