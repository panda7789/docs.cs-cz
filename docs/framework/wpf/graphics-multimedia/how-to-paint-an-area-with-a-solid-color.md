---
title: 'Postupy: Vykreslení oblasti plnou barvou'
ms.date: 03/30/2017
helpviewer_keywords:
- solid colors [WPF], painting with
- brushes [WPF], painting with solid colors
- painting [WPF], with solid colors
ms.assetid: 5d27d8a7-4bd7-4063-bdf3-2c5c0f19f9d3
ms.openlocfilehash: 017c685139979ec3aa411be6e6b5fdf0e91657de
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44075545"
---
# <a name="how-to-paint-an-area-with-a-solid-color"></a><span data-ttu-id="5f870-102">Postupy: Vykreslení oblasti plnou barvou</span><span class="sxs-lookup"><span data-stu-id="5f870-102">How to: Paint an Area with a Solid Color</span></span>
<span data-ttu-id="5f870-103">K vykreslení oblasti plnou barvou, můžete použít předdefinovaný systémový štětce, jako například <xref:System.Windows.Media.Brushes.Red%2A> nebo <xref:System.Windows.Media.Brushes.Blue%2A>, nebo můžete vytvořit nový <xref:System.Windows.Media.SolidColorBrush> a popsat její <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí hodnoty alfa, červené, zelené a modré.</span><span class="sxs-lookup"><span data-stu-id="5f870-103">To paint an area with a solid color, you can use a predefined system brush, such as <xref:System.Windows.Media.Brushes.Red%2A> or <xref:System.Windows.Media.Brushes.Blue%2A>, or you can create a new <xref:System.Windows.Media.SolidColorBrush> and describe its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using alpha, red, green, and blue values.</span></span> <span data-ttu-id="5f870-104">V XAML může také pomocí zápisu hexadecimální vykreslení oblasti plnou barvou.</span><span class="sxs-lookup"><span data-stu-id="5f870-104">In XAML, you may also paint an area with a solid color by using hexidecimal notation.</span></span>  
  
 <span data-ttu-id="5f870-105">Každý z následujících postupů v následujících příkladech používá k vykreslení <xref:System.Windows.Shapes.Rectangle> modrá.</span><span class="sxs-lookup"><span data-stu-id="5f870-105">The following examples uses each of these techniques to paint a <xref:System.Windows.Shapes.Rectangle> blue.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f870-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f870-106">Example</span></span>  
 <span data-ttu-id="5f870-107">**Použití předdefinované štětce**</span><span class="sxs-lookup"><span data-stu-id="5f870-107">**Using a Predefined Brush**</span></span>  
  
 <span data-ttu-id="5f870-108">V následujícím příkladu používá předdefinované štětce <xref:System.Windows.Media.Brushes.Blue%2A> má Vymalovat modrý obdélník.</span><span class="sxs-lookup"><span data-stu-id="5f870-108">In the following example uses the predefined brush <xref:System.Windows.Media.Brushes.Blue%2A> to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_predefinedbrush1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_PredefinedBrush1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_predefinedbrush1)]  
  
 <span data-ttu-id="5f870-109">**Pomocí šestnáctkové soustavě**</span><span class="sxs-lookup"><span data-stu-id="5f870-109">**Using Hexadecimal Notation**</span></span>  
  
 <span data-ttu-id="5f870-110">Následující příklad používá k vykreslení obdélníku modré 8 číslici šestnáctkové soustavě.</span><span class="sxs-lookup"><span data-stu-id="5f870-110">The next example uses 8-digit hexadecimal notation to paint a rectangle blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_HexNotation8Digit1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_hexnotation8digit1)]  
  
 <span data-ttu-id="5f870-111">**Pomocí hodnoty ARGB**</span><span class="sxs-lookup"><span data-stu-id="5f870-111">**Using ARGB Values**</span></span>  
  
 <span data-ttu-id="5f870-112">Následující příklad vytvoří <xref:System.Windows.Media.SolidColorBrush> a popisuje jeho <xref:System.Windows.Media.SolidColorBrush.Color%2A> pomocí ARGB hodnoty modrou barvu.</span><span class="sxs-lookup"><span data-stu-id="5f870-112">The next example creates a <xref:System.Windows.Media.SolidColorBrush> and describes its <xref:System.Windows.Media.SolidColorBrush.Color%2A> using the ARGB values for the color blue.</span></span>  
  
 [!code-xaml[brushsamples_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_snip/CS/SolidColorBrushExample.xaml#_graphicsmm_rgbnotation1)]  
  
 [!code-csharp[brushsamples_procedural_snip#_graphicsmm_RgbNotation1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/brushsamples_procedural_snip/CSharp/SolidColorBrushExample.cs#_graphicsmm_rgbnotation1)]  
  
 <span data-ttu-id="5f870-113">Další způsoby popisu barev, najdete v článku <xref:System.Windows.Media.Color> struktury.</span><span class="sxs-lookup"><span data-stu-id="5f870-113">For other ways of describing color, see the <xref:System.Windows.Media.Color> structure.</span></span>  
  
 <span data-ttu-id="5f870-114">**Související témata**</span><span class="sxs-lookup"><span data-stu-id="5f870-114">**Related Topics**</span></span>  
  
 <span data-ttu-id="5f870-115">Další informace o <xref:System.Windows.Media.SolidColorBrush> a další příklady najdete v článku [Malování plnými barvami a přechody přehled](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) Přehled.</span><span class="sxs-lookup"><span data-stu-id="5f870-115">For more information about <xref:System.Windows.Media.SolidColorBrush> and additional examples, see the [Painting with Solid Colors and Gradients Overview](../../../../docs/framework/wpf/graphics-multimedia/painting-with-solid-colors-and-gradients-overview.md) overview.</span></span>  
  
 <span data-ttu-id="5f870-116">Tento příklad kódu je součástí většího příkladu určeného pro <xref:System.Windows.Media.SolidColorBrush> třídy.</span><span class="sxs-lookup"><span data-stu-id="5f870-116">This code example is part of a larger example provided for the <xref:System.Windows.Media.SolidColorBrush> class.</span></span> <span data-ttu-id="5f870-117">Úplnou ukázku najdete v tématu [Ukázka štětců](https://go.microsoft.com/fwlink/?LinkID=159973).</span><span class="sxs-lookup"><span data-stu-id="5f870-117">For the complete sample, see the [Brushes Sample](https://go.microsoft.com/fwlink/?LinkID=159973).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5f870-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f870-118">See Also</span></span>  
 <xref:System.Windows.Media.Brushes>
