---
title: "Postupy: Použití materiálu na přední a zadní 3D objekt"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- 3-D objects [WPF], applying Material class
- Material class [WPF], applying to both sides of 3-D object
- classes [WPF], Material
ms.assetid: d93c8ad6-4939-4d29-9544-4d16d98093c1
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ce4605208be264418088399253298798205c3f9b
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a><span data-ttu-id="99f26-102">Postupy: Použití materiálu na přední a zadní 3D objekt</span><span class="sxs-lookup"><span data-stu-id="99f26-102">How to: Apply Material to the Front and Back of a 3-D Object</span></span>
<span data-ttu-id="99f26-103">Následující příklad ukazuje, jak se má použít <xref:System.Windows.Media.Media3D.Material> přední a zadní 3D objektu a použije animaci objekt, který chcete zobrazit obou stranách objektu.</span><span class="sxs-lookup"><span data-stu-id="99f26-103">The following example shows how to apply a <xref:System.Windows.Media.Media3D.Material> to the front and back of a 3-D object and animate the object to show both sides of the object.</span></span> <span data-ttu-id="99f26-104"><xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> se používá k aplikování zobrazí červený <xref:System.Windows.Media.Brush> k přední strana objektu a <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> se používá k aplikování modrá <xref:System.Windows.Media.Brush> na zadní straně objektu.</span><span class="sxs-lookup"><span data-stu-id="99f26-104">The <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> property of a <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a red <xref:System.Windows.Media.Brush> to the front side of the object and the <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> property of the <xref:System.Windows.Media.Media3D.GeometryModel3D> is used to apply a blue <xref:System.Windows.Media.Brush> to the back side of the object.</span></span> <span data-ttu-id="99f26-105">Následující kód ukazuje použití těchto materiálů k objektu:</span><span class="sxs-lookup"><span data-stu-id="99f26-105">The code below shows the application of the materials to the object:</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a><span data-ttu-id="99f26-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="99f26-106">Example</span></span>  
 <span data-ttu-id="99f26-107">Následující kód ukazuje celé ukázce.</span><span class="sxs-lookup"><span data-stu-id="99f26-107">The following code shows the entire sample.</span></span>  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="99f26-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="99f26-108">See Also</span></span>  
 [<span data-ttu-id="99f26-109">Vytvoření 3D scény</span><span class="sxs-lookup"><span data-stu-id="99f26-109">Create a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [<span data-ttu-id="99f26-110">Přehled 3D grafiky</span><span class="sxs-lookup"><span data-stu-id="99f26-110">3-D Graphics Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [<span data-ttu-id="99f26-111">Animace podstatným vlastnosti v 3D scény</span><span class="sxs-lookup"><span data-stu-id="99f26-111">Animate Material Properties in a 3-D Scene</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [<span data-ttu-id="99f26-112">Použití Emissive materiálu na objekt 3D</span><span class="sxs-lookup"><span data-stu-id="99f26-112">Apply Emissive Material to a 3-D Object</span></span>](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
