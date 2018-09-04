---
title: 'Postupy: Nastavení vlastností šířky elementu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- width properties [WPF]
- Panel control [WPF], width properties of elements
ms.assetid: 6ee04a9d-63f0-4f5b-a406-0a8cd4c35729
ms.openlocfilehash: 261318e3d1433a47eeec2069f484124efd14653f
ms.sourcegitcommit: 2eceb05f1a5bb261291a1f6a91c5153727ac1c19
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/04/2018
ms.locfileid: "43523808"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="2097d-102">Postupy: Nastavení vlastností šířky elementu</span><span class="sxs-lookup"><span data-stu-id="2097d-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="2097d-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="2097d-103">Example</span></span>  
 <span data-ttu-id="2097d-104">Tento příklad ukazuje vizuálně rozdíly při vykreslování chování mezi čtyři vlastnosti související s šířku v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="2097d-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="2097d-105"><xref:System.Windows.FrameworkElement> Třída zveřejňuje čtyři vlastnosti, které popisují vlastností šířky elementu.</span><span class="sxs-lookup"><span data-stu-id="2097d-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="2097d-106">Tyto čtyři vlastnosti může dojít ke konfliktu, a kdy to dělají, hodnotu, která má přednost před je stanoven následujícím způsobem: <xref:System.Windows.FrameworkElement.MinWidth%2A> přednost <xref:System.Windows.FrameworkElement.MaxWidth%2A> hodnotu, která naopak má přednost před <xref:System.Windows.FrameworkElement.Width%2A> hodnotu.</span><span class="sxs-lookup"><span data-stu-id="2097d-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="2097d-107">Čtvrtý vlastnost <xref:System.Windows.FrameworkElement.ActualWidth%2A>, je jen pro čtení a šířku skutečné určeného interakce s procesem rozložení sestavy.</span><span class="sxs-lookup"><span data-stu-id="2097d-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="2097d-108">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nakreslit příklady <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) jako podřízený objekt <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="2097d-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="2097d-109">Můžete změnit vlastnosti šířku <xref:System.Windows.Shapes.Rectangle> pomocí řady <xref:System.Windows.Controls.ListBox> prvky, které představují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, a <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="2097d-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="2097d-110">Tímto způsobem se zobrazí vizuální prioritu každé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="2097d-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="2097d-111">Následující příklady použití modelu code-behind zpracování událostí, který <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolává události.</span><span class="sxs-lookup"><span data-stu-id="2097d-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="2097d-112">Každá vlastní metoda přijímá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnoty jako <xref:System.Double>a použije hodnotu zadané vlastnosti týkající se šířky.</span><span class="sxs-lookup"><span data-stu-id="2097d-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="2097d-113">Šířka hodnoty jsou také převést na řetězec a zapsána do různých <xref:System.Windows.Controls.TextBlock> prvky (definice těchto prvků není zobrazené ve vybrané XAML).</span><span class="sxs-lookup"><span data-stu-id="2097d-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="2097d-114">Úplnou ukázku najdete v tématu [ukázkové porovnání vlastnosti Šířka](https://go.microsoft.com/fwlink/?LinkID=160050).</span><span class="sxs-lookup"><span data-stu-id="2097d-114">For the complete sample, see [Width Properties Comparison Sample](https://go.microsoft.com/fwlink/?LinkID=160050).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="2097d-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="2097d-115">See Also</span></span>  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.FrameworkElement>  
 <xref:System.Windows.FrameworkElement.ActualWidth%2A>  
 <xref:System.Windows.FrameworkElement.MaxWidth%2A>  
 <xref:System.Windows.FrameworkElement.MinWidth%2A>  
 <xref:System.Windows.FrameworkElement.Width%2A>  
 [<span data-ttu-id="2097d-116">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="2097d-116">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)  
 [<span data-ttu-id="2097d-117">Nastavení vlastností výšky elementu</span><span class="sxs-lookup"><span data-stu-id="2097d-117">Set the Height Properties of an Element</span></span>](../../../../docs/framework/wpf/controls/how-to-set-the-height-properties-of-an-element.md)  
 [<span data-ttu-id="2097d-118">Ukázkové porovnání vlastnosti šířky</span><span class="sxs-lookup"><span data-stu-id="2097d-118">Width Properties Comparison Sample</span></span>](https://go.microsoft.com/fwlink/?LinkID=160050)
