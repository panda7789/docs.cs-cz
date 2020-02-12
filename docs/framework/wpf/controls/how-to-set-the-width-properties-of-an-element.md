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
ms.openlocfilehash: 682929625612114d042e4619d8388617988b3c48
ms.sourcegitcommit: 011314e0c8eb4cf4a11d92078f58176c8c3efd2d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/11/2020
ms.locfileid: "77124270"
---
# <a name="how-to-set-the-width-properties-of-an-element"></a><span data-ttu-id="09363-102">Postupy: Nastavení vlastností šířky elementu</span><span class="sxs-lookup"><span data-stu-id="09363-102">How to: Set the Width Properties of an Element</span></span>
## <a name="example"></a><span data-ttu-id="09363-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="09363-103">Example</span></span>  
 <span data-ttu-id="09363-104">Tento příklad vizuálně znázorňuje rozdíly v chování vykreslování ze čtyř vlastností souvisejících s šířkou v [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span><span class="sxs-lookup"><span data-stu-id="09363-104">This example visually shows the differences in rendering behavior among the four width-related properties in [!INCLUDE[TLA#tla_winclient](../../../../includes/tlasharptla-winclient-md.md)].</span></span>  
  
 <span data-ttu-id="09363-105">Třída <xref:System.Windows.FrameworkElement> zpřístupňuje čtyři vlastnosti, které popisují charakteristiky šířky elementu.</span><span class="sxs-lookup"><span data-stu-id="09363-105">The <xref:System.Windows.FrameworkElement> class exposes four properties that describe the width characteristics of an element.</span></span> <span data-ttu-id="09363-106">Tyto čtyři vlastnosti mohou kolidovat a když jsou, hodnota, která má přednost, je určena následujícím způsobem: hodnota <xref:System.Windows.FrameworkElement.MinWidth%2A> má přednost před hodnotou <xref:System.Windows.FrameworkElement.MaxWidth%2A>, která zase má přednost před hodnotou <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="09363-106">These four properties can conflict, and when they do, the value that takes precedence is determined as follows: the <xref:System.Windows.FrameworkElement.MinWidth%2A> value takes precedence over the <xref:System.Windows.FrameworkElement.MaxWidth%2A> value, which in turn takes precedence over the <xref:System.Windows.FrameworkElement.Width%2A> value.</span></span> <span data-ttu-id="09363-107">Čtvrtá vlastnost, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, je jen pro čtení a oznamuje skutečnou šířku určenou v interakcích s procesem rozložení.</span><span class="sxs-lookup"><span data-stu-id="09363-107">A fourth property, <xref:System.Windows.FrameworkElement.ActualWidth%2A>, is read-only, and reports the actual width as determined by interactions with the layout process.</span></span>  
  
 <span data-ttu-id="09363-108">Následující příklady [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nakreslí <xref:System.Windows.Shapes.Rectangle> prvek (`rect1`) jako podřízenou položku <xref:System.Windows.Controls.Canvas>.</span><span class="sxs-lookup"><span data-stu-id="09363-108">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] examples draw a <xref:System.Windows.Shapes.Rectangle> element (`rect1`) as a child of <xref:System.Windows.Controls.Canvas>.</span></span> <span data-ttu-id="09363-109">Vlastnosti šířky <xref:System.Windows.Shapes.Rectangle> lze změnit pomocí řady <xref:System.Windows.Controls.ListBox> prvků, které reprezentují hodnoty vlastností <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>a <xref:System.Windows.FrameworkElement.Width%2A>.</span><span class="sxs-lookup"><span data-stu-id="09363-109">You can change the width properties of a <xref:System.Windows.Shapes.Rectangle> by using a series of <xref:System.Windows.Controls.ListBox> elements that represent the property values of <xref:System.Windows.FrameworkElement.MinWidth%2A>, <xref:System.Windows.FrameworkElement.MaxWidth%2A>, and <xref:System.Windows.FrameworkElement.Width%2A>.</span></span> <span data-ttu-id="09363-110">Tímto způsobem se vizuálně zobrazí priorita každé vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="09363-110">In this manner, the precedence of each property is visually displayed.</span></span>  
  
 [!code-xaml[WidthMinWidthMaxWidth#1](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#1)]  
[!code-xaml[WidthMinWidthMaxWidth#2](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml#2)]  
  
 <span data-ttu-id="09363-111">Následující příklady kódu zpracovávají události, které událost <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> vyvolává.</span><span class="sxs-lookup"><span data-stu-id="09363-111">The following code-behind examples handle the events that the <xref:System.Windows.Controls.Primitives.Selector.SelectionChanged> event raises.</span></span> <span data-ttu-id="09363-112">Každá vlastní metoda přebírá vstup z <xref:System.Windows.Controls.ListBox>, analyzuje hodnotu jako <xref:System.Double>a použije hodnotu na zadanou vlastnost související s šířkou.</span><span class="sxs-lookup"><span data-stu-id="09363-112">Each custom method takes the input from the <xref:System.Windows.Controls.ListBox>, parses the value as a <xref:System.Double>, and applies the value to the specified width-related property.</span></span> <span data-ttu-id="09363-113">Hodnoty šířky jsou také převedeny na řetězec a zapsány do různých <xref:System.Windows.Controls.TextBlock> prvků (definice těchto elementů se ve vybraném XAML nezobrazuje).</span><span class="sxs-lookup"><span data-stu-id="09363-113">The width values are also converted to a string and written to various <xref:System.Windows.Controls.TextBlock> elements (definition of those elements is not shown in the selected XAML).</span></span>  
  
 [!code-csharp[WidthMinWidthMaxWidth#3](~/samples/snippets/csharp/VS_Snippets_Wpf/WidthMinWidthMaxWidth/CSharp/Window1.xaml.cs#3)]
 [!code-vb[WidthMinWidthMaxWidth#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/WidthMinWidthMaxWidth/VisualBasic/Window1.xaml.vb#3)]  
  
 <span data-ttu-id="09363-114">Úplnou ukázku najdete v tématu [porovnání vlastností šířky – ukázka](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).</span><span class="sxs-lookup"><span data-stu-id="09363-114">For the complete sample, see [Width Properties Comparison Sample](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties).</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09363-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="09363-115">See also</span></span>

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.FrameworkElement>
- <xref:System.Windows.FrameworkElement.ActualWidth%2A>
- <xref:System.Windows.FrameworkElement.MaxWidth%2A>
- <xref:System.Windows.FrameworkElement.MinWidth%2A>
- <xref:System.Windows.FrameworkElement.Width%2A>
- [<span data-ttu-id="09363-116">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="09363-116">Panels Overview</span></span>](panels-overview.md)
- [<span data-ttu-id="09363-117">Nastavení vlastností výšky elementu</span><span class="sxs-lookup"><span data-stu-id="09363-117">Set the Height Properties of an Element</span></span>](how-to-set-the-height-properties-of-an-element.md)
- [<span data-ttu-id="09363-118">Ukázka porovnání vlastností šířky</span><span class="sxs-lookup"><span data-stu-id="09363-118">Width Properties Comparison Sample</span></span>](https://github.com/Microsoft/WPF-Samples/tree/master/Elements/WidthProperties)
