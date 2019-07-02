---
title: Použití kodérů a dekodérů ve spravovaném GDI+
ms.date: 03/30/2017
helpviewer_keywords:
- image encoders [Windows Forms], using
- image decoders [Windows Forms], using
ms.assetid: 0e838ea1-4e7e-4334-b882-ab25df607b8b
ms.openlocfilehash: 8cd66f3ce3da462867da9e23c38b3f6d877c058c
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67505087"
---
# <a name="using-image-encoders-and-decoders-in-managed-gdi"></a><span data-ttu-id="e0910-102">Použití kodérů a dekodérů ve spravovaném GDI+</span><span class="sxs-lookup"><span data-stu-id="e0910-102">Using Image Encoders and Decoders in Managed GDI+</span></span>
<span data-ttu-id="e0910-103"><xref:System.Drawing> Obor názvů poskytuje <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> třídy pro ukládání a manipulaci s obrázky.</span><span class="sxs-lookup"><span data-stu-id="e0910-103">The <xref:System.Drawing> namespace provides the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> classes for storing and manipulating images.</span></span> <span data-ttu-id="e0910-104">S použitím kodérů obrázků v GDI +, můžete napsat imagí z paměti na disk.</span><span class="sxs-lookup"><span data-stu-id="e0910-104">By using image encoders in GDI+, you can write images from memory to disk.</span></span> <span data-ttu-id="e0910-105">Pomocí dekódovací moduly obrázku v GDI + můžete načíst obrázky z disku do paměti.</span><span class="sxs-lookup"><span data-stu-id="e0910-105">By using image decoders in GDI+, you can load images from disk into memory.</span></span> <span data-ttu-id="e0910-106">Kodér převádí data do <xref:System.Drawing.Image> nebo <xref:System.Drawing.Bitmap> objektu do souboru ve formátu určený disk.</span><span class="sxs-lookup"><span data-stu-id="e0910-106">An encoder translates the data in an <xref:System.Drawing.Image> or <xref:System.Drawing.Bitmap> object into a designated disk file format.</span></span> <span data-ttu-id="e0910-107">Dekodér převádí data v souboru na disku na formát vyžadované <xref:System.Drawing.Image> a <xref:System.Drawing.Bitmap> objekty.</span><span class="sxs-lookup"><span data-stu-id="e0910-107">A decoder translates the data in a disk file to the format required by the <xref:System.Drawing.Image> and <xref:System.Drawing.Bitmap> objects.</span></span>  
  
 <span data-ttu-id="e0910-108">Rozhraní GDI + má integrované kodérů a dekodérů, které podporují následující typy souborů:</span><span class="sxs-lookup"><span data-stu-id="e0910-108">GDI+ has built-in encoders and decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="e0910-109">BMP</span><span class="sxs-lookup"><span data-stu-id="e0910-109">BMP</span></span>  
  
- <span data-ttu-id="e0910-110">GIF</span><span class="sxs-lookup"><span data-stu-id="e0910-110">GIF</span></span>  
  
- <span data-ttu-id="e0910-111">JPEG</span><span class="sxs-lookup"><span data-stu-id="e0910-111">JPEG</span></span>  
  
- <span data-ttu-id="e0910-112">PNG</span><span class="sxs-lookup"><span data-stu-id="e0910-112">PNG</span></span>  
  
- <span data-ttu-id="e0910-113">TIFF</span><span class="sxs-lookup"><span data-stu-id="e0910-113">TIFF</span></span>  
  
 <span data-ttu-id="e0910-114">Rozhraní GDI + je také integrované dekodérů, které podporují následující typy souborů:</span><span class="sxs-lookup"><span data-stu-id="e0910-114">GDI+ also has built-in decoders that support the following file types:</span></span>  
  
- <span data-ttu-id="e0910-115">WMF</span><span class="sxs-lookup"><span data-stu-id="e0910-115">WMF</span></span>  
  
- <span data-ttu-id="e0910-116">EMF</span><span class="sxs-lookup"><span data-stu-id="e0910-116">EMF</span></span>  
  
