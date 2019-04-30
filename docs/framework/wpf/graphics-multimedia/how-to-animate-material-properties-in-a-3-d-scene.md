---
title: 'Postupy: Animace vlastností materiálu ve 3D scéně'
ms.date: 03/30/2017
helpviewer_keywords:
- Material properties [WPF], animating in 3-D scenes
- animation [WPF], Material properties in 3-D scenes
- 3-D scenes [WPF], animating Material properties
ms.assetid: 229fd6eb-7401-4992-b0c9-8b28de230c0f
ms.openlocfilehash: 58e880a2828d21ee76f7fac6bdcf313e8454e65b
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61789321"
---
# <a name="how-to-animate-material-properties-in-a-3-d-scene"></a><span data-ttu-id="99469-102">Postupy: Animace vlastností materiálu ve 3D scéně</span><span class="sxs-lookup"><span data-stu-id="99469-102">How to: Animate Material Properties in a 3-D Scene</span></span>
<span data-ttu-id="99469-103">Tento příklad ukazuje, jak animovat <xref:System.Windows.Media.Brush.Opacity%2A> vlastnost <xref:System.Windows.Media.Media3D.Material> u [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.</span><span class="sxs-lookup"><span data-stu-id="99469-103">This example shows how to animate the <xref:System.Windows.Media.Brush.Opacity%2A> property of the <xref:System.Windows.Media.Media3D.Material> applied to a [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] model.</span></span>  
  
 <span data-ttu-id="99469-104">Následující příklad kódu definuje <xref:System.Windows.Media.LinearGradientBrush> použít jako <xref:System.Windows.Media.Media3D.Material> použít na 3D objekt.</span><span class="sxs-lookup"><span data-stu-id="99469-104">The following code example defines the <xref:System.Windows.Media.LinearGradientBrush> used as the <xref:System.Windows.Media.Media3D.Material> applied to the 3D object.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline1)]  
  
 <span data-ttu-id="99469-105"><xref:System.Windows.Media.Brush.Opacity%2A> Vlastnosti tohoto <xref:System.Windows.Media.LinearGradientBrush> je animovaný pomocí následující příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="99469-105">The <xref:System.Windows.Media.Brush.Opacity%2A> property of this <xref:System.Windows.Media.LinearGradientBrush> is animated using the code example below.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleInline2](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexampleinline2)]  
  
## <a name="example"></a><span data-ttu-id="99469-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="99469-106">Example</span></span>  
 <span data-ttu-id="99469-107">Následující kód ukazuje celý vzorku.</span><span class="sxs-lookup"><span data-stu-id="99469-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#AnimateMaterialExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/AnimateMaterialExample.xaml#animatematerialexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="99469-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="99469-108">See also</span></span>

- [<span data-ttu-id="99469-109">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="99469-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="99469-110">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="99469-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
