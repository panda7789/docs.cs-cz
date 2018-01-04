---
title: "Postupy: Oříznutí obrázku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 084e3dc7fad2bcb3b7ab787302f55c824ff3739d
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="d68d3-102">Postupy: Oříznutí obrázku</span><span class="sxs-lookup"><span data-stu-id="d68d3-102">How to: Crop an Image</span></span>
<span data-ttu-id="d68d3-103">Tento příklad ukazuje, jak oříznout k bitovou kopii pomocí <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span><span class="sxs-lookup"><span data-stu-id="d68d3-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="d68d3-104"><xref:System.Windows.Media.Imaging.CroppedBitmap>slouží především při kódování oříznutý verze bitové kopie na Uložit si do souboru.</span><span class="sxs-lookup"><span data-stu-id="d68d3-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="d68d3-105">Ořízne obrázek zobrazení účely najdete v tématu [vytvořit oblasti oříznutí](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376) tématu.</span><span class="sxs-lookup"><span data-stu-id="d68d3-105">To crop an image for display purposes see the [Create a Clip Region](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d68d3-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d68d3-106">Example</span></span>  
 <span data-ttu-id="d68d3-107">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definuje prostředky používané v rámci ukázky níže.</span><span class="sxs-lookup"><span data-stu-id="d68d3-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="d68d3-108">Následující příklad vytvoří k pomocí bitové kopie <xref:System.Windows.Media.Imaging.CroppedBitmap> jako svůj zdroj.</span><span class="sxs-lookup"><span data-stu-id="d68d3-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="d68d3-109"><xref:System.Windows.Media.Imaging.CroppedBitmap> Lze také použít jako zdroj jiný <xref:System.Windows.Media.Imaging.CroppedBitmap>, řetězení oříznutí.</span><span class="sxs-lookup"><span data-stu-id="d68d3-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="d68d3-110">Všimněte si, že <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> používá hodnoty, které jsou relativní vzhledem k zdroji oříznout rastrového obrázku a není počáteční bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="d68d3-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="d68d3-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="d68d3-111">See Also</span></span>  
 [<span data-ttu-id="d68d3-112">Vytvoření klip oblasti</span><span class="sxs-lookup"><span data-stu-id="d68d3-112">Create a Clip Region</span></span>](http://msdn.microsoft.com/en-us/56e4bed6-78d7-4292-b917-d72d0b3e4376)
