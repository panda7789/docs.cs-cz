---
title: 'Postupy: Použití několika transformací na objekt'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- grouping Transform objects [WPF]
- Transform objects [WPF], grouping
- graphics [WPF], grouping Transform objects
- TransformGroup [WPF]
ms.assetid: 98cd1921-12bc-4bf5-8193-529228fb7402
ms.openlocfilehash: 3ef11104b2a4fc775d29d2a388c9a70a69a3f10f
ms.sourcegitcommit: 267d092663aba36b6b2ea853034470aea493bfae
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/21/2020
ms.locfileid: "80112112"
---
# <a name="how-to-apply-multiple-transforms-to-an-object"></a>Postupy: Použití několika transformací na objekt
Tento příklad ukazuje, <xref:System.Windows.Media.TransformGroup> jak použít a <xref:System.Windows.Media.Transform> seskupit dva nebo více objektů do jednoho složeného <xref:System.Windows.Media.Transform>.  
  
## <a name="example"></a>Příklad  
 Následující příklad používá <xref:System.Windows.Media.TransformGroup> a <xref:System.Windows.Media.ScaleTransform> použít <xref:System.Windows.Media.RotateTransform> a <xref:System.Windows.Controls.Button>a a na .  
  
 [!code-xaml[Transforms_snip#MultipleTransformExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MultipleTransformExample.xaml#multipletransformexamplewholepage)]  
  
 [!code-csharp[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_Procedural_snip/CSharp/MultipleTransformsExample.cs#multipletransformscodeexamplewholepage)]
 [!code-vb[Transforms_Procedural_snip#MultipleTransformsCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Transforms_Procedural_snip/VisualBasic/MultipleTransformsExample.vb#multipletransformscodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.UIElement.RenderTransform%2A>
- <xref:System.Windows.Media.TransformGroup>
- [Přehled transformace](transforms-overview.md)
- [Ukázka 2D transformací](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/2DTransforms)
