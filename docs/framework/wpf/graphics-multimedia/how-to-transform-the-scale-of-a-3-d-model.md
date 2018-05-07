---
title: 'Postupy: Transformace měřítka 3D modelu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: 3cca1a210a7dbe410ebaacaaf89c08de8c31c40e
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>Postupy: Transformace měřítka 3D modelu
Tento příklad ukazuje postup škálování 3D objektu. Chcete-li změnit velikost 3D objekt, použijte <xref:System.Windows.Media.Media3D.ScaleTransform3D>. <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> vlastnosti změnit velikost elementu faktorem, který zadáte. Například <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> hodnotu 1.5 roztahovány objekt až 150 procent původní šířku. A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> hodnota 0,5 zmenšuje výška objektu o 50 procent. Následující kód ukazuje použití <xref:System.Windows.Media.Media3D.ScaleTransform3D> jako transformace pro <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celé ukázce.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Viz také  
 [Animace 3D posunutí](../../../../docs/framework/wpf/graphics-multimedia/how-to-animate-3-d-translations.md)  
 [Vytvoření 3D scény](../../../../docs/framework/wpf/graphics-multimedia/how-to-create-a-3-d-scene.md)  
 [Přehled 3D grafiky](../../../../docs/framework/wpf/graphics-multimedia/3-d-graphics-overview.md)
