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
ms.openlocfilehash: df54289722cf12bad840722c6eafdaa43279a5dc
ms.sourcegitcommit: b1cfd260928d464d91e20121f9bdba7611c94d71
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/02/2019
ms.locfileid: "67504582"
---
# <a name="metafiles-in-gdi"></a><span data-ttu-id="5ac00-102">Metasoubory v rozhraní GDI+</span><span class="sxs-lookup"><span data-stu-id="5ac00-102">Metafiles in GDI+</span></span>
<span data-ttu-id="5ac00-103">Poskytuje rozhraní GDI + <xref:System.Drawing.Imaging.Metafile> třídy, aby mohli zaznamenat a zobrazení metasouborů.</span><span class="sxs-lookup"><span data-stu-id="5ac00-103">GDI+ provides the <xref:System.Drawing.Imaging.Metafile> class so that you can record and display metafiles.</span></span> <span data-ttu-id="5ac00-104">Metasoubor zkratka bitovou kopii vektoru je obrázek, který se ukládá jako posloupnost kreslení příkazy a nastavení.</span><span class="sxs-lookup"><span data-stu-id="5ac00-104">A metafile, also called a vector image, is an image that is stored as a sequence of drawing commands and settings.</span></span> <span data-ttu-id="5ac00-105">Příkazy a nastavení popsané v <xref:System.Drawing.Imaging.Metafile> objektu lze uložit v paměti nebo uložit do souboru nebo datového proudu.</span><span class="sxs-lookup"><span data-stu-id="5ac00-105">The commands and settings recorded in a <xref:System.Drawing.Imaging.Metafile> object can be stored in memory or saved to a file or stream.</span></span>  
  
## <a name="metafile-formats"></a><span data-ttu-id="5ac00-106">Formáty metasoubor</span><span class="sxs-lookup"><span data-stu-id="5ac00-106">Metafile Formats</span></span>  
 <span data-ttu-id="5ac00-107">Rozhraní GDI + můžete zobrazení metasouborů uložené v následujících formátech:</span><span class="sxs-lookup"><span data-stu-id="5ac00-107">GDI+ can display metafiles that have been stored in the following formats:</span></span>  
  
- <span data-ttu-id="5ac00-108">Windows Metafile (WMF)</span><span class="sxs-lookup"><span data-stu-id="5ac00-108">Windows Metafile (WMF)</span></span>  
  
- <span data-ttu-id="5ac00-109">EMF (Enhanced Metafile)</span><span class="sxs-lookup"><span data-stu-id="5ac00-109">Enhanced Metafile (EMF)</span></span>  
  
- <span data-ttu-id="5ac00-110">EMF+</span><span class="sxs-lookup"><span data-stu-id="5ac00-110">EMF+</span></span>  
  
 <span data-ttu-id="5ac00-111">Rozhraní GDI + můžete zaznamenat metasoubory v EMF a EMF + formáty, ale není ve formátu WMF.</span><span class="sxs-lookup"><span data-stu-id="5ac00-111">GDI+ can record metafiles in the EMF and EMF+ formats, but not in the WMF format.</span></span>  
  
 <span data-ttu-id="5ac00-112">EMF + je rozšíření EMF, která umožňuje rozhraní GDI + záznamy mají být uloženy.</span><span class="sxs-lookup"><span data-stu-id="5ac00-112">EMF+ is an extension to EMF that allows GDI+ records to be stored.</span></span> <span data-ttu-id="5ac00-113">Existují dvě varianty EMF + formát: EMF + pouze a EMF + duální.</span><span class="sxs-lookup"><span data-stu-id="5ac00-113">There are two variations on the EMF+ format: EMF+ Only and EMF+ Dual.</span></span> <span data-ttu-id="5ac00-114">EMF + pouze metasoubory obsahuje pouze záznamy rozhraní GDI +.</span><span class="sxs-lookup"><span data-stu-id="5ac00-114">EMF+ Only metafiles contain only GDI+ records.</span></span> <span data-ttu-id="5ac00-115">Takové metasoubory lze zobrazit pomocí GDI +, ale ne GDI.</span><span class="sxs-lookup"><span data-stu-id="5ac00-115">Such metafiles can be displayed by GDI+ but not by GDI.</span></span> <span data-ttu-id="5ac00-116">Metasoubory EMF + duální obsahovat rozhraní GDI + a GDI záznamů.</span><span class="sxs-lookup"><span data-stu-id="5ac00-116">EMF+ Dual metafiles contain GDI+ and GDI records.</span></span> <span data-ttu-id="5ac00-117">Každý záznam rozhraní GDI + duální EMF + metasoubor je spárovaná s alternativní záznam GDI.</span><span class="sxs-lookup"><span data-stu-id="5ac00-117">Each GDI+ record in an EMF+ Dual metafile is paired with an alternate GDI record.</span></span> <span data-ttu-id="5ac00-118">Takové metasoubory lze zobrazit pomocí GDI + nebo GDI.</span><span class="sxs-lookup"><span data-stu-id="5ac00-118">Such metafiles can be displayed by GDI+ or by GDI.</span></span>  
  
 <span data-ttu-id="5ac00-119">Následující příklad zobrazuje metasoubor dříve uložený jako soubor.</span><span class="sxs-lookup"><span data-stu-id="5ac00-119">The following example displays a metafile that was previously saved as a file.</span></span> <span data-ttu-id="5ac00-120">Zobrazí se tento metasoubor pomocí jeho levého horního rohu na (100, 100).</span><span class="sxs-lookup"><span data-stu-id="5ac00-120">The metafile is displayed with its upper-left corner at (100, 100).</span></span>  
  
 [!code-csharp[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/CS/Class1.cs#21)]
 [!code-vb[System.Drawing.ImagesBitmapsMetafiles#21](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Drawing.ImagesBitmapsMetafiles/VB/Class1.vb#21)]  
  
## <a name="see-also"></a><span data-ttu-id="5ac00-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="5ac00-121">See also</span></span>

- [<span data-ttu-id="5ac00-122">Obrázky, rastrové obrázky a metasoubory</span><span class="sxs-lookup"><span data-stu-id="5ac00-122">Images, Bitmaps, and Metafiles</span></span>](images-bitmaps-and-metafiles.md)
