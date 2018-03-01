---
title: "Postupy: Vytváření vlastních transformací použitím MatrixTransform"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology:
- dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
caps.latest.revision: 
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 1414ae590be10c3adcc6857492e23bf659beec67
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="aada1-102">Postupy: Vytváření vlastních transformací použitím MatrixTransform</span><span class="sxs-lookup"><span data-stu-id="aada1-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="aada1-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.MatrixTransform> přeložit (přesunout) pozici stretch a zkosení z <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="aada1-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="aada1-104">Použití <xref:System.Windows.Media.MatrixTransform> třídy za účelem vytvoření vlastní transformace, které se neposkytují <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, nebo <xref:System.Windows.Media.TranslateTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="aada1-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="aada1-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="aada1-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="aada1-106">Viz také</span><span class="sxs-lookup"><span data-stu-id="aada1-106">See Also</span></span>  
 <xref:System.Windows.Media.MatrixTransform>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="aada1-107">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="aada1-107">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="aada1-108">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="aada1-108">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)  
 [<span data-ttu-id="aada1-109">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="aada1-109">Shapes and Basic Drawing in WPF Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/shapes-and-basic-drawing-in-wpf-overview.md)
