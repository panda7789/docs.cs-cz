---
title: "Postupy: Určení počátku transformace použitím relativních hodnot"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- origins of Transforms [WPF]
- Transforms [WPF], origins of
- graphics [WPF], origins of Transforms
ms.assetid: f4dbc29d-93c7-41cd-96d8-5cfd8624b470
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: d29a572e2989ffb800434fdaab9756cb651c0816
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-the-origin-of-a-transform-by-using-relative-values"></a><span data-ttu-id="79e72-102">Postupy: Určení počátku transformace použitím relativních hodnot</span><span class="sxs-lookup"><span data-stu-id="79e72-102">How to: Specify the Origin of a Transform by Using Relative Values</span></span>
<span data-ttu-id="79e72-103">Tento příklad ukazuje, jak použít relativní hodnoty k určení původu <xref:System.Windows.UIElement.RenderTransform%2A> který se použije pro <xref:System.Windows.FrameworkElement>.</span><span class="sxs-lookup"><span data-stu-id="79e72-103">This example shows how to use relative values to specify the origin of a <xref:System.Windows.UIElement.RenderTransform%2A> that is applied to a <xref:System.Windows.FrameworkElement>.</span></span>  
  
 <span data-ttu-id="79e72-104">Při otočení, škálovat nebo zkreslit <xref:System.Windows.FrameworkElement> pomocí <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost, výchozí nastavení pro transformaci se vztahuje na levém horním rohu elementu.</span><span class="sxs-lookup"><span data-stu-id="79e72-104">When you rotate, scale, or skew a <xref:System.Windows.FrameworkElement> by using the <xref:System.Windows.UIElement.RenderTransform%2A> property, the default setting applies the transform to the upper-left corner of the element.</span></span> <span data-ttu-id="79e72-105">Pokud chcete otočit, změnit velikost nebo zkosení z centra elementu, můžete odpovídajícím způsobem nastavením středu transformovat k centru elementu.</span><span class="sxs-lookup"><span data-stu-id="79e72-105">If you want to rotate, scale, or skew from the center of the element, you can compensate by setting the center of the transform to the center of the element.</span></span> <span data-ttu-id="79e72-106">Toto řešení však vyžaduje, že znáte velikost elementu.</span><span class="sxs-lookup"><span data-stu-id="79e72-106">However, that solution requires that you know the size of the element.</span></span> <span data-ttu-id="79e72-107">Jednodušší způsob použití transformace k centru elementu je nastavit jeho <xref:System.Windows.UIElement.RenderTransformOrigin%2A> vlastnosti (0,5, 0,5), namísto nastavování hodnotu center na transformace sám sebe.</span><span class="sxs-lookup"><span data-stu-id="79e72-107">An easier way of applying a transform to the center of an element is to set its <xref:System.Windows.UIElement.RenderTransformOrigin%2A> property to (0.5, 0.5), instead of setting a center value on the transform itself.</span></span>  
  
## <a name="example"></a><span data-ttu-id="79e72-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="79e72-108">Example</span></span>  
 <span data-ttu-id="79e72-109">Následující příklad používá <xref:System.Windows.Media.RotateTransform> otočení <xref:System.Windows.Controls.Button> 45 stupňů po směru hodinových ručiček.</span><span class="sxs-lookup"><span data-stu-id="79e72-109">The following example uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise.</span></span> <span data-ttu-id="79e72-110">Vzhledem k tomu, že v příkladu neurčuje center, tlačítko otočí o bodu (0, 0), což je jeho levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="79e72-110">Because the example does not specify a center, the button rotates about the point (0, 0), which is its upper-left corner.</span></span> <span data-ttu-id="79e72-111"><xref:System.Windows.Media.RotateTransform> Se použijí na <xref:System.Windows.UIElement.RenderTransform%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="79e72-111">The <xref:System.Windows.Media.RotateTransform> is applied to the <xref:System.Windows.UIElement.RenderTransform%2A> property.</span></span>  
  
 <span data-ttu-id="79e72-112">Následující obrázek znázorňuje výsledek transformace pro příklad, který následuje dále.</span><span class="sxs-lookup"><span data-stu-id="79e72-112">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="79e72-113">![Tlačítko transformované pomocí RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span><span class="sxs-lookup"><span data-stu-id="79e72-113">![A button transformed using RenderTransform](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformwithdefaultcenter.png "graphicsmm_RenderTransformWithDefaultCenter")</span></span>  
<span data-ttu-id="79e72-114">Po směru hodinových ručiček rotaci 45 stupňů pomocí vlastnosti RenderTransform</span><span class="sxs-lookup"><span data-stu-id="79e72-114">A 45 degree clockwise rotation by using the RenderTransform property</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample1)]  
  
 <span data-ttu-id="79e72-115">Následující příklad používá také <xref:System.Windows.Media.RotateTransform> otočení <xref:System.Windows.Controls.Button> v tomto příkladu nastaví 45 stupňů po směru hodinových ručiček; však <xref:System.Windows.UIElement.RenderTransformOrigin%2A> u tlačítka (0,5, 0,5).</span><span class="sxs-lookup"><span data-stu-id="79e72-115">The following example also uses a <xref:System.Windows.Media.RotateTransform> to rotate a <xref:System.Windows.Controls.Button> 45 degrees clockwise; however, this example sets the <xref:System.Windows.UIElement.RenderTransformOrigin%2A> of the button to (0.5, 0.5).</span></span> <span data-ttu-id="79e72-116">V důsledku toho je oběh se použije k centru tlačítka místo levého horního rohu.</span><span class="sxs-lookup"><span data-stu-id="79e72-116">As a result, the rotation is applied to the center of the button instead of to the upper-left corner.</span></span>  
  
 <span data-ttu-id="79e72-117">Následující obrázek znázorňuje výsledek transformace pro příklad, který následuje dále.</span><span class="sxs-lookup"><span data-stu-id="79e72-117">The following illustration shows the transformation result for the example that follows.</span></span>  
  
 <span data-ttu-id="79e72-118">![Tlačítko transformované o jeho center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span><span class="sxs-lookup"><span data-stu-id="79e72-118">![A button transformed about its center](../../../../docs/framework/wpf/graphics-multimedia/media/graphicsmm-rendertransformrelativecenter.png "graphicsmm_RenderTransformRelativeCenter")</span></span>  
<span data-ttu-id="79e72-119">Otočení 45 stupňů pomocí vlastnosti RenderTransform s RenderTransformOrigin z (0,5, 0,5)</span><span class="sxs-lookup"><span data-stu-id="79e72-119">A 45 degree rotation by using the RenderTransform property with a RenderTransformOrigin of (0.5, 0.5)</span></span>  
  
 [!code-xaml[Transforms_snip#GraphicsMMRotateButtonExample2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Transforms_snip/CS/ButtonRotateTransformExample.xaml#graphicsmmrotatebuttonexample2)]  
  
 <span data-ttu-id="79e72-120">Další informace o transformaci <xref:System.Windows.FrameworkElement> objekty, najdete [transformuje přehled](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span><span class="sxs-lookup"><span data-stu-id="79e72-120">For more information about transforming <xref:System.Windows.FrameworkElement> objects, see the [Transforms Overview](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="79e72-121">Viz také</span><span class="sxs-lookup"><span data-stu-id="79e72-121">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 [<span data-ttu-id="79e72-122">Přehled transformace</span><span class="sxs-lookup"><span data-stu-id="79e72-122">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="79e72-123">Témata s postupy</span><span class="sxs-lookup"><span data-stu-id="79e72-123">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
