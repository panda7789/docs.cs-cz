---
title: "Postupy: Animace 3D posunutí"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d49ad52906787eed9ab115adeb763b89b2ea38e0
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-animate-3-d-translations"></a><span data-ttu-id="cd65f-102">Postupy: Animace 3D posunutí</span><span class="sxs-lookup"><span data-stu-id="cd65f-102">How to: Animate 3-D Translations</span></span>
<span data-ttu-id="cd65f-103">Toto téma ukazuje, jak animace překlad transformace nastavit na [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="cd65f-103">This topic demonstrates how to animate a translation transformation set on a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="cd65f-104">Následující kód ukazuje použití <xref:System.Windows.Media.Media3D.TranslateTransform3D> do objektu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span><span class="sxs-lookup"><span data-stu-id="cd65f-104">The code below shows the application of a <xref:System.Windows.Media.Media3D.TranslateTransform3D> object to the <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D>.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <span data-ttu-id="cd65f-105"><xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Vlastnost tohoto objektu <xref:System.Windows.Media.Media3D.TranslateTransform3D> objektu je animovaný pomocí kódu níže.</span><span class="sxs-lookup"><span data-stu-id="cd65f-105">The <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> property of this <xref:System.Windows.Media.Media3D.TranslateTransform3D> object is animated using the code below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a><span data-ttu-id="cd65f-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cd65f-106">Example</span></span>  
 <span data-ttu-id="cd65f-107">Následující kód ukazuje celé ukázce.</span><span class="sxs-lookup"><span data-stu-id="cd65f-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="cd65f-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="cd65f-108">See Also</span></span>  
 [<span data-ttu-id="cd65f-109">Přehled animace</span><span class="sxs-lookup"><span data-stu-id="cd65f-109">Animation Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [<span data-ttu-id="cd65f-110">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="cd65f-110">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="cd65f-111">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="cd65f-111">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="cd65f-112">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="cd65f-112">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
