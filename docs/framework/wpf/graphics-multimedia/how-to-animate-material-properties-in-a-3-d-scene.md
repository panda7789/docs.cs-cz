---
title: 'Postup: Animace vlastností materiálu ve 3D scéně'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3D scenes
- animation [WPF], Material properties in 3D scenes
- 3D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: db59debcd7558cde52d8604cb04c8c4e68921825
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112190"
---
# <a name="how-to-animate-material-properties-in-a-3d-scene"></a><span data-ttu-id="5c73c-102">Postup: Animace vlastností materiálu ve 3D scéně</span><span class="sxs-lookup"><span data-stu-id="5c73c-102">How to: Animate Material Properties in a 3D Scene</span></span>
<span data-ttu-id="5c73c-103">Tento příklad ukazuje, jak <xref:System.Windows.Media.Brush.Opacity%2A> animovat vlastnost aplikovaného <xref:System.Windows.Media.Media3D.Material> na 3D model.</span><span class="sxs-lookup"><span data-stu-id="5c73c-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a 3D model.</span></span>  
  
 <span data-ttu-id="5c73c-104">Následující příklad kódu definuje <xref:System.Windows.Media.LinearGradientBrush> použitý <xref:System.Windows.Media.Media3D.Material> jako aplikovaný na 3D objekt.</span><span class="sxs-lookup"><span data-stu-id="5c73c-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="5c73c-105">Vlastnost <xref:System.Windows.Media.Brush.Opacity%2A> tohoto <xref:System.Windows.Media.LinearGradientBrush> je animovaný pomocí příkladu kódu níže.</span><span class="sxs-lookup"><span data-stu-id="5c73c-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="5c73c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5c73c-106">Example</span></span>  
 <span data-ttu-id="5c73c-107">Následující kód ukazuje celý vzorek.</span><span class="sxs-lookup"><span data-stu-id="5c73c-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5c73c-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="5c73c-108">See also</span></span>

- [<span data-ttu-id="5c73c-109">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="5c73c-109">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="5c73c-110">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="5c73c-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
