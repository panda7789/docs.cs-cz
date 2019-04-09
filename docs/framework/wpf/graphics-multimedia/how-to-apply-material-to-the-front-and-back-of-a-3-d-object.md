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
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Postupy: Použití materiálu na přední a zadní část 3D objektu
Následující příklad ukazuje, jak použít <xref:System.Windows.Media.Media3D.Material> na přední a zadní 3D objekt a animovat objekt, který chcete zobrazit obě strany objektu. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> se používá k aplikování červený <xref:System.Windows.Media.Brush> do přední části objektu a <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> se používá k aplikování modrý <xref:System.Windows.Media.Brush> na zadní straně objektu. Následující kód ukazuje použití materiály k objektu:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorku.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Animace vlastností materiálu ve 3D scéně](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Použití vyzařujícího materiálu na 3D objekt](how-to-apply-emissive-material-to-a-3-d-object.md)
