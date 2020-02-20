---
title: 'Postupy: Vytvoření reflexe'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- creating reflections [WPF]
- brushes [WPF], creating reflections
- reflections [WPF], creating
ms.assetid: 4f017e16-ab80-43c7-98df-03b6bddbb203
ms.openlocfilehash: 8a5ed345c0aa25312bd74799264e1f66ab4554e0
ms.sourcegitcommit: 700ea803fb06c5ce98de017c7f76463ba33ff4a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/19/2020
ms.locfileid: "77452055"
---
# <a name="how-to-create-a-reflection"></a><span data-ttu-id="c9b91-102">Postupy: Vytvoření reflexe</span><span class="sxs-lookup"><span data-stu-id="c9b91-102">How to: Create a Reflection</span></span>
<span data-ttu-id="c9b91-103">Tento příklad ukazuje, jak použít <xref:System.Windows.Media.VisualBrush> k vytvoření reflexe.</span><span class="sxs-lookup"><span data-stu-id="c9b91-103">This example shows how to use a <xref:System.Windows.Media.VisualBrush> to create a reflection.</span></span> <span data-ttu-id="c9b91-104">Vzhledem k tomu, že <xref:System.Windows.Media.VisualBrush> může zobrazit existující vizuál, můžete tuto schopnost využít k tvorbě zajímavých vizuálních efektů, jako je například odrazy a zvětšení.</span><span class="sxs-lookup"><span data-stu-id="c9b91-104">Because a <xref:System.Windows.Media.VisualBrush> can display an existing visual, you can use this capability to produce interesting visual effects, such as reflections and magnification.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c9b91-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c9b91-105">Example</span></span>  
 <span data-ttu-id="c9b91-106">Následující příklad používá <xref:System.Windows.Media.VisualBrush> k vytvoření odrazu <xref:System.Windows.Controls.Border>, která obsahuje několik prvků.</span><span class="sxs-lookup"><span data-stu-id="c9b91-106">The following example uses a <xref:System.Windows.Media.VisualBrush> to create a reflection of a <xref:System.Windows.Controls.Border> that contains several elements.</span></span> <span data-ttu-id="c9b91-107">Následující obrázek ukazuje výstup, který tento příklad vytvoří.</span><span class="sxs-lookup"><span data-stu-id="c9b91-107">The following illustration shows the output that this example produces.</span></span>  
  
 <span data-ttu-id="c9b91-108">![Odrazný vizuální objekt](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span><span class="sxs-lookup"><span data-stu-id="c9b91-108">![A reflected Visual object](./media/graphicsmm-visualbrush-reflection-small.jpg "graphicsmm_visualbrush_reflection_small")</span></span>  
<span data-ttu-id="c9b91-109">Odrazný vizuální objekt</span><span class="sxs-lookup"><span data-stu-id="c9b91-109">A reflected Visual object</span></span>  
  
 [!code-csharp[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/visualbrush_markup_snip/CSharp/ReflectionExample.cs#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-vb[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/visualbrush_markup_snip/visualbasic/reflectionexample.vb#graphicsmmvisualbrushreflectionexamplewholepage)]
 [!code-xaml[visualbrush_markup_snip#GraphicsMMVisualBrushReflectionExampleWholePage](~/samples/snippets/xaml/VS_Snippets_Wpf/visualbrush_markup_snip/XAML/ReflectionExample.xaml#graphicsmmvisualbrushreflectionexamplewholepage)]  
  
 <span data-ttu-id="c9b91-110">Kompletní vzorek, který obsahuje příklady, které ukazují, jak zvětšit části obrazovky a jak vytvořit odrazy, najdete v tématu [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span><span class="sxs-lookup"><span data-stu-id="c9b91-110">For the complete sample, which includes examples that show how to magnify parts of the screen and how to create reflections, see [VisualBrush Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Graphics/VisualBrush).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c9b91-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="c9b91-111">See also</span></span>

- <xref:System.Windows.Media.VisualBrush>
- [<span data-ttu-id="c9b91-112">Malování pomocí obrázků, kreseb a vizuálních objektů</span><span class="sxs-lookup"><span data-stu-id="c9b91-112">Painting with Images, Drawings, and Visuals</span></span>](painting-with-images-drawings-and-visuals.md)
