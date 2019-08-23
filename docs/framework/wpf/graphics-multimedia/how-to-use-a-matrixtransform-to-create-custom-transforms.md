---
title: 'Postupy: Vytvoření vlastních transformací pomocí MatrixTransform'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: 1971d5fe9422c5138f140517e6fd4c9f9b2cf48b
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69913921"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a>Postupy: Vytvoření vlastních transformací pomocí MatrixTransform
Tento příklad ukazuje, jak použít <xref:System.Windows.Media.MatrixTransform> k překladu (přesunutí) pozice, roztažení a zkosení <xref:System.Windows.Controls.Button>pro.  
  
> [!NOTE]
> <xref:System.Windows.Media.TranslateTransform> <xref:System.Windows.Media.ScaleTransform> <xref:System.Windows.Media.SkewTransform> <xref:System.Windows.Media.RotateTransform>Použijte třídu k vytvoření vlastních transformací, které nejsou poskytovány třídami,, nebo. <xref:System.Windows.Media.MatrixTransform>  
  
## <a name="example"></a>Příklad  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [Přehled transformace](transforms-overview.md)
- [Témata s postupy](transformations-how-to-topics.md)
- [Přehled objektů Shape a základního kreslení ve WPF](shapes-and-basic-drawing-in-wpf-overview.md)
