---
title: "Postupy: Změna velikosti elementu"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- scaling [WPF], elements
- graphics [WPF], scaling elements
ms.assetid: 18158d94-bbe7-4f6a-814e-84d27fa748bf
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 23b3086452526e804bfdbe50bb0c134f33158f5d
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-scale-an-element"></a><span data-ttu-id="7bf81-102">Postupy: Změna velikosti elementu</span><span class="sxs-lookup"><span data-stu-id="7bf81-102">How to: Scale an Element</span></span>
<span data-ttu-id="7bf81-103">Tento příklad ukazuje, jak používat <xref:System.Windows.Media.ScaleTransform> škálování elementu.</span><span class="sxs-lookup"><span data-stu-id="7bf81-103">This example shows how to use a <xref:System.Windows.Media.ScaleTransform> to scale an element.</span></span>  
  
 <span data-ttu-id="7bf81-104">Použití <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> a <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> vlastnosti, které chcete změnit velikost elementu faktorem, který zadáte.</span><span class="sxs-lookup"><span data-stu-id="7bf81-104">Use the <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> and <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> properties to resize the element by the factor you specify.</span></span> <span data-ttu-id="7bf81-105">Například <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> hodnotu 1.5 roztahovány až 150 procent původní šířku elementu.</span><span class="sxs-lookup"><span data-stu-id="7bf81-105">For example, a <xref:System.Windows.Media.ScaleTransform.ScaleX%2A> value of 1.5 stretches the element to 150 percent of its original width.</span></span> <span data-ttu-id="7bf81-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> hodnota 0,5 zmenšuje Výška elementu o 50 procent.</span><span class="sxs-lookup"><span data-stu-id="7bf81-106">A <xref:System.Windows.Media.ScaleTransform.ScaleY%2A> value of 0.5 shrinks the height of an element by 50 percent.</span></span>  
  
 <span data-ttu-id="7bf81-107">Použití <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> vlastnosti k určení bodu, který je na střed operace škálování.</span><span class="sxs-lookup"><span data-stu-id="7bf81-107">Use the <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> properties to specify the point that is the center of the scale operation.</span></span> <span data-ttu-id="7bf81-108">Ve výchozím nastavení <xref:System.Windows.Media.ScaleTransform> je umístěn na střed v bodě (0,0), který odpovídá levého horního rohu obdélníku.</span><span class="sxs-lookup"><span data-stu-id="7bf81-108">By default, a <xref:System.Windows.Media.ScaleTransform> is centered at the point (0,0), which corresponds to the upper-left corner of the rectangle.</span></span> <span data-ttu-id="7bf81-109">To má za následek přesunutí elementu a také proto to vypadá větší, protože když použijete <xref:System.Windows.Media.Transform>, změníte souřadnicového prostoru, ve kterém se objekt nachází.</span><span class="sxs-lookup"><span data-stu-id="7bf81-109">This has the effect of moving the element and also of making it appear larger, because when you apply a <xref:System.Windows.Media.Transform>, you change the coordinate space in which the object resides.</span></span>  
  
 <span data-ttu-id="7bf81-110">Následující příklad používá <xref:System.Windows.Media.ScaleTransform> dvojnásobku velikosti 50 – podle-50 <xref:System.Windows.Shapes.Rectangle>.</span><span class="sxs-lookup"><span data-stu-id="7bf81-110">The following example uses a <xref:System.Windows.Media.ScaleTransform> to double the size of a 50-by-50 <xref:System.Windows.Shapes.Rectangle>.</span></span> <span data-ttu-id="7bf81-111"><xref:System.Windows.Media.ScaleTransform> Má hodnotu 0 (výchozí) pro obě <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span><span class="sxs-lookup"><span data-stu-id="7bf81-111">The <xref:System.Windows.Media.ScaleTransform> has a value of 0 (the default) for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="7bf81-112">Příklad</span><span class="sxs-lookup"><span data-stu-id="7bf81-112">Example</span></span>  
 [!code-xaml[transformsSample#21](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#21)]  
  
 <span data-ttu-id="7bf81-113">Obvykle nastavíte <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A> k centru objektu, který bude změněno měřítko: (<xref:System.Windows.FrameworkElement.Width%2A>/2,  <xref:System.Windows.FrameworkElement.Height%2A> /2).</span><span class="sxs-lookup"><span data-stu-id="7bf81-113">Typically, you set <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A> to the center of the object that is scaled: (<xref:System.Windows.FrameworkElement.Width%2A>/2, <xref:System.Windows.FrameworkElement.Height%2A>/2).</span></span>  
  
 <span data-ttu-id="7bf81-114">Následující příklad ukazuje další <xref:System.Windows.Shapes.Rectangle> , se používají v velikost; však to <xref:System.Windows.Media.ScaleTransform> má hodnotu 25 pro obě <xref:System.Windows.Media.ScaleTransform.CenterX%2A> a <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, která odpovídá středu rámeček.</span><span class="sxs-lookup"><span data-stu-id="7bf81-114">The following example shows another <xref:System.Windows.Shapes.Rectangle> that is doubled in size; however, this <xref:System.Windows.Media.ScaleTransform> has a value of 25 for both <xref:System.Windows.Media.ScaleTransform.CenterX%2A> and <xref:System.Windows.Media.ScaleTransform.CenterY%2A>, which corresponds to the center of the rectangle.</span></span>  
  
 [!code-xaml[transformsSample#22](../../../../samples/snippets/csharp/VS_Snippets_Wpf/transformsSample/CS/ScaleTransformExample.xaml#22)]  
  
 <span data-ttu-id="7bf81-115">Následující obrázek ukazuje rozdíl mezi nimi <xref:System.Windows.Media.ScaleTransform> operace.</span><span class="sxs-lookup"><span data-stu-id="7bf81-115">The following illustration shows the difference between the two <xref:System.Windows.Media.ScaleTransform> operations.</span></span> <span data-ttu-id="7bf81-116">Tečkovaná čára zobrazuje velikost a umístění obdélníku před škálování.</span><span class="sxs-lookup"><span data-stu-id="7bf81-116">The dotted line shows the size and position of the rectangle before scaling.</span></span>  
  
 <span data-ttu-id="7bf81-117">![2 x dál škáluje s různými středy](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span><span class="sxs-lookup"><span data-stu-id="7bf81-117">![2x scales with different center points](../../../../docs/framework/wpf/graphics-multimedia/media/wcpsdk-graphicsmm-scalecenter.gif "wcpsdk_graphicsmm_scalecenter")</span></span>  
<span data-ttu-id="7bf81-118">Dvě metody ScaleTransform operace s identické hodnoty ScaleX a ScaleY ale jiné Center</span><span class="sxs-lookup"><span data-stu-id="7bf81-118">Two ScaleTransform operations with identical ScaleX and ScaleY values but different centers</span></span>  
  
 <span data-ttu-id="7bf81-119">Kompletní příklad, najdete v části [2-D transformací ukázka](http://go.microsoft.com/fwlink/?LinkID=158252).</span><span class="sxs-lookup"><span data-stu-id="7bf81-119">For the complete sample, see [2-D Transforms Sample](http://go.microsoft.com/fwlink/?LinkID=158252).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="7bf81-120">Viz také</span><span class="sxs-lookup"><span data-stu-id="7bf81-120">See Also</span></span>  
 <xref:System.Windows.Media.Transform>  
 <xref:System.Windows.Media.ScaleTransform>  
 [<span data-ttu-id="7bf81-121">Transformuje – přehled</span><span class="sxs-lookup"><span data-stu-id="7bf81-121">Transforms Overview</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transforms-overview.md)  
 [<span data-ttu-id="7bf81-122">Postupy: témata</span><span class="sxs-lookup"><span data-stu-id="7bf81-122">How-to Topics</span></span>](../../../../docs/framework/wpf/graphics-multimedia/transformations-how-to-topics.md)
