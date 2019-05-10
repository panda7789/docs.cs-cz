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
ms.openlocfilehash: f46c24b699aa49db2bc4b8467ce96a125602acec
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64645743"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="d6725-102">Metasoubory v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="d6725-102">Metafiles in GDI+</span></span>
[!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="d6725-103">poskytuje <xref:System.Drawing.Imaging.Metafile> třídy, aby mohli zaznamenat a zobrazení metasouborů.</span><span class="sxs-lookup"><span data-stu-id="d6725-103">provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="d6725-104">Metasoubor zkratka bitovou kopii vektoru je obrázek, který se ukládá jako posloupnost kreslení příkazy a nastavení.</span><span class="sxs-lookup"><span data-stu-id="d6725-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="d6725-105">Příkazy a nastavení popsané v <xref:System.Drawing.Imaging.Metafile> objektu lze uložit v paměti nebo uložit do souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="d6725-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="d6725-106">Formáty metasoubor</span><span class="sxs-lookup"><span data-stu-id="d6725-106">Metafile Formats</span></span>  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="d6725-107">můžete zobrazit metasoubory, které jsou uložené v následujících formátech:</span><span class="sxs-lookup"><span data-stu-id="d6725-107">can display metafiles that have been stored in the following formats:</span></span>  
  
- <span data-ttu-id="d6725-108">Windows Metafile (WMF)</span><span class="sxs-lookup"><span data-stu-id="d6725-108">Windows Metafile (WMF)</span></span>  
  
- <span data-ttu-id="d6725-109">EMF (Enhanced Metafile)</span><span class="sxs-lookup"><span data-stu-id="d6725-109">Enhanced Metafile (EMF)</span></span>  
  
- <span data-ttu-id="d6725-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="d6725-110">EMF+</span></span>  
  
 [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] <span data-ttu-id="d6725-111">můžete zaznamenat metasoubory v EMF a EMF + formáty, ale není ve formátu WMF.</span><span class="sxs-lookup"><span data-stu-id="d6725-111">can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="d6725-112">EMF + je rozšíření EMF umožňující [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy mají být uloženy.</span><span class="sxs-lookup"><span data-stu-id="d6725-112">EMF+ is an extension to EMF that allows [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records to be stored.</span></span> <span data-ttu-id="d6725-113">Existují dvě varianty EMF + formát: EMF + pouze a EMF + duální.</span><span class="sxs-lookup"><span data-stu-id="d6725-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="d6725-114">EMF + pouze metasoubory obsahovat pouze [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznamy.</span><span class="sxs-lookup"><span data-stu-id="d6725-114">EMF+ Only metafiles contain only [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] records.</span></span> <span data-ttu-id="d6725-115">Tyto soubory lze zobrazit v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] , ale ne za [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6725-115">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] but not by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span> <span data-ttu-id="d6725-116">Metasoubory EMF + duální obsahovat [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] a [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamy.</span><span class="sxs-lookup"><span data-stu-id="d6725-116">EMF+ Dual metafiles contain [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] and [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] records.</span></span> <span data-ttu-id="d6725-117">Každý [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] záznam ve dvou EMF + metasoubor se páruje s oblastí alternativu [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] záznamu.</span><span class="sxs-lookup"><span data-stu-id="d6725-117">Each [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] record in an EMF+ Dual metafile is paired with an alternate [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)] record.</span></span> <span data-ttu-id="d6725-118">Tyto soubory lze zobrazit v [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] nebo [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span><span class="sxs-lookup"><span data-stu-id="d6725-118">Such metafiles can be displayed by [!INCLUDE[ndptecgdiplus](../../../../includes/ndptecgdiplus-md.md)] or by [!INCLUDE[ndptecgdi](../../../../includes/ndptecgdi-md.md)].</span></span>  
  
 <span data-ttu-id="d6725-119">Následující příklad zobrazuje metasoubor dříve uložený jako soubor.</span><span class="sxs-lookup"><span data-stu-id="d6725-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="d6725-120">Zobrazí se tento metasoubor pomocí jeho levého horního rohu na (100, 100).</span><span class="sxs-lookup"><span data-stu-id="d6725-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="d6725-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="d6725-121">See also</span></span>

- [<span data-ttu-id="d6725-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="d6725-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
