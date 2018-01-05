---
title: "Postupy: Vytvoření reflexe"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
caps.latest.revision: "6"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 157bc01e23c304531f04b0a1cc7a66bad4bb3934
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="5698c-102">Postupy: Vytvoření reflexe</span><span class="sxs-lookup"><span data-stu-id="5698c-102">How to: Create a Reflection</span></span>
<span data-ttu-id="5698c-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.VisualBrush> k vytvoření reflexe.</span><span class="sxs-lookup"><span data-stu-id="5698c-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="5698c-104">Protože <xref:System.Windows.Media.VisualBrush> , můžete zobrazit stávající visual této funkci můžete použít k vytvoření zajímavé vizuální efekty, jako je například odrazů a zvětšení.</span><span class="sxs-lookup"><span data-stu-id="5698c-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5698c-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="5698c-105">Example</span></span>  
 <span data-ttu-id="5698c-106">Následující příklad používá <xref:System.Windows.Media.VisualBrush> vytvořit odraz <xref:System.Windows.Controls.Border> obsahující několik elementy.</span><span class="sxs-lookup"><span data-stu-id="5698c-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="5698c-107">Následující obrázek znázorňuje výstupu, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="5698c-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="5698c-108">![A projeví vizuální objekt](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="5698c-108">![A reflected Visual object](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="5698c-109">Zrcadlený vizuální objekt</span><span class="sxs-lookup"><span data-stu-id="5698c-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="5698c-110">Je kompletní ukázka, která obsahuje příklady, které ukazují, jak zvětšit části obrazovky a postup vytvoření odrazů, najdete v části [VisualBrush ukázka](http://go.microsoft.com/fwlink/?LinkID=160049).</span><span class="sxs-lookup"><span data-stu-id="5698c-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](http://go.microsoft.com/fwlink/?LinkID=160049).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5698c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="5698c-111">See Also</span></span>  
 <xref:System.Windows.Media.VisualBrush>  
 [<span data-ttu-id="5698c-112">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="5698c-112">Painting with Images, Drawings, and Visuals</span></span>](../../../../docs/framework/wpf/graphics-multimedia/painting-with-images-drawings-and-visuals.md)
