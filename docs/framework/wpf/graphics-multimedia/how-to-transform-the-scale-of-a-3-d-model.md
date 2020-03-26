---
title: 'Postup: Transformace měřítka 3D modelu'
ms.date: 03/30/2017
helpviewer_keywords:
- scaling [WPF], 3D objects
- 3D objects [WPF], scaling
ms.assetid: f3fdfe33-f7dc-44b0-84a5-e43b89947f35
ms.openlocfilehash: be41a0e10929912c1b54bf7140d743d9453199bf
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80111982"
---
# <a name="how-to-transform-the-scale-of-a-3d-model"></a>Postup: Transformace měřítka 3D modelu
Tento příklad ukazuje, jak změnit měřítko 3D objektu. Chcete-li změnit velikost 3D objektu, <xref:System.Windows.Media.Media3D.ScaleTransform3D>použijte . <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A>Vlastnosti <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A>, <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleZ%2A> a změní velikost prvku podle zadaného faktoru. Například <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleX%2A> hodnota 1,5 roztáhne objekt na 150 procent jeho původní šířky. Hodnota <xref:System.Windows.Media.Media3D.ScaleTransform3D.ScaleY%2A> 0,5 zmenší výšku objektu o 50 procent. Níže uvedený kód <xref:System.Windows.Media.Media3D.ScaleTransform3D> ukazuje použití jako <xref:System.Windows.Media.Media3D.GeometryModel3D>transformace pro .  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleInline1](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexampleinline1)]  
  
## <a name="example"></a>Příklad  
 Následující kód ukazuje celý vzorek.  
  
 [!code-xaml[3DGallery_snip#ScaleTransform3DExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/3DGallery_snip/CS/ScaleTransform3DExample.xaml#scaletransform3dexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- [Animace 3D překladů](how-to-animate-3-d-translations.md)
- [Vytvoření 3D scény](how-to-create-a-3-d-scene.md)
- [Přehled 3D grafiky](3-d-graphics-overview.md)
