---
title: 'Postupy: Použití materiálu na přední a zadní část 3D objektu'
ms.date: 03/30/2017
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 1d3f6a0622b5e0ccccf14af99782bb78dfe87ccb
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59168048"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="cdf20-102">Postupy: Použití materiálu na přední a zadní část 3D objektu</span><span class="sxs-lookup"><span data-stu-id="cdf20-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="cdf20-103">Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Media3D.Material> na přední a zadní 3D objekt a animovat objekt, který chcete zobrazit obě strany objektu.</span><span class="sxs-lookup"><span data-stu-id="cdf20-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="cdf20-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> se používá k aplikování červený <xref:System.Windows.Media.Brush> do přední části objektu a <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> se používá k aplikování modrý <xref:System.Windows.Media.Brush> na zadní straně objektu.</span><span class="sxs-lookup"><span data-stu-id="cdf20-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="cdf20-105">Následující kód ukazuje použití materiály k objektu:</span><span class="sxs-lookup"><span data-stu-id="cdf20-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="cdf20-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="cdf20-106">Example</span></span>  
 <span data-ttu-id="cdf20-107">Následující kód ukazuje celý vzorku.</span><span class="sxs-lookup"><span data-stu-id="cdf20-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="cdf20-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cdf20-108">See also</span></span>

- [<span data-ttu-id="cdf20-109">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="cdf20-109">Create a 3-D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="cdf20-110">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="cdf20-110">3-D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="cdf20-111">Animace vlastností materiálu ve 3D scéně</span><span class="sxs-lookup"><span data-stu-id="cdf20-111">Animate Material Properties in a 3-D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="cdf20-112">Použití vyzařujícího materiálu na 3D objekt</span><span class="sxs-lookup"><span data-stu-id="cdf20-112">Apply Emissive Material to a 3-D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
