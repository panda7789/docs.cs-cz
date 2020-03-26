---
title: 'Postup: Aplikování materiálu na přední a zadní stranu 3D objektu'
ms.date: 03/30/2017
helpviewer_keywords:
- 3D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
ms.openlocfilehash: 5c24879d97e7857fb07fcef4a9ba8efa901e4a39
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112138"
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a><span data-ttu-id="8eaf8-102">Postup: Aplikování materiálu na přední a zadní stranu 3D objektu</span><span class="sxs-lookup"><span data-stu-id="8eaf8-102">How to: Apply Material to the Front and Back of a 3D Object</span></span>
<span data-ttu-id="8eaf8-103">Následující příklad ukazuje, jak <xref:System.Windows.Media.Media3D.Material> aplikovat a na přední a zadní stranu 3D objektu a animovat objekt tak, aby zobrazoval obě strany objektu.</span><span class="sxs-lookup"><span data-stu-id="8eaf8-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="8eaf8-104">Vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> <xref:System.Windows.Media.Media3D.GeometryModel3D> a se používá k <xref:System.Windows.Media.Brush> použití červené na přední straně <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> objektu <xref:System.Windows.Media.Media3D.GeometryModel3D> a vlastnost objektu se používá k použití modré <xref:System.Windows.Media.Brush> na zadní straně objektu.</span><span class="sxs-lookup"><span data-stu-id="8eaf8-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="8eaf8-105">Níže uvedený kód ukazuje použití materiálů na objekt:</span><span class="sxs-lookup"><span data-stu-id="8eaf8-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="8eaf8-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="8eaf8-106">Example</span></span>  
 <span data-ttu-id="8eaf8-107">Následující kód ukazuje celý vzorek.</span><span class="sxs-lookup"><span data-stu-id="8eaf8-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="8eaf8-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="8eaf8-108">See also</span></span>

- [<span data-ttu-id="8eaf8-109">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="8eaf8-109">Create a 3D Scene</span></span>](how-to-create-a-3-d-scene.md)
- [<span data-ttu-id="8eaf8-110">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="8eaf8-110">3D Graphics Overview</span></span>](3-d-graphics-overview.md)
- [<span data-ttu-id="8eaf8-111">Animace vlastností materiálu ve 3D scéně</span><span class="sxs-lookup"><span data-stu-id="8eaf8-111">Animate Material Properties in a 3D Scene</span></span>](how-to-animate-material-properties-in-a-3-d-scene.md)
- [<span data-ttu-id="8eaf8-112">Aplikování emisivního materiálu na 3D objekt</span><span class="sxs-lookup"><span data-stu-id="8eaf8-112">Apply Emissive Material to a 3D Object</span></span>](how-to-apply-emissive-material-to-a-3-d-object.md)
