---
title: "Postupy: Vykreslení oblasti radiálním přechodem"
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
- brushes [WPF], painting with radial gradients
- radial gradients [WPF], painting with
- painting [WPF], with radial gradients
ms.assetid: b5d0fc8a-8986-4796-b003-a75b41a48928
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: f1da933a2ee7c179a55da7d33c61539d440eabc3
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-paint-an-area-with-a-radial-gradient"></a><span data-ttu-id="733ba-102">Postupy: Vykreslení oblasti radiálním přechodem</span><span class="sxs-lookup"><span data-stu-id="733ba-102">How to: Paint an Area with a Radial Gradient</span></span>
<span data-ttu-id="733ba-103">Tento příklad ukazuje způsob použití <xref:System.Windows.Media.RadialGradientBrush> třídy Malování oblast s kruhového přechodu.</span><span class="sxs-lookup"><span data-stu-id="733ba-103">This example shows how to use the <xref:System.Windows.Media.RadialGradientBrush> class to paint an area with a radial gradient.</span></span>  
  
## <a name="example"></a><span data-ttu-id="733ba-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="733ba-104">Example</span></span>  
 <span data-ttu-id="733ba-105">Následující příklad používá <xref:System.Windows.Media.RadialGradientBrush> k vyplnění obdélníku s kruhového přechodu, která přejde z žlutý do červené na modrou k vápna zelená.</span><span class="sxs-lookup"><span data-stu-id="733ba-105">The following example uses a <xref:System.Windows.Media.RadialGradientBrush> to paint a rectangle with a radial gradient that transitions from yellow to red to blue to lime green.</span></span>  
  
 [!code-csharp[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BrushesIntroduction_snip/CSharp/RadialGradientBrushSnippet.cs#simpleradialgradientexamplewholepage)]
 [!code-vb[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/BrushesIntroduction_snip/visualbasic/radialgradientbrushsnippet.vb#simpleradialgradientexamplewholepage)]
 [!code-xaml[BrushesIntroduction_snip#SimpleRadialGradientExampleWholePage](../../../../samples/snippets/xaml/VS_Snippets_Wpf/BrushesIntroduction_snip/XAML/RadialGradientBrushSnippet.xaml#simpleradialgradientexamplewholepage)]  
  
 <span data-ttu-id="733ba-106">Následující obrázek znázorňuje přechodu z předchozího příkladu.</span><span class="sxs-lookup"><span data-stu-id="733ba-106">The following illustration shows the gradient from the preceding example.</span></span> <span data-ttu-id="733ba-107">Zdůraznily má barevný přechod zastaví.</span><span class="sxs-lookup"><span data-stu-id="733ba-107">The gradient's stops have been highlighted.</span></span>  
  
 <span data-ttu-id="733ba-108">![Přechodové zarážky v kruhového přechodu](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span><span class="sxs-lookup"><span data-stu-id="733ba-108">![Gradient stops in a radial gradient](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-4gradientstops-rg.png "wcpsdk_graphicsmm_4gradientstops_rg")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="733ba-109">V příkladech v tomto tématu pomocí souřadnicový systém výchozí kontrolní body.</span><span class="sxs-lookup"><span data-stu-id="733ba-109">The examples in this topic use the default coordinate system for setting control points.</span></span> <span data-ttu-id="733ba-110">Systém souřadnic výchozí je relativní vzhledem ke ohraničující pole: 0 znamená 0 procent ohraničujícího rámečku a 1 znamená 100 procent ohraničujícího rámečku.</span><span class="sxs-lookup"><span data-stu-id="733ba-110">The default coordinate system is relative to a bounding box: 0 indicates 0 percent of the bounding box, and 1 indicates 100 percent of the bounding box.</span></span> <span data-ttu-id="733ba-111">Tento systém souřadnic můžete změnit nastavením <xref:System.Windows.Media.GradientBrush.MappingMode%2A> vlastnost na hodnotu <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span><span class="sxs-lookup"><span data-stu-id="733ba-111">You can change this coordinate system by setting the <xref:System.Windows.Media.GradientBrush.MappingMode%2A> property to the value <xref:System.Windows.Media.BrushMappingMode.Absolute>.</span></span> <span data-ttu-id="733ba-112">Absolutní souřadnicový systém není relativně k ohraničující pole.</span><span class="sxs-lookup"><span data-stu-id="733ba-112">An absolute coordinate system is not relative to a bounding box.</span></span> <span data-ttu-id="733ba-113">Hodnoty se interpretují přímo v místním prostoru.</span><span class="sxs-lookup"><span data-stu-id="733ba-113">Values are interpreted directly in local space.</span></span>  
  
 <span data-ttu-id="733ba-114">Pro další <xref:System.Windows.Media.RadialGradientBrush> příklady najdete v tématu [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="733ba-114">For additional <xref:System.Windows.Media.RadialGradientBrush> examples, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span> <span data-ttu-id="733ba-115">Další informace o přechody a dalších typů štětce najdete v tématu [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span><span class="sxs-lookup"><span data-stu-id="733ba-115">For more information about gradients and other types of brushes, see [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md).</span></span>
