---
title: Práce s obrázky, rastrovými obrázky, ikonami a metasoubory
ms.date: 03/30/2017
helpviewer_keywords:
- metafiles [Windows Forms], working with
- examples [Windows Forms], bitmaps
- examples [Windows Forms], images
- bitmaps [Windows Forms], working with
- images [Windows Forms], working with
- examples [Windows Forms], metafiles
ms.assetid: a626d701-bd99-4fd8-b92f-7b8f794e042b
ms.openlocfilehash: 61d534f8299c920f656abe4280cc3ea5e609c0b2
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57710456"
---
# <a name="working-with-images-bitmaps-icons-and-metafiles"></a><span data-ttu-id="eeb30-102">Práce s obrázky, rastrovými obrázky, ikonami a metasoubory</span><span class="sxs-lookup"><span data-stu-id="eeb30-102">Working with Images, Bitmaps, Icons, and Metafiles</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="eeb30-103">poskytuje `Bitmap` tříd pro práci s rastrové obrázky a `Metafile` tříd pro práci s imagemi vektoru.</span><span class="sxs-lookup"><span data-stu-id="eeb30-103">provides the `Bitmap` class for working with raster images and the `Metafile` class for working with vector images.</span></span> <span data-ttu-id="eeb30-104">`Bitmap` a `Metafile` obě třídy dědí `Image` třídy.</span><span class="sxs-lookup"><span data-stu-id="eeb30-104">The `Bitmap` and the `Metafile` classes both inherit from the `Image` class.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="eeb30-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="eeb30-105">In This Section</span></span>  
 [<span data-ttu-id="eeb30-106">Postupy: Nakreslení existujícího rastrového obrázku na obrazovku</span><span class="sxs-lookup"><span data-stu-id="eeb30-106">How to: Draw an Existing Bitmap to the Screen</span></span>](how-to-draw-an-existing-bitmap-to-the-screen.md)  
 <span data-ttu-id="eeb30-107">Popisuje, jak načíst a nakreslete rastrových obrázků.</span><span class="sxs-lookup"><span data-stu-id="eeb30-107">Describes how to load and draw bitmaps.</span></span>  
  
 [<span data-ttu-id="eeb30-108">Postupy: Načtení a zobrazení metasouborů</span><span class="sxs-lookup"><span data-stu-id="eeb30-108">How to: Load and Display Metafiles</span></span>](how-to-load-and-display-metafiles.md)  
 <span data-ttu-id="eeb30-109">Ukazuje, jak načíst a metasoubory nakreslit.</span><span class="sxs-lookup"><span data-stu-id="eeb30-109">Shows how to load and draw metafiles.</span></span>  
  
 [<span data-ttu-id="eeb30-110">Oříznutí a změna měřítka obrázků v GDI+</span><span class="sxs-lookup"><span data-stu-id="eeb30-110">Cropping and Scaling Images in GDI+</span></span>](cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="eeb30-111">Vysvětluje, jak oříznout a škálovat vektoru a rastrových obrázků.</span><span class="sxs-lookup"><span data-stu-id="eeb30-111">Explains how to crop and scale vector and raster images.</span></span>  
  
 [<span data-ttu-id="eeb30-112">Postupy: Otáčení, převrácení a zkosení obrázků</span><span class="sxs-lookup"><span data-stu-id="eeb30-112">How to: Rotate, Reflect, and Skew Images</span></span>](how-to-rotate-reflect-and-skew-images.md)  
 <span data-ttu-id="eeb30-113">Popisuje, jak nakreslit otočený, zrcadlených a výrazně nerovnoměrnou distribucí Image.</span><span class="sxs-lookup"><span data-stu-id="eeb30-113">Describes how to draw rotated, reflected and skewed images.</span></span>  
  
 [<span data-ttu-id="eeb30-114">Postupy: Použití režimu interpolace pro řízení kvality obrázku během změny měřítka</span><span class="sxs-lookup"><span data-stu-id="eeb30-114">How to: Use Interpolation Mode to Control Image Quality During Scaling</span></span>](how-to-use-interpolation-mode-to-control-image-quality-during-scaling.md)  
 <span data-ttu-id="eeb30-115">Ukazuje způsob použití <xref:System.Drawing.Drawing2D.InterpolationMode> výčet změnit kvality obrázku.</span><span class="sxs-lookup"><span data-stu-id="eeb30-115">Shows how to use the <xref:System.Drawing.Drawing2D.InterpolationMode> enumeration to change image quality.</span></span>  
  
 [<span data-ttu-id="eeb30-116">Postupy: Vytváření miniatur obrázků</span><span class="sxs-lookup"><span data-stu-id="eeb30-116">How to: Create Thumbnail Images</span></span>](how-to-create-thumbnail-images.md)  
 <span data-ttu-id="eeb30-117">Popisuje postup vytvoření obrázků miniatur.</span><span class="sxs-lookup"><span data-stu-id="eeb30-117">Describes how to create thumbnail images.</span></span>  
  
 [<span data-ttu-id="eeb30-118">Postupy: Zvýšení výkonu zabráněním automatické změně měřítka</span><span class="sxs-lookup"><span data-stu-id="eeb30-118">How to: Improve Performance by Avoiding Automatic Scaling</span></span>](how-to-improve-performance-by-avoiding-automatic-scaling.md)  
 <span data-ttu-id="eeb30-119">Vysvětluje způsob vykreslení obrázku bez automatického škálování.</span><span class="sxs-lookup"><span data-stu-id="eeb30-119">Explains how to draw an image without automatic scaling.</span></span>  
  
 [<span data-ttu-id="eeb30-120">Postupy: Čtení metadat obrázku</span><span class="sxs-lookup"><span data-stu-id="eeb30-120">How to: Read Image Metadata</span></span>](how-to-read-image-metadata.md)  
 <span data-ttu-id="eeb30-121">Popisuje postup při čtení metadat z image.</span><span class="sxs-lookup"><span data-stu-id="eeb30-121">Describes how to read metadata from an image.</span></span>  
  
 [<span data-ttu-id="eeb30-122">Postupy: Vytvoření rastrového obrázku za běhu</span><span class="sxs-lookup"><span data-stu-id="eeb30-122">How to: Create a Bitmap at Run Time</span></span>](how-to-create-a-bitmap-at-run-time.md)  
 <span data-ttu-id="eeb30-123">Ukazuje, jak nakreslit za běhu rastrový obrázek.</span><span class="sxs-lookup"><span data-stu-id="eeb30-123">Shows how to draw a bitmap at runtime.</span></span>  
  
 [<span data-ttu-id="eeb30-124">Postupy: Extrahování ikony přidružené k souboru v modelu Windows Forms</span><span class="sxs-lookup"><span data-stu-id="eeb30-124">How to: Extract the Icon Associated with a File in Windows Forms</span></span>](how-to-extract-the-icon-associated-with-a-file-in-windows-forms.md)  
 <span data-ttu-id="eeb30-125">Popisuje, jak extrahovat, který je vloženým prostředkem souboru ikony.</span><span class="sxs-lookup"><span data-stu-id="eeb30-125">Describes how to extract an icon that is an embedded resource of a file.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="eeb30-126">Odkaz</span><span class="sxs-lookup"><span data-stu-id="eeb30-126">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="eeb30-127">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="eeb30-127">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Imaging.Metafile>  
 <span data-ttu-id="eeb30-128">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="eeb30-128">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="eeb30-129">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="eeb30-129">Describes this class and has links to all of its members.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="eeb30-130">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="eeb30-130">Related Sections</span></span>  
 [<span data-ttu-id="eeb30-131">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="eeb30-131">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)  
 <span data-ttu-id="eeb30-132">Obsahuje odkazy na témata, které popisují různé typy rastrových obrázků a manipulaci s nimi ve svých aplikacích.</span><span class="sxs-lookup"><span data-stu-id="eeb30-132">Contains links to topics that discuss different types of bitmaps and manipulating them in your applications.</span></span>
