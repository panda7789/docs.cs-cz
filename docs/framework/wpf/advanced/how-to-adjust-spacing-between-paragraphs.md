---
title: 'Postupy: Úprava mezer mezi odstavci'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: b232903054cf45b70ba99a9223352391498cf79b
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33542945"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="63457-102">Postupy: Úprava mezer mezi odstavci</span><span class="sxs-lookup"><span data-stu-id="63457-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="63457-103">Tento příklad ukazuje, jak upravit nebo odstranit mezery mezi odstavci v toku obsahu.</span><span class="sxs-lookup"><span data-stu-id="63457-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="63457-104">V toku obsahu místo navíc, který se zobrazí mezi odstavců je výsledkem okraje nastavit u těchto odstavců; Proto může být řízena mezery mezi odstavci nastavování okrajů na těchto odstavcích.</span><span class="sxs-lookup"><span data-stu-id="63457-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="63457-105">Zcela eliminovat mezera navíc mezi dva odstavce, nastavení okrajů pro odstavců na **0**.</span><span class="sxs-lookup"><span data-stu-id="63457-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="63457-106">K dosažení uniform mezery mezi odstavci v rámci celou <xref:System.Windows.Documents.FlowDocument>, můžete nastavit hodnotu uniform rozpětí pro všechny odstavce v pomocí stylů <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="63457-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="63457-107">Je důležité si uvědomit, že okraje pro dva odstavce přiléhající bude "sbalit" větší dva okraje, namísto prodloužily nahoru.</span><span class="sxs-lookup"><span data-stu-id="63457-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="63457-108">Ano Pokud dva odstavce přiléhající okraje 20 pixelů a 40 pixelů v uvedeném pořadí, výsledná mezery mezi odstavců je 40 pixelů, větší hodnot dva okraje.</span><span class="sxs-lookup"><span data-stu-id="63457-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="63457-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="63457-109">Example</span></span>  
 <span data-ttu-id="63457-110">Následující příklad používá stylů pro nastavení okraje pro všechny <xref:System.Windows.Documents.Paragraph> elementů v <xref:System.Windows.Documents.FlowDocument> k **0**, které efektivně eliminuje mezi odstavců v mezera navíc <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="63457-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
