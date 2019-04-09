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
ms.openlocfilehash: d586eef8d1308070da38a0a54c63c3ba64d30c8b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59133832"
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="7d965-102">Postupy: Vytvoření dekorace textu</span><span class="sxs-lookup"><span data-stu-id="7d965-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="7d965-103">A <xref:System.Windows.TextDecoration> objekt je vizuální dekoru můžete přidat do textu.</span><span class="sxs-lookup"><span data-stu-id="7d965-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="7d965-104">Existují čtyři druhy dekorace textu: podtržení, Směrný plán, přeškrtnutí a přeškrtnutí.</span><span class="sxs-lookup"><span data-stu-id="7d965-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="7d965-105">Následující příklad ukazuje umístění dekorace textu vzhledem k textu.</span><span class="sxs-lookup"><span data-stu-id="7d965-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 ![Diagram typů dekorace textu](./media/how-to-create-a-text-decoration/text-decoration-types.gif)  
  
 <span data-ttu-id="7d965-107">Pro přidání do textové dekorace textu, vytvořte <xref:System.Windows.TextDecoration> objekt a upravit její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d965-107">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="7d965-108">Použití <xref:System.Windows.TextDecoration.Location%2A> vlastnosti a určit, kde dekorace textu se zobrazí, jako je například podtržení.</span><span class="sxs-lookup"><span data-stu-id="7d965-108">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="7d965-109">Použití <xref:System.Windows.TextDecoration.Pen%2A> vlastnosti k určení vzhledu textové dekorace, jako je například plné barvy nebo barevný přechod.</span><span class="sxs-lookup"><span data-stu-id="7d965-109">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="7d965-110">Pokud nezadáte hodnotu <xref:System.Windows.TextDecoration.Pen%2A> vlastnost dekorace výchozí hodnoty na stejnou barvu jako text.</span><span class="sxs-lookup"><span data-stu-id="7d965-110">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="7d965-111">Po definování <xref:System.Windows.TextDecoration> objektu, přidejte ji tak <xref:System.Windows.TextDecorations> kolekce objektu požadovaný text.</span><span class="sxs-lookup"><span data-stu-id="7d965-111">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="7d965-112">Následující příklad ukazuje dekorace textu, který byl navržen štětec lineárního přechodu a přerušované pera.</span><span class="sxs-lookup"><span data-stu-id="7d965-112">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 ![Dekorace textu pomocí lineárního přechodu podtržení](./media/how-to-create-a-text-decoration/text-decoration-gradient.png)  
  
 <span data-ttu-id="7d965-114"><xref:System.Windows.Documents.Hyperlink> Je objekt, který vám umožní hostitele hypertextové odkazy do plovoucího obsahu toku na úrovni vložení obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="7d965-114">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="7d965-115">Ve výchozím nastavení <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.TextDecoration> zobrazíte podtržení.</span><span class="sxs-lookup"><span data-stu-id="7d965-115">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <xref:System.Windows.TextDecoration> <span data-ttu-id="7d965-116">objekty lze vytvořit instanci, náročné na výkon, zejména v případě, že budete mít mnoho <xref:System.Windows.Documents.Hyperlink> objekty.</span><span class="sxs-lookup"><span data-stu-id="7d965-116">objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="7d965-117">Pokud provedete převážně <xref:System.Windows.Documents.Hyperlink> prvky, možná budete chtít zvážit zobrazující podtržení jenom v případě, že se aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí.</span><span class="sxs-lookup"><span data-stu-id="7d965-117">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="7d965-118">V následujícím příkladu je dynamický podtržení pro odkaz "My MSN" – zobrazí se jenom v případě <xref:System.Windows.ContentElement.MouseEnter> událost se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="7d965-118">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 ![Zobrazení TextDecorations hypertextových odkazů](./media/how-to-create-a-text-decoration/text-decorations-hyperlinks.png)  
   
 <span data-ttu-id="7d965-120">Další informace najdete v tématu [podtržený zadejte hypertextového odkazu](how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="7d965-120">For more information, see [Specify Whether a Hyperlink is Underlined](how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d965-121">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d965-121">Example</span></span>  
 <span data-ttu-id="7d965-122">V následujícím příkladu kódu používá textové dekorace podtržení výchozí písmo hodnotu.</span><span class="sxs-lookup"><span data-stu-id="7d965-122">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="7d965-123">V následujícím příkladu kódu je vytvořen textové dekorace podtržení s štětec jednotné barvy pro pero.</span><span class="sxs-lookup"><span data-stu-id="7d965-123">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="7d965-124">V následujícím příkladu kódu je vytvořen textové dekorace podtržení s přerušované pera štětec lineárního přechodu.</span><span class="sxs-lookup"><span data-stu-id="7d965-124">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](~/samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="7d965-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="7d965-125">See also</span></span>

- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="7d965-126">Určení podtržení hypertextového odkazu</span><span class="sxs-lookup"><span data-stu-id="7d965-126">Specify Whether a Hyperlink is Underlined</span></span>](how-to-specify-whether-a-hyperlink-is-underlined.md)
