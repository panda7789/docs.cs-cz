---
title: 'Postupy: Vytvoření vlastních transformací pomocí MatrixTransform'
ms.date: 03/30/2017
helpviewer_keywords:
- graphics [WPF], custom Transforms
ms.assetid: 919381ca-989f-47cf-86b4-1094060236e4
ms.openlocfilehash: aeccb961db539d4cc6dea75fb487fba06e59d6de
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61769256"
---
# <a name="how-to-use-a-matrixtransform-to-create-custom-transforms"></a><span data-ttu-id="4346a-102">Postupy: Vytvoření vlastních transformací pomocí MatrixTransform</span><span class="sxs-lookup"><span data-stu-id="4346a-102">How to: Use a MatrixTransform to Create Custom Transforms</span></span>
<span data-ttu-id="4346a-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.MatrixTransform> přeložit (přesunout) pozici roztáhnout a zkosení <xref:System.Windows.Controls.Button>.</span><span class="sxs-lookup"><span data-stu-id="4346a-103">This example shows how to use a <xref:System.Windows.Media.MatrixTransform> to translate (move) the position, stretch, and skew of a <xref:System.Windows.Controls.Button>.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="4346a-104">Použití <xref:System.Windows.Media.MatrixTransform> třídy za účelem vytvoření vlastních transformací, které nejsou součástí <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, nebo <xref:System.Windows.Media.TranslateTransform> třídy.</span><span class="sxs-lookup"><span data-stu-id="4346a-104">Use the <xref:System.Windows.Media.MatrixTransform> class to create custom transformations that are not provided by the <xref:System.Windows.Media.RotateTransform>, <xref:System.Windows.Media.SkewTransform>, <xref:System.Windows.Media.ScaleTransform>, or <xref:System.Windows.Media.TranslateTransform> classes.</span></span>  
  
## <a name="example"></a><span data-ttu-id="4346a-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="4346a-105">Example</span></span>  
 [!code-xaml[Transforms_snip#MatrixTransform](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/MatrixTransformExample.xaml#matrixtransform)]  
  
## <a name="see-also"></a><span data-ttu-id="4346a-106">Viz také:</span><span class="sxs-lookup"><span data-stu-id="4346a-106">See also</span></span>

- <xref:System.Windows.Media.MatrixTransform>
- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="4346a-107">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="4346a-107">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="4346a-108">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="4346a-108">How-to Topics</span></span>](transformations-how-to-topics.md)
- [<span data-ttu-id="4346a-109">Přehled objektů Shape a základního kreslení ve WPF</span><span class="sxs-lookup"><span data-stu-id="4346a-109">Shapes and Basic Drawing in WPF Overview</span></span>](shapes-and-basic-drawing-in-wpf-overview.md)
