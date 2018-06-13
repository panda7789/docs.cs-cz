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
ms.locfileid: "33561157"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="f5d36-102">Postupy: Vytváření vlastních transformací použitím MatrixTransform</span><span class="sxs-lookup"><span data-stu-id="f5d36-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="f5d36-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.MatrixTransform> přeložit (přesunout) pozici stretch a zkosení z <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="f5d36-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="f5d36-104">Použití <xref:System.Windows.Media.MatrixTransform> třídy za účelem vytvoření vlastní transformace, které se neposkytují <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, nebo <xref:System.Windows.Media.TranslateTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="f5d36-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f5d36-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="f5d36-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="f5d36-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="f5d36-106">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="f5d36-107">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="f5d36-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="f5d36-108">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="f5d36-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="f5d36-109">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="f5d36-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
