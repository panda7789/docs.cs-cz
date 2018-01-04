---
title: "Postupy: Vytvoření dekorace textu"
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
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0beb22ba78c6fc99951bc2d780c1c5defa32e637
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-text-decoration"></a><span data-ttu-id="7d6fd-102">Postupy: Vytvoření dekorace textu</span><span class="sxs-lookup"><span data-stu-id="7d6fd-102">How to: Create a Text Decoration</span></span>
<span data-ttu-id="7d6fd-103">A <xref:System.Windows.TextDecoration> objekt je visual dekoru můžete přidat do textu.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-103">A <xref:System.Windows.TextDecoration> object is a visual ornamentation you can add to text.</span></span> <span data-ttu-id="7d6fd-104">Existují čtyři typy textové dekorace: podtržení, standardních hodnot, přeškrtnutí a čáry nahoře.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-104">There are four types of text decorations: underline, baseline, strikethrough, and overline.</span></span> <span data-ttu-id="7d6fd-105">Následující příklad ukazuje umístění textové dekorace textu.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-105">The following example shows the locations of the text decorations relative to the text.</span></span>  
  
 <span data-ttu-id="7d6fd-106">![Diagram umístění textové dekorace](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span><span class="sxs-lookup"><span data-stu-id="7d6fd-106">![Diagram of text decoration locations](../../../../docs/framework/wpf/advanced/media/textdecoration01.gif "TextDecoration01")</span></span>  
<span data-ttu-id="7d6fd-107">Příklad textové dekorace typů</span><span class="sxs-lookup"><span data-stu-id="7d6fd-107">Example of text decoration types</span></span>  
  
 <span data-ttu-id="7d6fd-108">Chcete-li přidat textové dekorace na text, vytvořte <xref:System.Windows.TextDecoration> objektu a upravit její vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-108">To add a text decoration to text, create a <xref:System.Windows.TextDecoration> object and modify its properties.</span></span> <span data-ttu-id="7d6fd-109">Použití <xref:System.Windows.TextDecoration.Location%2A> vlastnosti k určení, kde textová dekorace se zobrazí, jako je například podtržení.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-109">Use the <xref:System.Windows.TextDecoration.Location%2A> property to specify where the text decoration appears, such as underline.</span></span> <span data-ttu-id="7d6fd-110">Použití <xref:System.Windows.TextDecoration.Pen%2A> vlastnosti a určit vzhled textová dekorace, jako je plné výplně nebo barva barevného přechodu.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-110">Use the <xref:System.Windows.TextDecoration.Pen%2A> property to specify the appearance of the text decoration, such as a solid fill or gradient color.</span></span> <span data-ttu-id="7d6fd-111">Pokud nezadáte hodnotu <xref:System.Windows.TextDecoration.Pen%2A> vlastnost dekorace výchozí hodnoty pro stejnou barvu jako text.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-111">If you do not specify a value for the <xref:System.Windows.TextDecoration.Pen%2A> property, the decorations defaults to the same color as the text.</span></span> <span data-ttu-id="7d6fd-112">Jakmile definujete <xref:System.Windows.TextDecoration> objektu, přidejte ho do <xref:System.Windows.TextDecorations> kolekce objekt požadovaná textu.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-112">Once you have defined a <xref:System.Windows.TextDecoration> object, add it to the <xref:System.Windows.TextDecorations> collection of the desired text object.</span></span>  
  
 <span data-ttu-id="7d6fd-113">Následující příklad ukazuje textové dekorace něhož má byly použity lineární štětce přechodu a pera přerušovanou.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-113">The following example shows a text decoration that has been styled with a linear gradient brush and a dashed pen.</span></span>  
  
 <span data-ttu-id="7d6fd-114">![Textové dekorace s lineárního přechodu podtržení](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span><span class="sxs-lookup"><span data-stu-id="7d6fd-114">![Text decoration with linear gradient underline](../../../../docs/framework/wpf/advanced/media/textdecoration02.png "TextDecoration02")</span></span>  
<span data-ttu-id="7d6fd-115">Příklad podtržení navržen s lineárního přechodu štětce a přerušovanou pera</span><span class="sxs-lookup"><span data-stu-id="7d6fd-115">Example of an underline styled with a linear gradient brush and dashed pen</span></span>  
  
 <span data-ttu-id="7d6fd-116"><xref:System.Windows.Documents.Hyperlink> Je objekt na úrovni toku obsahu element, který umožňuje hostitele hypertextové odkazy v rámci toku obsahu.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-116">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="7d6fd-117">Ve výchozím nastavení <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.TextDecoration> objekt, který chcete zobrazit podtržení.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-117">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="7d6fd-118"><xref:System.Windows.TextDecoration>objekty lze náročné vytvořit instanci, výkonu, zejména pokud máte mnoho <xref:System.Windows.Documents.Hyperlink> objekty.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-118"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="7d6fd-119">Pokud provedete rozsáhlé používání šířky <xref:System.Windows.Documents.Hyperlink> elementy, možná budete chtít zvážit zobrazující podtržení jenom v případě, že aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-119">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="7d6fd-120">V následujícím příkladu je, že podtržení odkazu "Moje MSN" dynamické – zobrazí se pouze když <xref:System.Windows.ContentElement.MouseEnter> je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-120">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="7d6fd-121">![Hypertextové odkazy zobrazující objekty TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="7d6fd-121">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="7d6fd-122">Hypertextové odkazy definované s objekty TextDecorations</span><span class="sxs-lookup"><span data-stu-id="7d6fd-122">Hyperlinks defined with TextDecorations</span></span>  
  
 <span data-ttu-id="7d6fd-123">Další informace najdete v tématu [určit, zda hypertextový odkaz je podtržený](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span><span class="sxs-lookup"><span data-stu-id="7d6fd-123">For more information, see [Specify Whether a Hyperlink is Underlined](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="7d6fd-124">Příklad</span><span class="sxs-lookup"><span data-stu-id="7d6fd-124">Example</span></span>  
 <span data-ttu-id="7d6fd-125">V následujícím příkladu kódu textové dekorace podtržení, které používá výchozí hodnota písma.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-125">In the following code example, an underline text decoration uses the default font value.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets1)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets1)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets1)]  
  
 <span data-ttu-id="7d6fd-126">V následujícím příkladu kódu textové dekorace podtržení, které se vytvoří s plnobarevné štětce pro pero.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-126">In the following code example, an underline text decoration is created with a solid color brush for the pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets2)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets2)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets2](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets2)]  
  
 <span data-ttu-id="7d6fd-127">V následujícím příkladu kódu textové dekorace podtržení, které se vytvoří s lineární štětce přechodu pro přerušovanou pera.</span><span class="sxs-lookup"><span data-stu-id="7d6fd-127">In the following code example, an underline text decoration is created with a linear gradient brush for the dashed pen.</span></span>  
  
 [!code-csharp[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml.cs#textdecorationsnippets3)]
 [!code-vb[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextDecorationSnippets/visualbasic/window1.xaml.vb#textdecorationsnippets3)]
 [!code-xaml[TextDecorationSnippets#TextDecorationSnippets3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextDecorationSnippets/CSharp/Window1.xaml#textdecorationsnippets3)]  
  
## <a name="see-also"></a><span data-ttu-id="7d6fd-128">Viz také</span><span class="sxs-lookup"><span data-stu-id="7d6fd-128">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="7d6fd-129">Určení podtržení hypertextového odkazu</span><span class="sxs-lookup"><span data-stu-id="7d6fd-129">Specify Whether a Hyperlink is Underlined</span></span>](../../../../docs/framework/wpf/advanced/how-to-specify-whether-a-hyperlink-is-underlined.md)
