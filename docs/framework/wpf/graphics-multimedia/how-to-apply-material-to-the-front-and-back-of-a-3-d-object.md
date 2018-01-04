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
ms.workload: dotnet
ms.openlocfilehash: c5ead8805c3d16bc16e259bdf90a19f05500563c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-apply-material-to-the-front-and-back-of-a-3-d-object"></a>Postupy: Použití materiálu na přední a zadní 3D objekt
Následující příklad ukazuje, jak se má použít <xref:System.Windows.Media.Media3D.Material> přední a zadní 3D objektu a použije animaci objekt, který chcete zobrazit obou stranách objektu. <xref:System.Windows.Media.Media3D.GeometryModel3D.Material%2A> Vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> se používá k aplikování zobrazí červený <xref:System.Windows.Media.Brush> k přední strana objektu a <xref:System.Windows.Media.Media3D.GeometryModel3D.BackMaterial%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D> se používá k aplikování modrá <xref:System.Windows.Media.Brush> na zadní straně objektu. Následující kód ukazuje použití těchto materiálů k objektu:  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexampleinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celé ukázce.  
  
 [!code-xaml[Animation3DGallery_snip#BackMaterialAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/BackMaterialAnimationExample.xaml#backmaterialanimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření 3D scény](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Animace vlastností materiálu ve 3D scéně](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-material-properties-in-a-3-d-scene.md)  
 [Použití vyzařujícího materiálu na 3D objekt](../../../../docs/framework/wpf/graphics-multimedia/how-to-apply-emissive-material-to-a-3-d-object.md)
