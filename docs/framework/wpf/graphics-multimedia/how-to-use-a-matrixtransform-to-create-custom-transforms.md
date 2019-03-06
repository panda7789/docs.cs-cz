---
title: 'Postupy: Vytvoření vlastních transformací použitím MatrixTransform'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 179c7986b6a7021f4e1245aef01eb555108ebf4f
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57358857"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Postupy: Vytvoření vlastních transformací použitím MatrixTransform
Tento příklad ukazuje způsob použití <xref:System.Windows.Media.MatrixTransform> přeložit (přesunout) pozici roztáhnout a zkosení <xref:System.Windows.Controls.Button>.  
  
> [!NOTE]
>  Použití <xref:System.Windows.Media.MatrixTransform> třídy za účelem vytvoření vlastních transformací, které nejsou součástí <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, nebo <xref:System.Windows.Media.TranslateTransform> třídy.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Přehled transformace](transforms-overview.md)
- [Témata s postupy](transformations-how-to-topics.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
