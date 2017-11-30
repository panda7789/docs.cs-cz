---
title: "Obrázky, rastrové obrázky a metasoubory"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- metafiles [Windows Forms], about metafiles
- bitmaps [Windows Forms], about bitmaps
- images [Windows Forms], about images
- Windows Forms, images
ms.assetid: 7152b45b-a55c-49bc-8c78-ae002a844f71
caps.latest.revision: "16"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 3f48027e413f9573158cfa2c3748fc93408b3f83
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="images-bitmaps-and-metafiles"></a><span data-ttu-id="ec3ad-102">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="ec3ad-102">Images, Bitmaps, and Metafiles</span></span>
<span data-ttu-id="ec3ad-103">`Image` Třída je abstraktní základní třída, která poskytuje metody pro práci s rastrových obrázků (Bitmap) a vektoru bitové kopie (metasoubory).</span><span class="sxs-lookup"><span data-stu-id="ec3ad-103">The `Image` class is an abstract base class that provides methods for working with raster images (bitmaps) and vector images (metafiles).</span></span> <span data-ttu-id="ec3ad-104">`Bitmap` Třídy a <xref:System.Drawing.Imaging.Metafile> obě dědí z třídy `Image` třídy.</span><span class="sxs-lookup"><span data-stu-id="ec3ad-104">The `Bitmap` class and the <xref:System.Drawing.Imaging.Metafile> class both inherit from the `Image` class.</span></span> <span data-ttu-id="ec3ad-105">`Bitmap` Třída rozšíří na možnosti `Image` třída tím, že poskytuje další metody pro načítání, ukládání a manipulace s nimi rastrových obrázků.</span><span class="sxs-lookup"><span data-stu-id="ec3ad-105">The `Bitmap` class expands on the capabilities of the `Image` class by providing additional methods for loading, saving, and manipulating raster images.</span></span> <span data-ttu-id="ec3ad-106"><xref:System.Drawing.Imaging.Metafile> Třída rozšíří na možnosti `Image` třída tím, že poskytuje další metody pro zaznamenání a zkoumání vektoru bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="ec3ad-106">The <xref:System.Drawing.Imaging.Metafile> class expands on the capabilities of the `Image` class by providing additional methods for recording and examining vector images.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="ec3ad-107">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="ec3ad-107">In This Section</span></span>  
 [<span data-ttu-id="ec3ad-108">Typy rastrových obrázků</span><span class="sxs-lookup"><span data-stu-id="ec3ad-108">Types of Bitmaps</span></span>](../../../../docs/framework/winforms/advanced/types-of-bitmaps.md)  
 <span data-ttu-id="ec3ad-109">Popisuje různé formátů obrázku.</span><span class="sxs-lookup"><span data-stu-id="ec3ad-109">Discusses the various image formats.</span></span>  
  
 [<span data-ttu-id="ec3ad-110">Metasoubory v rozhraní GDI +</span><span class="sxs-lookup"><span data-stu-id="ec3ad-110">Metafiles in GDI+</span></span>](../../../../docs/framework/winforms/advanced/metafiles-in-gdi.md)  
 <span data-ttu-id="ec3ad-111">Popisuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] podpora metasoubory.</span><span class="sxs-lookup"><span data-stu-id="ec3ad-111">Discusses [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] support for metafiles.</span></span>  
  
 [<span data-ttu-id="ec3ad-112">Kreslení, umisťování a klonování obrázků v GDI +</span><span class="sxs-lookup"><span data-stu-id="ec3ad-112">Drawing, Positioning, and Cloning Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/drawing-positioning-and-cloning-images-in-gdi.md)  
 <span data-ttu-id="ec3ad-113">Popisuje metody pro kreslení vektoru a rastrových obrázků se spravovaným kódem.</span><span class="sxs-lookup"><span data-stu-id="ec3ad-113">Discusses methods for drawing vector and raster images with managed code.</span></span>  
  
 [<span data-ttu-id="ec3ad-114">Oříznutí a změna měřítka obrázků v GDI +</span><span class="sxs-lookup"><span data-stu-id="ec3ad-114">Cropping and Scaling Images in GDI+</span></span>](../../../../docs/framework/winforms/advanced/cropping-and-scaling-images-in-gdi.md)  
 <span data-ttu-id="ec3ad-115">Popisuje metody pro oříznutí a změna velikosti vektoru a rastrových obrázků se spravovaným kódem</span><span class="sxs-lookup"><span data-stu-id="ec3ad-115">Discusses methods for cropping and scaling vector and raster images with managed code</span></span>  
  
## <a name="reference"></a><span data-ttu-id="ec3ad-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="ec3ad-116">Reference</span></span>  
 <xref:System.Drawing.Image>  
 <span data-ttu-id="ec3ad-117">Tato třída popisuje a obsahuje odkazy na všechny její členy.</span><span class="sxs-lookup"><span data-stu-id="ec3ad-117">Describes this class and has links to all of its members.</span></span>  
  
 <xref:System.Drawing.Bitmap>  
 <span data-ttu-id="ec3ad-118">Tato třída popisuje a obsahuje odkazy na všechny její členy</span><span class="sxs-lookup"><span data-stu-id="ec3ad-118">Describes this class and has links to all of its members</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="ec3ad-119">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="ec3ad-119">Related Sections</span></span>  
 [<span data-ttu-id="ec3ad-120">Práce s obrázky, rastrové obrázky, ikony a metasoubory</span><span class="sxs-lookup"><span data-stu-id="ec3ad-120">Working with Images, Bitmaps, Icons, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/working-with-images-bitmaps-icons-and-metafiles.md)  
 <span data-ttu-id="ec3ad-121">Obsahuje odkazy na témata, která ukazují, jak pomocí bitové kopie ve vaší aplikaci.</span><span class="sxs-lookup"><span data-stu-id="ec3ad-121">Contains links to topics that demonstrate how to use images in your application.</span></span>
