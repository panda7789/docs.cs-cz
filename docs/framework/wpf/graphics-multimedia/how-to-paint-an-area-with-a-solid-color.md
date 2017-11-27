---
title: "Postupy: Vykreslení oblasti plnou barvou"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: cde7f7df5089806ffb3235393eacc855d137ee51
ms.sourcegitcommit: c2e216692ef7576a213ae16af2377cd98d1a67fa
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2017
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="12488-102">Postupy: Vykreslení oblasti plnou barvou</span><span class="sxs-lookup"><span data-stu-id="12488-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="12488-103">K vyplnění oblast plnou barvou, můžete použít předdefinované systému štětce, například <xref:System.Windows.Media.Brushes.Red%2A> nebo <xref:System.Windows.Media.Brushes.Blue%2A>, nebo můžete vytvořit nový <xref:System.Windows.Media.SolidColorBrush> a popisují jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí hodnoty alfa, červené, zelené a modré.</span><span class="sxs-lookup"><span data-stu-id="12488-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="12488-104">V jazyce XAML může také pomocí zápisu hexadecimální malovat oblast plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="12488-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="12488-105">Následující příklady používá každý z těchto postupů pro malování <xref:System.Windows.Shapes.Rectangle> blue.</span><span class="sxs-lookup"><span data-stu-id="12488-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="12488-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="12488-106">Example</span></span>  
 <span data-ttu-id="12488-107">**Použití předdefinovaného štětce**</span><span class="sxs-lookup"><span data-stu-id="12488-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="12488-108">V následujícím příkladu používá předdefinovanou štětce <xref:System.Windows.Media.Brushes.Blue%2A> k vyplnění obdélníku blue.</span><span class="sxs-lookup"><span data-stu-id="12488-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="12488-109">**Hexadecimální notaci**</span><span class="sxs-lookup"><span data-stu-id="12488-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="12488-110">Další příklad používá šestnáctkové soustavě 8 číslic k vyplnění obdélníku blue.</span><span class="sxs-lookup"><span data-stu-id="12488-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="12488-111">**Pomocí ARGB hodnot**</span><span class="sxs-lookup"><span data-stu-id="12488-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="12488-112">V dalším příkladu se vytváří <xref:System.Windows.Media.SolidColorBrush> a popisuje jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí ARGB hodnoty pro modrou barvu.</span><span class="sxs-lookup"><span data-stu-id="12488-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="12488-113">Další způsoby, jak popisuje barvu, najdete v článku <xref:System.Windows.Media.Color> struktura.</span><span class="sxs-lookup"><span data-stu-id="12488-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="12488-114">**Související témata**</span><span class="sxs-lookup"><span data-stu-id="12488-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="12488-115">Další informace o <xref:System.Windows.Media.SolidColorBrush> a další příklady najdete v článku [vykreslování s plnou barvy a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) Přehled.</span><span class="sxs-lookup"><span data-stu-id="12488-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="12488-116">Tento příklad kódu je součástí většího příkladu vztahujícího se pro <xref:System.Windows.Media.SolidColorBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="12488-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="12488-117">Kompletní příklad, najdete v článku [štětce ukázka](http://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="12488-117">For the complete sample, see the [Brushes Sample](http://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="12488-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="12488-118">See Also</span></span>  
 <xref:System.Windows.Media.Brushes>
