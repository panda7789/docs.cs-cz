---
title: 'Postupy: Nastavení vlastností výšky elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- height properties [WPF]
- Panel control [WPF], height properties of elements
ms.assetid: 5ab9e781-dbb8-469a-a3c8-cf38ce312647
ms.openlocfilehash: 467cd57c728be015fb9eb9b974ca6e81e4fd7754
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33554849"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="1328f-102">Postupy: Nastavení vlastností výšky elementu</span><span class="sxs-lookup"><span data-stu-id="1328f-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="1328f-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="1328f-103">Example</span></span>  
 <span data-ttu-id="1328f-104">Tento příklad ukazuje vizuálně rozdíly v chování mezi čtyři vlastnosti související s výška v vykreslování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="1328f-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="1328f-105"><xref:System.Windows.FrameworkElement> Třída zpřístupňuje čtyři vlastnosti, které popisují charakteristiky Výška elementu.</span><span class="sxs-lookup"><span data-stu-id="1328f-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="1328f-106">Tyto čtyři vlastnosti může dojít ke konfliktu, a pokud tomu tak je, hodnotu, která má přednost před se určuje takto: <xref:System.Windows.FrameworkElement.MinHeight%2A> hodnota má přednost před <xref:System.Windows.FrameworkElement.MaxHeight%2A> hodnotu, která naopak má přednost před <xref:System.Windows.FrameworkElement.Height%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="1328f-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="1328f-107">Čtvrtý vlastnost <xref:System.Windows.FrameworkElement.ActualHeight%2A>, je jen pro čtení a výšce skutečné určeného interakce s proces rozložení sestavy.</span><span class="sxs-lookup"><span data-stu-id="1328f-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="1328f-108">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklady kreslení <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) jako podřízený <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="1328f-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="1328f-109">Můžete změnit vlastnosti výšky <xref:System.Windows.Shapes.Rectangle> pomocí řady <xref:System.Windows.Controls.ListBox> prvky, které představují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="1328f-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="1328f-110">Tímto způsobem se zobrazí vizuálně prioritu každé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1328f-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="1328f-111">Následující příklady kódu zpracování události, <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolá událost.</span><span class="sxs-lookup"><span data-stu-id="1328f-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="1328f-112">Každou rutinu přebírá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnotu jako <xref:System.Double>a použije hodnotu na zadané vlastnosti související s výšku.</span><span class="sxs-lookup"><span data-stu-id="1328f-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="1328f-113">Výška hodnoty jsou také převedeno na řetězec a zapisovat do různých <xref:System.Windows.Controls.TextBlock> elementy (definice těchto elementů není znázorněné vybrané XAML).</span><span class="sxs-lookup"><span data-stu-id="1328f-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="1328f-114">Kompletní příklad, najdete v části [výška vlastnosti vzorku](http://go.microsoft.com/fwlink/?LinkID=159993).</span><span class="sxs-lookup"><span data-stu-id="1328f-114">For the complete sample, see [Height Properties Sample](http://go.microsoft.com/fwlink/?LinkID=159993).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1328f-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="1328f-115">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [<span data-ttu-id="1328f-116">Nastavení vlastností šířky elementu</span><span class="sxs-lookup"><span data-stu-id="1328f-116">Set the Width Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [<span data-ttu-id="1328f-117">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="1328f-117">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="1328f-118">Výška vlastnosti vzorku</span><span class="sxs-lookup"><span data-stu-id="1328f-118">Height Properties Sample</span></span>](http://go.microsoft.com/fwlink/?LinkID=159993)
