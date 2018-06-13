---
title: 'Postupy: Určení podtržení hypertextového odkazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 3d57039d959aa63c031ef467cd2f8398fc3ffd96
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544141"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="331f1-102">Postupy: Určení podtržení hypertextového odkazu</span><span class="sxs-lookup"><span data-stu-id="331f1-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="331f1-103"><xref:System.Windows.Documents.Hyperlink> Je objekt na úrovni toku obsahu element, který umožňuje hostitele hypertextové odkazy v rámci toku obsahu.</span><span class="sxs-lookup"><span data-stu-id="331f1-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="331f1-104">Ve výchozím nastavení <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.TextDecoration> objekt, který chcete zobrazit podtržení.</span><span class="sxs-lookup"><span data-stu-id="331f1-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="331f1-105"><xref:System.Windows.TextDecoration> objekty lze náročné vytvořit instanci, výkonu, zejména pokud máte mnoho <xref:System.Windows.Documents.Hyperlink> objekty.</span><span class="sxs-lookup"><span data-stu-id="331f1-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="331f1-106">Pokud provedete rozsáhlé používání šířky <xref:System.Windows.Documents.Hyperlink> elementy, možná budete chtít zvážit zobrazující podtržení jenom v případě, že aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí.</span><span class="sxs-lookup"><span data-stu-id="331f1-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="331f1-107">V následujícím příkladu je, že podtržení odkazu "Moje MSN" dynamické – zobrazí se pouze když <xref:System.Windows.ContentElement.MouseEnter> je aktivována událost.</span><span class="sxs-lookup"><span data-stu-id="331f1-107">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="331f1-108">![Hypertextové odkazy zobrazující objekty TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="331f1-108">![Hyperlinks displaying TextDecorations](../../../../docs/framework/wpf/advanced/media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="331f1-109">Hypertextové odkazy definované s objekty TextDecorations</span><span class="sxs-lookup"><span data-stu-id="331f1-109">Hyperlinks defined with TextDecorations</span></span>  
  
## <a name="example"></a><span data-ttu-id="331f1-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="331f1-110">Example</span></span>  
 <span data-ttu-id="331f1-111">Následující kód ukazuje ukázka <xref:System.Windows.Documents.Hyperlink> definované s i bez podtržení, které:</span><span class="sxs-lookup"><span data-stu-id="331f1-111">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="331f1-112">Následující příklad kódu ukazuje, jak vytvořit podtržení pro <xref:System.Windows.Documents.Hyperlink> na <xref:System.Windows.ContentElement.MouseEnter> události a odeberte na <xref:System.Windows.ContentElement.MouseLeave> událostí.</span><span class="sxs-lookup"><span data-stu-id="331f1-112">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="331f1-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="331f1-113">See Also</span></span>  
 <xref:System.Windows.TextDecoration>  
 <xref:System.Windows.Documents.Hyperlink>  
 [<span data-ttu-id="331f1-114">Optimalizace výkonu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="331f1-114">Optimizing WPF Application Performance</span></span>](../../../../docs/framework/wpf/advanced/optimizing-wpf-application-performance.md)  
 [<span data-ttu-id="331f1-115">Vytvoření dekorace textu</span><span class="sxs-lookup"><span data-stu-id="331f1-115">Create a Text Decoration</span></span>](../../../../docs/framework/wpf/advanced/how-to-create-a-text-decoration.md)
