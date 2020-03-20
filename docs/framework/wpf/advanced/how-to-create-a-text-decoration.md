---
title: 'Postupy: Vytvoření dekorace textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- fonts [WPF], baseline
- text [WPF], decorations
- fonts [WPF], underline
- fonts [WPF], overline
- strikethrough type [WPF]
- fonts [WPF], strikethrough
- overline type [WPF]
- underline type [WPF]
- typography [WPF], text decorations
- baseline type [WPF]
ms.assetid: cf3cb4e7-782a-4be7-b2d4-e0935e21e4e0
ms.openlocfilehash: cf3b3c3bcb75153a0be4f7ced03b38134b79a930
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/12/2020
ms.locfileid: "79185926"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="92041-102">Postupy: Vytvoření dekorace textu</span><span class="sxs-lookup"><span data-stu-id="92041-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="92041-103">Objekt <xref:System.Windows.TextDecoration> je vizuální ozdoba, kterou můžete přidat k textu.</span><span class="sxs-lookup"><span data-stu-id="92041-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="92041-104">Existují čtyři typy textových dekorací: podtržení, účaří, přeškrtávací a nadčár.</span><span class="sxs-lookup"><span data-stu-id="92041-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="92041-105">Následující příklad ukazuje umístění textových dekorací vzhledem k textu.</span><span class="sxs-lookup"><span data-stu-id="92041-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 ![Diagram typů textových dekorací](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 <span data-ttu-id="92041-107">Chcete-li k textu přidat <xref:System.Windows.TextDecoration> textovou ozdobu, vytvořte objekt a upravte jeho vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="92041-107">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="92041-108">Pomocí <xref:System.Windows.TextDecoration.Location%2A> vlastnosti určete, kde se zobrazí dekorace textu, například podtržení.</span><span class="sxs-lookup"><span data-stu-id="92041-108">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="92041-109"><xref:System.Windows.TextDecoration.Pen%2A> Vlastnost í slouží k určení vzhledu dekorace textu, například plné výplně nebo barvy přechodu.</span><span class="sxs-lookup"><span data-stu-id="92041-109">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="92041-110">Pokud nezadáte hodnotu vlastnosti, <xref:System.Windows.TextDecoration.Pen%2A> dekorace budou mít výchozí hodnotu stejné barvy jako text.</span><span class="sxs-lookup"><span data-stu-id="92041-110">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="92041-111">Po definování objektu <xref:System.Windows.TextDecoration> jej přidejte <xref:System.Windows.TextDecorations> do kolekce požadovaného textového objektu.</span><span class="sxs-lookup"><span data-stu-id="92041-111">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="92041-112">Následující příklad ukazuje textovou výzdobu, která byla stylizována s lineárním přechodem stopy a přerušované pero.</span><span class="sxs-lookup"><span data-stu-id="92041-112">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 ![Dekorace textu s lineárním přechodem podtržení](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <span data-ttu-id="92041-114">Objekt <xref:System.Windows.Documents.Hyperlink> je prvek obsahu toku na úrovni vložky, který umožňuje hostovat hypertextové odkazy v rámci obsahu toku.</span><span class="sxs-lookup"><span data-stu-id="92041-114">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="92041-115">Ve výchozím <xref:System.Windows.Documents.Hyperlink> nastavení <xref:System.Windows.TextDecoration> používá objekt k zobrazení podtržení.</span><span class="sxs-lookup"><span data-stu-id="92041-115">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="92041-116"><xref:System.Windows.TextDecoration>objekty mohou být náročné na výkon k vytvoření <xref:System.Windows.Documents.Hyperlink> instance, zejména pokud máte mnoho objektů.</span><span class="sxs-lookup"><span data-stu-id="92041-116"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="92041-117">Pokud provedete rozsáhlé <xref:System.Windows.Documents.Hyperlink> použití prvků, můžete zvážit zobrazení podtržení pouze při <xref:System.Windows.ContentElement.MouseEnter> aktivaci události, jako je například událost.</span><span class="sxs-lookup"><span data-stu-id="92041-117">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="92041-118">V následujícím příkladu je podtržení pro odkaz "Moje MSN" <xref:System.Windows.ContentElement.MouseEnter> dynamické – zobrazí se pouze při aktivaci události.</span><span class="sxs-lookup"><span data-stu-id="92041-118">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 ![Hypertextové odkazy zobrazující textdekorace](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  

 <span data-ttu-id="92041-120">Další informace naleznete [v tématu Určení, zda je hypertextový odkaz podtržený](how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="92041-120">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="92041-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="92041-121">Example</span></span>  
 <span data-ttu-id="92041-122">V následujícím příkladu kódu používá dekorace podtržení textu výchozí hodnotu písma.</span><span class="sxs-lookup"><span data-stu-id="92041-122">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="92041-123">V následujícím příkladu kódu je dekorace podtržení textu vytvořena s plnou barevnou stopou pro pero.</span><span class="sxs-lookup"><span data-stu-id="92041-123">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="92041-124">V následujícím příkladu kódu je vytvořena dekorace podtržení textu s lineárním přechodem pro přerušované pero.</span><span class="sxs-lookup"><span data-stu-id="92041-124">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="92041-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="92041-125">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="92041-126">Určení podtržení hypertextového odkazu</span><span class="sxs-lookup"><span data-stu-id="92041-126">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
