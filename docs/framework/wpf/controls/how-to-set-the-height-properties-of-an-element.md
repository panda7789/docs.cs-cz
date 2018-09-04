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
ms.openlocfilehash: 4d4aade743507001f825c19994e2f5feb1726ac4
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43525471"
---
# <a name="how-to-set-the-height-properties-of-an-element"></a><span data-ttu-id="bc1c9-102">Postupy: Nastavení vlastností výšky elementu</span><span class="sxs-lookup"><span data-stu-id="bc1c9-102">How to: Set the Height Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="bc1c9-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="bc1c9-103">Example</span></span>  
 <span data-ttu-id="bc1c9-104">Tento příklad ukazuje vizuálně rozdíly v chování mezi čtyři vlastnosti související s výšku ve vykreslování [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="bc1c9-104">This example visually shows the differences in rendering behavior among the four height-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="bc1c9-105"><xref:System.Windows.FrameworkElement> Třída zveřejňuje čtyři vlastnosti, které popisují vlastností výšky elementu.</span><span class="sxs-lookup"><span data-stu-id="bc1c9-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the height characteristics of an element.</span></span> <span data-ttu-id="bc1c9-106">Tyto čtyři vlastnosti může dojít ke konfliktu, a kdy to dělají, hodnotu, která má přednost před je stanoven následujícím způsobem: <xref:System.Windows.FrameworkElement.MinHeight%2A> přednost <xref:System.Windows.FrameworkElement.MaxHeight%2A> hodnotu, která naopak má přednost před <xref:System.Windows.FrameworkElement.Height%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="bc1c9-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinHeight%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxHeight%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Height%2A> value.</span></span> <span data-ttu-id="bc1c9-107">Čtvrtý vlastnost <xref:System.Windows.FrameworkElement.ActualHeight%2A>, která je jen pro čtení a skutečné výška určeného interakce s procesem rozložení sestavy.</span><span class="sxs-lookup"><span data-stu-id="bc1c9-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualHeight%2A>, is read-only, and reports the actual height as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="bc1c9-108">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nakreslit příklady <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) jako podřízený objekt <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="bc1c9-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="bc1c9-109">Můžete změnit vlastností výšky <xref:System.Windows.Shapes.Rectangle> pomocí řady <xref:System.Windows.Controls.ListBox> prvky, které představují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, a <xref:System.Windows.FrameworkElement.Height%2A>.</span><span class="sxs-lookup"><span data-stu-id="bc1c9-109">You can change the height properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinHeight%2A>, <xref:System.Windows.FrameworkElement.MaxHeight%2A>, and <xref:System.Windows.FrameworkElement.Height%2A>.</span></span> <span data-ttu-id="bc1c9-110">Tímto způsobem se zobrazí vizuální prioritu každé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="bc1c9-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[HeightMinHeightMaxHeight#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#1)]  
[!code-xaml[HeightMinHeightMaxHeight#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="bc1c9-111">Následující příklady použití modelu code-behind zpracování událostí, který <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolává události.</span><span class="sxs-lookup"><span data-stu-id="bc1c9-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="bc1c9-112">Každý popisovač přijímá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnoty jako <xref:System.Double>a použije hodnotu zadané vlastnosti související s výšku.</span><span class="sxs-lookup"><span data-stu-id="bc1c9-112">Each handler takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified height-related property.</span></span> <span data-ttu-id="bc1c9-113">Výška hodnoty jsou také převést na řetězec a zapsána do různých <xref:System.Windows.Controls.TextBlock> prvky (definice těchto prvků není zobrazené ve vybrané XAML).</span><span class="sxs-lookup"><span data-stu-id="bc1c9-113">The height values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[HeightMinHeightMaxHeight#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/HeightMinHeightMaxHeight/CSharp/Window1.xaml.cs#3)]
 [!code-vb[HeightMinHeightMaxHeight#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/HeightMinHeightMaxHeight/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="bc1c9-114">Úplnou ukázku najdete v tématu [výška vlastnosti vzorku](https://go.microsoft.com/fwlink/?LinkID=159993).</span><span class="sxs-lookup"><span data-stu-id="bc1c9-114">For the complete sample, see [Height Properties Sample](https://go.microsoft.com/fwlink/?LinkID=159993).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="bc1c9-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="bc1c9-115">See Also</span></span>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement.ActualHeight%2A>  
 <xref:System.Windows.FrameworkElement.MaxHeight%2A>  
 <xref:System.Windows.FrameworkElement.MinHeight%2A>  
 <xref:System.Windows.FrameworkElement.Height%2A>  
 [<span data-ttu-id="bc1c9-116">Nastavení vlastností šířky elementu</span><span class="sxs-lookup"><span data-stu-id="bc1c9-116">Set the Width Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-width-properties-of-an-element.md)  
 [<span data-ttu-id="bc1c9-117">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="bc1c9-117">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="bc1c9-118">Výška vlastnosti vzorku</span><span class="sxs-lookup"><span data-stu-id="bc1c9-118">Height Properties Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=159993)
