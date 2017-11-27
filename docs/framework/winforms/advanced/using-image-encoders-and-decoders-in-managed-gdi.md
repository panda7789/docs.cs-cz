---
title: "Použití kodérů a dekodérů ve spravovaném GDI+"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 64384e3c283b6596e36d5b2bd583a304faf080b4
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="fc2f5-102">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="fc2f5-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="fc2f5-103"><xref:System.Drawing> Obor názvů obsahuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulace s nimi bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="fc2f5-104">Pomocí kódovací moduly obrázku v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], můžete napsat bitové kopie z paměti na disk.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-104">By using image encoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can write images from memory to disk.</span></span> <span data-ttu-id="fc2f5-105">Pomocí dekódovací moduly obrázku v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], bitové kopie můžete načíst z disku do paměti.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-105">By using image decoders in [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)], you can load images from disk into memory.</span></span> <span data-ttu-id="fc2f5-106">Kodér převádí data v <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objekt do formátu souboru určený disk.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="fc2f5-107">Dekodér převádí data v souboru na disku na formát vyžadovanou <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> objekty.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="fc2f5-108">má integrovanou kodérů a dekodérů, které podporují tyto typy souborů:</span><span class="sxs-lookup"><span data-stu-id="fc2f5-108"> has built-in encoders and decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="fc2f5-109">BMP</span><span class="sxs-lookup"><span data-stu-id="fc2f5-109">BMP</span></span>  
  
-   <span data-ttu-id="fc2f5-110">GIF</span><span class="sxs-lookup"><span data-stu-id="fc2f5-110">GIF</span></span>  
  
-   <span data-ttu-id="fc2f5-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="fc2f5-111">JPEG</span></span>  
  
-   <span data-ttu-id="fc2f5-112">PNG</span><span class="sxs-lookup"><span data-stu-id="fc2f5-112">PNG</span></span>  
  
-   <span data-ttu-id="fc2f5-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="fc2f5-113">TIFF</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="fc2f5-114">také obsahuje integrovanou dekódovací moduly, které podporují tyto typy souborů:</span><span class="sxs-lookup"><span data-stu-id="fc2f5-114"> also has built-in decoders that support the following file types:</span></span>  
  
-   <span data-ttu-id="fc2f5-115">WMF</span><span class="sxs-lookup"><span data-stu-id="fc2f5-115">WMF</span></span>  
  
-   <span data-ttu-id="fc2f5-116">EMF</span><span class="sxs-lookup"><span data-stu-id="fc2f5-116">EMF</span></span>  
  
-   <span data-ttu-id="fc2f5-117">IKONA</span><span class="sxs-lookup"><span data-stu-id="fc2f5-117">ICON</span></span>  
  
 <span data-ttu-id="fc2f5-118">Následující témata popisují kodérů a dekodérů podrobněji:</span><span class="sxs-lookup"><span data-stu-id="fc2f5-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fc2f5-119">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fc2f5-119">In This Section</span></span>  
 [<span data-ttu-id="fc2f5-120">Postupy: vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="fc2f5-120">How to: List Installed Encoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-encoders.md)  
 <span data-ttu-id="fc2f5-121">Popisuje, jak seznam kodéry, které jsou dostupné v počítači.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="fc2f5-122">Postupy: vypsání seznamu instalovaných dekodérů</span><span class="sxs-lookup"><span data-stu-id="fc2f5-122">How to: List Installed Decoders</span></span>](../../../../docs/framework/winforms/advanced/how-to-list-installed-decoders.md)  
 <span data-ttu-id="fc2f5-123">Popisuje, jak seznam dekodérů dostupné v počítači.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="fc2f5-124">Postupy: určení parametrů podporovaných kodérem</span><span class="sxs-lookup"><span data-stu-id="fc2f5-124">How to: Determine the Parameters Supported by an Encoder</span></span>](../../../../docs/framework/winforms/advanced/how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="fc2f5-125">Popisuje, jak zobrazit seznam <xref:System.Drawing.Imaging.EncoderParameters> podporovaných kodérem.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="fc2f5-126">Postupy: převod obrázku Bpm na obrázek na obrázek PNG</span><span class="sxs-lookup"><span data-stu-id="fc2f5-126">How to: Convert a BMP image to a PNG image</span></span>](../../../../docs/framework/winforms/advanced/how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="fc2f5-127">Popisuje, jak uložit obrázek ve formátu, jinou bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="fc2f5-128">Postupy: nastavení úrovně komprese JPEG</span><span class="sxs-lookup"><span data-stu-id="fc2f5-128">How to: Set JPEG Compression Level</span></span>](../../../../docs/framework/winforms/advanced/how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="fc2f5-129">Popisuje, jak chcete změnit úroveň kvality obrázku.</span><span class="sxs-lookup"><span data-stu-id="fc2f5-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fc2f5-130">Odkaz</span><span class="sxs-lookup"><span data-stu-id="fc2f5-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="fc2f5-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="fc2f5-131">Related Sections</span></span>  
 [<span data-ttu-id="fc2f5-132">O GDI + spravovaný kód</span><span class="sxs-lookup"><span data-stu-id="fc2f5-132">About GDI+ Managed Code</span></span>](../../../../docs/framework/winforms/advanced/about-gdi-managed-code.md)  
  
 [<span data-ttu-id="fc2f5-133">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="fc2f5-133">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
