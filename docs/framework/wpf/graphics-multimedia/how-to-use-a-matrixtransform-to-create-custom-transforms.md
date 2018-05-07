---
title: 'Postupy: Vytváření vlastních transformací použitím MatrixTransform'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 4ffbefea498e9a2bdc5546d112f6ff10e12fed67
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Postupy: Vytváření vlastních transformací použitím MatrixTransform
Tento příklad ukazuje, jak používat <xref:System.Windows.Media.MatrixTransform> přeložit (přesunout) pozici stretch a zkosení z <xref:System.Windows.Controls.Button>.  
  
> [!NOTE]
>  Použití <xref:System.Windows.Media.MatrixTransform> třídy za účelem vytvoření vlastní transformace, které se neposkytují <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, nebo <xref:System.Windows.Media.TranslateTransform> třídy.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [Přehled transformace](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [Přehled objektů Shape a základního kreslení ve WPF](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
