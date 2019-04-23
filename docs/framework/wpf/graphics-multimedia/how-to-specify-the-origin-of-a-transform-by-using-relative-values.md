---
title: 'Postupy: Určení počátku transformace použitím relativních hodnot'
ms.date: 03/30/2017
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
ms.openlocfilehash: 48b3b0df8dab8516873495a996074eae57ffe00f
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59082955"
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="062bc-102">Postupy: Určení počátku transformace použitím relativních hodnot</span><span class="sxs-lookup"><span data-stu-id="062bc-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="062bc-103">Tento příklad ukazuje, jak použít relativní hodnoty k určení počátku <xref:System.Windows.UIElement.RenderTransform%2A> , která je použita na <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="062bc-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="062bc-104">Při otočení, škálování nebo zkosení <xref:System.Windows.FrameworkElement> pomocí <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost, výchozí nastavení se týká transformací, která se levém horním rohu elementu.</span><span class="sxs-lookup"><span data-stu-id="062bc-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="062bc-105">Pokud chcete k otočení, škálování nebo zkosení v centru elementu, může kompenzovat nastavením center transformací, která se k centru elementu.</span><span class="sxs-lookup"><span data-stu-id="062bc-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="062bc-106">Toto řešení vyžaduje znát velikost prvku.</span><span class="sxs-lookup"><span data-stu-id="062bc-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="062bc-107">Snadnější použití transformace na System center elementu je nastavit jeho <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti (0,5, 0,5), namísto nastavení středovou hodnotou na samotný transformace.</span><span class="sxs-lookup"><span data-stu-id="062bc-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="062bc-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="062bc-108">Example</span></span>  
 <span data-ttu-id="062bc-109">Následující příklad používá <xref:System.Windows.Media.RotateTransform> otočíte <xref:System.Windows.Controls.Button> 45 stupňů po směru hodinových ručiček.</span><span class="sxs-lookup"><span data-stu-id="062bc-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="062bc-110">Protože příklad neurčuje System center, tlačítko otočí o bod (0, 0), který je jeho levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="062bc-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="062bc-111"><xref:System.Windows.Media.RotateTransform> Aplikován <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="062bc-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="062bc-112">Následující obrázek ukazuje výsledek transformace pro příklad, který následuje.</span><span class="sxs-lookup"><span data-stu-id="062bc-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="062bc-113">![Tlačítko transformovat pomocí RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="062bc-113">![A button transformed using RenderTransform](./media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="062bc-114">45 stupňů po směru hodinových ručiček otočení pomocí RenderTransform – vlastnost</span><span class="sxs-lookup"><span data-stu-id="062bc-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="062bc-115">V následujícím příkladu se používá také <xref:System.Windows.Media.RotateTransform> otočíte <xref:System.Windows.Controls.Button> v tomto příkladu nastaví 45 stupňů po směru hodinových ručiček, nicméně <xref:System.Windows.UIElement.RenderTransformOrigin%2A> tlačítka (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="062bc-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="062bc-116">Otočení v důsledku toho se použije pro Centrum tlačítko místo do levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="062bc-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="062bc-117">Následující obrázek ukazuje výsledek transformace pro příklad, který následuje.</span><span class="sxs-lookup"><span data-stu-id="062bc-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="062bc-118">![Tlačítko transformované o jeho střed](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="062bc-118">![A button transformed about its center](./media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="062bc-119">Otočení kolem osy 45 stupňů, pomocí RenderTransformOrigin z RenderTransform – vlastnost (0,5, 0,5)</span><span class="sxs-lookup"><span data-stu-id="062bc-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](~/samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="062bc-120">Další informace o transformaci <xref:System.Windows.FrameworkElement> objekty, najdete [transformuje přehled](transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="062bc-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="062bc-121">Viz také:</span><span class="sxs-lookup"><span data-stu-id="062bc-121">See also</span></span>

- <xref:System.Windows.Media.Transform>
- [<span data-ttu-id="062bc-122">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="062bc-122">Transforms Overview</span></span>](transforms-overview.md)
- [<span data-ttu-id="062bc-123">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="062bc-123">How-to Topics</span></span>](transformations-how-to-topics.md)
