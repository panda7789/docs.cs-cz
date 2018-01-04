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
# <a name="how-to-animate-3-d-translations"></a>Postupy: Animace 3D posunutí
Toto téma ukazuje, jak animace překlad transformace nastavit na [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.  
  
 Následující kód ukazuje použití <xref:System.Windows.Media.Media3D.TranslateTransform3D> do objektu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Vlastnost tohoto objektu <xref:System.Windows.Media.Media3D.TranslateTransform3D> objektu je animovaný pomocí kódu níže.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celé ukázce.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)  
 [Vytvoření 3D scény](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
