---
title: 'Postupy: Určení podtržení hypertextového odkazu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Hyperlink control type [WPF]
ms.assetid: 3996cfe6-1dac-4835-aeb3-c719ce9cfee5
ms.openlocfilehash: 9e8eb54d4710095a1aba052b16e49c528bd17c0e
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57371037"
---
# <a name="how-to-specify-whether-a-hyperlink-is-underlined"></a><span data-ttu-id="2463d-102">Postupy: Určení podtržení hypertextového odkazu</span><span class="sxs-lookup"><span data-stu-id="2463d-102">How to: Specify Whether a Hyperlink is Underlined</span></span>
<span data-ttu-id="2463d-103"><xref:System.Windows.Documents.Hyperlink> Je objekt, který vám umožní hostitele hypertextové odkazy do plovoucího obsahu toku na úrovni vložení obsahu elementu.</span><span class="sxs-lookup"><span data-stu-id="2463d-103">The <xref:System.Windows.Documents.Hyperlink> object is an inline-level flow content element that allows you to host hyperlinks within the flow content.</span></span> <span data-ttu-id="2463d-104">Ve výchozím nastavení <xref:System.Windows.Documents.Hyperlink> používá <xref:System.Windows.TextDecoration> zobrazíte podtržení.</span><span class="sxs-lookup"><span data-stu-id="2463d-104">By default, <xref:System.Windows.Documents.Hyperlink> uses a <xref:System.Windows.TextDecoration> object to display an underline.</span></span> <span data-ttu-id="2463d-105"><xref:System.Windows.TextDecoration> objekty lze vytvořit instanci, náročné na výkon, zejména v případě, že budete mít mnoho <xref:System.Windows.Documents.Hyperlink> objekty.</span><span class="sxs-lookup"><span data-stu-id="2463d-105"><xref:System.Windows.TextDecoration> objects can be performance intensive to instantiate, particularly if you have many <xref:System.Windows.Documents.Hyperlink> objects.</span></span> <span data-ttu-id="2463d-106">Pokud provedete převážně <xref:System.Windows.Documents.Hyperlink> prvky, možná budete chtít zvážit zobrazující podtržení jenom v případě, že se aktivuje událost, například <xref:System.Windows.ContentElement.MouseEnter> událostí.</span><span class="sxs-lookup"><span data-stu-id="2463d-106">If you make extensive use of <xref:System.Windows.Documents.Hyperlink> elements, you may want to consider showing an underline only when triggering an event, such as the <xref:System.Windows.ContentElement.MouseEnter> event.</span></span>  
  
 <span data-ttu-id="2463d-107">V následujícím příkladu je dynamický podtržení pro odkaz "My MSN" – zobrazí se jenom v případě <xref:System.Windows.ContentElement.MouseEnter> událost se aktivuje.</span><span class="sxs-lookup"><span data-stu-id="2463d-107">In the following example, the underline for the "My MSN" link is dynamic—it only appears when the <xref:System.Windows.ContentElement.MouseEnter> event is triggered.</span></span>  
  
 <span data-ttu-id="2463d-108">![Hypertextové odkazy zobrazení TextDecorations](./media/textdecoration03.png "TextDecoration03")</span><span class="sxs-lookup"><span data-stu-id="2463d-108">![Hyperlinks displaying TextDecorations](./media/textdecoration03.png "TextDecoration03")</span></span>  
<span data-ttu-id="2463d-109">Hypertextové odkazy definované pomocí TextDecorations</span><span class="sxs-lookup"><span data-stu-id="2463d-109">Hyperlinks defined with TextDecorations</span></span>  
  
## <a name="example"></a><span data-ttu-id="2463d-110">Příklad</span><span class="sxs-lookup"><span data-stu-id="2463d-110">Example</span></span>  
 <span data-ttu-id="2463d-111">Následující ukázkový kód <xref:System.Windows.Documents.Hyperlink> definována a nemusíte podtržení:</span><span class="sxs-lookup"><span data-stu-id="2463d-111">The following markup sample shows a <xref:System.Windows.Documents.Hyperlink> defined with and without an underline:</span></span>  
  
 [!code-xaml[Performance#PerformanceSnippet11](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml#performancesnippet11)]  
  
 <span data-ttu-id="2463d-112">Následující příklad kódu ukazuje, jak vytvořit podtržení pro <xref:System.Windows.Documents.Hyperlink> na <xref:System.Windows.ContentElement.MouseEnter> události a odeberte na <xref:System.Windows.ContentElement.MouseLeave> událostí.</span><span class="sxs-lookup"><span data-stu-id="2463d-112">The following code sample shows how to create an underline for the <xref:System.Windows.Documents.Hyperlink> on the <xref:System.Windows.ContentElement.MouseEnter> event, and remove it on the <xref:System.Windows.ContentElement.MouseLeave> event.</span></span>  
  
 [!code-csharp[Performance#PerformanceSnippet15](~/samples/snippets/csharp/VS_Snippets_Wpf/Performance/CSharp/Hyperlink.xaml.cs#performancesnippet15)]
 [!code-vb[Performance#PerformanceSnippet15](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Performance/visualbasic/hyperlink.xaml.vb#performancesnippet15)]  
  
## <a name="see-also"></a><span data-ttu-id="2463d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="2463d-113">See also</span></span>
- <xref:System.Windows.TextDecoration>
- <xref:System.Windows.Documents.Hyperlink>
- [<span data-ttu-id="2463d-114">Optimalizace výkonu aplikace WPF</span><span class="sxs-lookup"><span data-stu-id="2463d-114">Optimizing WPF Application Performance</span></span>](optimizing-wpf-application-performance.md)
- [<span data-ttu-id="2463d-115">Vytvoření dekorace textu</span><span class="sxs-lookup"><span data-stu-id="2463d-115">Create a Text Decoration</span></span>](how-to-create-a-text-decoration.md)
