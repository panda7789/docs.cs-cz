---
title: 'Postupy: Oříznutí obrázku'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- images [WPF], cropping
- cropping images [WPF]
ms.assetid: c6bba109-c6e7-4cf8-bfe6-9cf8d01bb4fc
ms.openlocfilehash: f4c1a735ac102b3f6d81b5253bc15a5d1893075c
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57366800"
---
# <a name="how-to-crop-an-image"></a><span data-ttu-id="abf5f-102">Postupy: Oříznutí obrázku</span><span class="sxs-lookup"><span data-stu-id="abf5f-102">How to: Crop an Image</span></span>
<span data-ttu-id="abf5f-103">Tento příklad ukazuje, jak chcete provést oříznutí image pomocí <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span><span class="sxs-lookup"><span data-stu-id="abf5f-103">This example shows how to crop an image using <xref:System.Windows.Media.Imaging.CroppedBitmap>.</span></span>  
  
 <span data-ttu-id="abf5f-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> se používá především při kódování oříznutý verzi image uložit si do souboru.</span><span class="sxs-lookup"><span data-stu-id="abf5f-104"><xref:System.Windows.Media.Imaging.CroppedBitmap> is primarily used when encoding a cropped version of an image to save out to a file.</span></span> <span data-ttu-id="abf5f-105">Pokud chcete provést oříznutí obrázku pro zobrazení účely najdete v tématu [jak: Vytvořit oblast Ústřižku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90)) tématu.</span><span class="sxs-lookup"><span data-stu-id="abf5f-105">To crop an image for display purposes see the [How to: Create a Clip Region](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90)) topic.</span></span>  
  
## <a name="example"></a><span data-ttu-id="abf5f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="abf5f-106">Example</span></span>  
 <span data-ttu-id="abf5f-107">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] definuje prostředky používané v rámci níže.</span><span class="sxs-lookup"><span data-stu-id="abf5f-107">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] defines resources used within the samples below.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml1)]  
  
 <span data-ttu-id="abf5f-108">Následující příklad vytvoří objekt pomocí bitové kopie <xref:System.Windows.Media.Imaging.CroppedBitmap> jako zdroj.</span><span class="sxs-lookup"><span data-stu-id="abf5f-108">The following example creates an image using a <xref:System.Windows.Media.Imaging.CroppedBitmap> as its source.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml2)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp1)]
 [!code-vb[imageelementexample#CroppedCSharp1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp1)]  
  
 <span data-ttu-id="abf5f-109"><xref:System.Windows.Media.Imaging.CroppedBitmap> Může také sloužit jako zdroj jiný <xref:System.Windows.Media.Imaging.CroppedBitmap>, řetězení oříznutí.</span><span class="sxs-lookup"><span data-stu-id="abf5f-109">The <xref:System.Windows.Media.Imaging.CroppedBitmap> can also be used as the source of another <xref:System.Windows.Media.Imaging.CroppedBitmap>, chaining the cropping.</span></span> <span data-ttu-id="abf5f-110">Všimněte si, že <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> používá hodnoty, které jsou relativní vzhledem k zdroji oříznuté rastrového obrázku a ne počáteční bitové kopie.</span><span class="sxs-lookup"><span data-stu-id="abf5f-110">Note that the <xref:System.Windows.Media.Imaging.CroppedBitmap.SourceRect%2A> uses values that are relative to the source cropped bitmap and not the initial image.</span></span>  
  
 [!code-xaml[imageelementexample#CroppedXAML3](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml#croppedxaml3)]  
  
 [!code-csharp[imageelementexample#CroppedCSharp2](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample/CSharp/CroppedImageExample.xaml.cs#croppedcsharp2)]
 [!code-vb[imageelementexample#CroppedCSharp2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample/VB/CroppedImageExample.xaml.vb#croppedcsharp2)]  
  
## <a name="see-also"></a><span data-ttu-id="abf5f-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="abf5f-111">See also</span></span>
- <span data-ttu-id="abf5f-112">[Postupy: Vytvořit oblast Ústřižku](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90))</span><span class="sxs-lookup"><span data-stu-id="abf5f-112">[How to: Create a Clip Region](https://docs.microsoft.com/previous-versions/dotnet/netframework-3.5/ms746710(v=vs.90))</span></span>
