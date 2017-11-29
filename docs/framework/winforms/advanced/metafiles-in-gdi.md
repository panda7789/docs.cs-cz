---
title: "Metasoubory v rozhraní GDI+"
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
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 6b75ceb08df0454172a000d5d1ad15445f685ddf
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="4206b-102">Metasoubory v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="4206b-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4206b-103">poskytuje <xref:System.Drawing.Imaging.Metafile> třídy, aby mohli zaznamenat a zobrazení metasouborů.</span><span class="sxs-lookup"><span data-stu-id="4206b-103"> provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="4206b-104">Metasoubory, označované taky jako bitovou kopii vektoru je image, která je uložena jako posloupnost kreslení příkazy a nastavení.</span><span class="sxs-lookup"><span data-stu-id="4206b-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="4206b-105">Příkazy a nastavení popsané v <xref:System.Drawing.Imaging.Metafile> objekt můžete uložené v paměti nebo uložit do souboru nebo datový proud.</span><span class="sxs-lookup"><span data-stu-id="4206b-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="4206b-106">Formáty metasouborů</span><span class="sxs-lookup"><span data-stu-id="4206b-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4206b-107">můžete zobrazit metasoubory, která jsou uložená v následujících formátech:</span><span class="sxs-lookup"><span data-stu-id="4206b-107"> can display metafiles that have been stored in the following formats:</span></span>  
  
-   <span data-ttu-id="4206b-108">Formát WMF (WMF)</span><span class="sxs-lookup"><span data-stu-id="4206b-108">Windows Metafile (WMF)</span></span>  
  
-   <span data-ttu-id="4206b-109">EMF (Enhanced Metafile)</span><span class="sxs-lookup"><span data-stu-id="4206b-109">Enhanced Metafile (EMF)</span></span>  
  
-   <span data-ttu-id="4206b-110">EMF +</span><span class="sxs-lookup"><span data-stu-id="4206b-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="4206b-111">můžete zaznamenat metasoubory v formáty EMF a EMF +, ale není ve formátu WMF.</span><span class="sxs-lookup"><span data-stu-id="4206b-111"> can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="4206b-112">EMF + je rozšíření EMF, která umožňuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy uložit.</span><span class="sxs-lookup"><span data-stu-id="4206b-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="4206b-113">Existují dvě varianty EMF + format: EMF + pouze a duální EMF +.</span><span class="sxs-lookup"><span data-stu-id="4206b-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="4206b-114">EMF + pouze metasoubory obsahovat pouze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy.</span><span class="sxs-lookup"><span data-stu-id="4206b-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="4206b-115">Takové metasoubory lze zobrazit [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale nejsou nástrojem [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4206b-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="4206b-116">Metasoubory EMF + duální obsahovat [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamy.</span><span class="sxs-lookup"><span data-stu-id="4206b-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="4206b-117">Každý [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamů v duální EMF + metafile je spárován s náhradní [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamu.</span><span class="sxs-lookup"><span data-stu-id="4206b-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="4206b-118">Takové metasoubory lze zobrazit [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nebo [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="4206b-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="4206b-119">Následující příklad zobrazuje metafile, který byl dříve uložili jako soubor.</span><span class="sxs-lookup"><span data-stu-id="4206b-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="4206b-120">S jeho levého horního rohu na se zobrazí metafile (100, 100).</span><span class="sxs-lookup"><span data-stu-id="4206b-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="4206b-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="4206b-121">See Also</span></span>  
 [<span data-ttu-id="4206b-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="4206b-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
