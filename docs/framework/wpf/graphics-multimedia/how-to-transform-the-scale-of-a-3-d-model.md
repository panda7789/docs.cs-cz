---
title: 'Postupy: Transformace měřítka 3D modelu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3-D objects
- 3-D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: afe18cea95be945313ef78a690c58950a3fff9b0
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57378779"
---
# <a name="how-to-transform-the-scale-of-a-3-d-model"></a>Postupy: Transformace měřítka 3D modelu
Tento příklad ukazuje, jak škálovat 3D objekt. Ke škálování 3D objektu můžete použít <xref:System.Windows.Media.Media3D.ScaleTransform3D>. <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> vlastnosti změnit velikost elementu faktorem, který zadáte. Například <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> hodnotu 1.5 roztáhne objektu na jeho původní šířka 150 procent. A <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> hodnota 0,5 zmenšuje výšku objektu o 50 procent. Následující kód ukazuje použití <xref:System.Windows.Media.Media3D.ScaleTransform3D> jako transformace pro <xref:System.Windows.Media.Media3D.GeometryModel3D>.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorku.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:
- [Animace 3D posunutí](how-to-animate-3-d-translations.md)
- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
