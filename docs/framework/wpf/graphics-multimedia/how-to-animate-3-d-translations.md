---
title: 'Postupy: Animace 3D posunutí'
ms.date: 03/30/2017
helpviewer_keywords:
- animation [WPF], 3-D translations
- 3-D translations [WPF], animating
ms.assetid: d4eece1f-0cd2-4a2c-8370-293354c380e4
ms.openlocfilehash: e73035a48e32e3eec20b44c82b5b9ec6763c1e7c
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54653031"
---
# <a name="how-to-animate-3-d-translations"></a>Postupy: Animace 3D posunutí
Toto téma ukazuje, jak animovat transformace překlad nastavte na [!INCLUDE[TLA#tla_3d](../../../../includes/tlasharptla-3d-md.md)] modelu.  
  
 Následující kód ukazuje použití <xref:System.Windows.Media.Media3D.TranslateTransform3D> objektu <xref:System.Windows.Media.Media3D.Model3D.Transform%2A> vlastnost <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline1)]  
  
 <xref:System.Windows.Media.Media3D.TranslateTransform3D.OffsetX%2A> Vlastnosti tohoto <xref:System.Windows.Media.Media3D.TranslateTransform3D> objektu je animovaný pomocí níže uvedeného kódu.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationInline2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationinline2)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorku.  
  
 [!code-xaml[Animation3DGallery_snip#Translation3DAnimationExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Animation3DGallery_snip/CS/Translation3DAnimationExample.xaml#translation3danimationexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Přehled animace](../../../../docs/framework/wpf/graphics-multimedia/animation-overview.md)
- [Vytvoření 3D scény](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)
- [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
- [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)
