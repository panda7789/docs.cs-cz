---
title: Metasoubory v rozhraní GDI+
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [Windows Forms], metafiles
- GDI+, metafiles
- metafiles
ms.assetid: 51da872c-c783-440f-8bf6-1e580a966c31
ms.openlocfilehash: 73cacb7f701768b42121c31cfbc4f26905961231
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33525088"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="1c8c0-102">Metasoubory v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="1c8c0-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="1c8c0-103"> poskytuje <xref:System.Drawing.Imaging.Metafile> třídy, aby mohli zaznamenat a zobrazení metasouborů.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-103"> provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="1c8c0-104">Metasoubory, označované taky jako bitovou kopii vektoru je image, která je uložena jako posloupnost kreslení příkazy a nastavení.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="1c8c0-105">Příkazy a nastavení popsané v <xref:System.Drawing.Imaging.Metafile> objekt můžete uložené v paměti nebo uložit do souboru nebo datový proud.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="1c8c0-106">Formáty metasouborů</span><span class="sxs-lookup"><span data-stu-id="1c8c0-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="1c8c0-107"> můžete zobrazit metasoubory, která jsou uložená v následujících formátech:</span><span class="sxs-lookup"><span data-stu-id="1c8c0-107"> can display metafiles that have been stored in the following formats:</span></span>  
  
-   <span data-ttu-id="1c8c0-108">Formát WMF (WMF)</span><span class="sxs-lookup"><span data-stu-id="1c8c0-108">Windows Metafile (WMF)</span></span>  
  
-   <span data-ttu-id="1c8c0-109">EMF (Enhanced Metafile)</span><span class="sxs-lookup"><span data-stu-id="1c8c0-109">Enhanced Metafile (EMF)</span></span>  
  
-   <span data-ttu-id="1c8c0-110">EMF +</span><span class="sxs-lookup"><span data-stu-id="1c8c0-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)]<span data-ttu-id="1c8c0-111"> můžete zaznamenat metasoubory v formáty EMF a EMF +, ale není ve formátu WMF.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-111"> can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="1c8c0-112">EMF + je rozšíření EMF, která umožňuje [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy uložit.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="1c8c0-113">Existují dvě varianty EMF + format: EMF + pouze a duální EMF +.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="1c8c0-114">EMF + pouze metasoubory obsahovat pouze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="1c8c0-115">Takové metasoubory lze zobrazit [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale nejsou nástrojem [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c8c0-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="1c8c0-116">Metasoubory EMF + duální obsahovat [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamy.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="1c8c0-117">Každý [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamů v duální EMF + metafile je spárován s náhradní [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamu.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="1c8c0-118">Takové metasoubory lze zobrazit [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nebo [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1c8c0-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="1c8c0-119">Následující příklad zobrazuje metafile, který byl dříve uložili jako soubor.</span><span class="sxs-lookup"><span data-stu-id="1c8c0-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="1c8c0-120">S jeho levého horního rohu na se zobrazí metafile (100, 100).</span><span class="sxs-lookup"><span data-stu-id="1c8c0-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="1c8c0-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c8c0-121">See Also</span></span>  
 [<span data-ttu-id="1c8c0-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="1c8c0-122">Images, Bitmaps, and Metafiles</span></span>](../../../../docs/framework/winforms/advanced/images-bitmaps-and-metafiles.md)
