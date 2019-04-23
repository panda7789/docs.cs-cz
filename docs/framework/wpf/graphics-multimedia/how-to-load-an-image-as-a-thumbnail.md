---
title: 'Postupy: Načtení obrázku jako miniatury'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
ms.openlocfilehash: f984293a395e925368b20cef6aa0cd902bd6fc15
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134040"
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="6ad3d-102">Postupy: Načtení obrázku jako miniatury</span><span class="sxs-lookup"><span data-stu-id="6ad3d-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="6ad3d-103">Následující příklady ukazují, jak načíst <xref:System.Windows.Controls.Image> jako miniatury pro konzervaci paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="6ad3d-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6ad3d-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ad3d-104">Example</span></span>  
 <span data-ttu-id="6ad3d-105">Následující příklad nastaví <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] snížit velikost paměti, které jsou nutné k načtení obrázku.</span><span class="sxs-lookup"><span data-stu-id="6ad3d-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="6ad3d-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6ad3d-106">Example</span></span>  
 <span data-ttu-id="6ad3d-107">Následující příklad nastaví <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage> v kód pro omezení paměti potřebných k načtení obrázku.</span><span class="sxs-lookup"><span data-stu-id="6ad3d-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="6ad3d-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="6ad3d-108">See also</span></span>

- [<span data-ttu-id="6ad3d-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="6ad3d-109">Imaging Overview</span></span>](imaging-overview.md)
