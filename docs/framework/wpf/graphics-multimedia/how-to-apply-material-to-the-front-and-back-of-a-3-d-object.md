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
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3d-object"></a>Postup: Aplikování materiálu na přední a zadní stranu 3D objektu
Následující příklad ukazuje, jak <xref:System.Windows.Media.Media3D.Material> aplikovat a na přední a zadní stranu 3D objektu a animovat objekt tak, aby zobrazoval obě strany objektu. Vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> <xref:System.Windows.Media.Media3D.GeometryModel3D> a se používá k <xref:System.Windows.Media.Brush> použití červené na přední straně <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> objektu <xref:System.Windows.Media.Media3D.GeometryModel3D> a vlastnost objektu se používá k použití modré <xref:System.Windows.Media.Brush> na zadní straně objektu. Níže uvedený kód ukazuje použití materiálů na objekt:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorek.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
- [Animace vlastností materiálu ve 3D scéně](how-to-animate-material-properties-in-a-3-d-scene.md)
- [Aplikování emisivního materiálu na 3D objekt](how-to-apply-emissive-material-to-a-3-d-object.md)