- <span data-ttu-id="e0910-117">IKONA</span><span class="sxs-lookup"><span data-stu-id="e0910-117">ICON</span></span>  
  
 <span data-ttu-id="e0910-118">Následující témata popisují kodérů a dekodérů podrobněji:</span><span class="sxs-lookup"><span data-stu-id="e0910-118">The following topics discuss encoders and decoders in more detail:</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="e0910-119">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="e0910-119">In This Section</span></span>  
 [<span data-ttu-id="e0910-120">Postupy: Vypsání seznamu instalovaných kodérů</span><span class="sxs-lookup"><span data-stu-id="e0910-120">How to: List Installed Encoders</span></span>](how-to-list-installed-encoders.md)  
 <span data-ttu-id="e0910-121">Popisuje, jak zobrazit seznam u kodérů dostupných na počítači.</span><span class="sxs-lookup"><span data-stu-id="e0910-121">Describes how to list the encoders available on a computer.</span></span>  
  
 [<span data-ttu-id="e0910-122">Postupy: Vypsání seznamu instalovaných dekodérů</span><span class="sxs-lookup"><span data-stu-id="e0910-122">How to: List Installed Decoders</span></span>](how-to-list-installed-decoders.md)  
 <span data-ttu-id="e0910-123">Popisuje, jak zobrazit seznam dostupných na počítači dekodérů.</span><span class="sxs-lookup"><span data-stu-id="e0910-123">Describes how to list the decoders available on a computer.</span></span>  
  
 [<span data-ttu-id="e0910-124">Postupy: Určuje parametry podporuje kodéru</span><span class="sxs-lookup"><span data-stu-id="e0910-124">How to: Determine the Parameters Supported by an Encoder</span></span>](how-to-determine-the-parameters-supported-by-an-encoder.md)  
 <span data-ttu-id="e0910-125">Popisuje, jak zobrazit seznam <xref:System.Drawing.Imaging.EncoderParameters> podporuje kodéru.</span><span class="sxs-lookup"><span data-stu-id="e0910-125">Describes how to list the <xref:System.Drawing.Imaging.EncoderParameters> supported by an encoder.</span></span>  
  
 [<span data-ttu-id="e0910-126">Postupy: Převod obrázku Bpm na obrázek PNG</span><span class="sxs-lookup"><span data-stu-id="e0910-126">How to: Convert a BMP image to a PNG image</span></span>](how-to-convert-a-bmp-image-to-a-png-image.md)  
 <span data-ttu-id="e0910-127">Popisuje, jak uložit do image ve formátu jiný obrázek.</span><span class="sxs-lookup"><span data-stu-id="e0910-127">Describes how to save a image in a different image format.</span></span>  
  
 [<span data-ttu-id="e0910-128">Postupy: Nastavení úrovně komprese JPEG</span><span class="sxs-lookup"><span data-stu-id="e0910-128">How to: Set JPEG Compression Level</span></span>](how-to-set-jpeg-compression-level.md)  
 <span data-ttu-id="e0910-129">Popisuje, jak změnit úroveň kvality obrázku.</span><span class="sxs-lookup"><span data-stu-id="e0910-129">Describes how to change the quality level of an image.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="e0910-130">Odkaz</span><span class="sxs-lookup"><span data-stu-id="e0910-130">Reference</span></span>  
 <xref:System.Drawing.Image>  
  
 <xref:System.Drawing.Bitmap>  
  
 <xref:System.Drawing.Imaging.ImageCodecInfo>  
  
 <xref:System.Drawing.Imaging.EncoderParameter>  
  
 <xref:System.Drawing.Imaging.Encoder>  
  
## <a name="related-sections"></a><span data-ttu-id="e0910-131">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="e0910-131">Related Sections</span></span>  
 [<span data-ttu-id="e0910-132">Informace o spravovaném kódu GDI+</span><span class="sxs-lookup"><span data-stu-id="e0910-132">About GDI+ Managed Code</span></span>](about-gdi-managed-code.md)  
  
 [<span data-ttu-id="e0910-133">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="e0910-133">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
