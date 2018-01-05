---
title: "Postupy: Načtení obrázku jako miniatury"
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
- loading images as thumbnails [WPF]
- images [WPF], loading as thumbnails
- thumbnails [WPF], loading images as
ms.assetid: 02e055a0-54df-499a-b8b6-ab6ff7535cff
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0e91e032162e6e652daf18268d05c2a7db291bfc
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-load-an-image-as-a-thumbnail"></a><span data-ttu-id="d081f-102">Postupy: Načtení obrázku jako miniatury</span><span class="sxs-lookup"><span data-stu-id="d081f-102">How to: Load an Image as a Thumbnail</span></span>
<span data-ttu-id="d081f-103">Následující příklady ukazují, jak načíst <xref:System.Windows.Controls.Image> jako miniaturu pro konzervaci paměti aplikace.</span><span class="sxs-lookup"><span data-stu-id="d081f-103">The following examples show how to load an <xref:System.Windows.Controls.Image> as a thumbnail to conserve application memory.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d081f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="d081f-104">Example</span></span>  
 <span data-ttu-id="d081f-105">Následující příklad nastavuje <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage> v [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] snížit velikost paměti vyžadované pro načtení bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="d081f-105">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] to reduce the memory required to load the image.</span></span>  
  
 [!code-xaml[ImageElementExample_snip#ImageSimpleExampleInlineMarkup](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml#imagesimpleexampleinlinemarkup)]  
  
## <a name="example"></a><span data-ttu-id="d081f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="d081f-106">Example</span></span>  
 <span data-ttu-id="d081f-107">Následující příklad nastavuje <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> vlastnost <xref:System.Windows.Media.Imaging.BitmapImage> v kódu snížit velikost paměti vyžadované pro načtení bitovou kopii.</span><span class="sxs-lookup"><span data-stu-id="d081f-107">The following example sets the <xref:System.Windows.Media.Imaging.BitmapImage.DecodePixelWidth%2A> property of a <xref:System.Windows.Media.Imaging.BitmapImage> in code to reduce the memory required to load the image.</span></span>  
  
 [!code-csharp[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ImageElementExample_snip/CSharp/ImageSimpleExample.xaml.cs#imagesimpleexampleinlinecode1)]
 [!code-vb[ImageElementExample_snip#ImageSimpleExampleInlineCode1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/ImageElementExample_snip/VB/ImageSimpleExample.xaml.vb#imagesimpleexampleinlinecode1)]  
  
## <a name="see-also"></a><span data-ttu-id="d081f-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="d081f-108">See Also</span></span>  
 [<span data-ttu-id="d081f-109">Přehled obrázků</span><span class="sxs-lookup"><span data-stu-id="d081f-109">Imaging Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/imaging-overview.md)
