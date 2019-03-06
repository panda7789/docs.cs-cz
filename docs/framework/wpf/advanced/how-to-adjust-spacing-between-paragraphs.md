---
title: 'Postupy: Úprava mezer mezi odstavci'
ms.date: 03/30/2017
helpviewer_keywords:
- spacing between paragraphs [WPF]
- paragraphs [WPF], spacing between
- documents [WPF], adjusting spacing between paragraphs
ms.assetid: 7cd2f2ac-0e19-4587-bfb6-7f5b18c9536e
ms.openlocfilehash: e2a6ba34e3ab15eb316671fef7c11bea03d53c73
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57367476"
---
# <a name="how-to-adjust-spacing-between-paragraphs"></a><span data-ttu-id="d8a9a-102">Postupy: Úprava mezer mezi odstavci</span><span class="sxs-lookup"><span data-stu-id="d8a9a-102">How to: Adjust Spacing Between Paragraphs</span></span>
<span data-ttu-id="d8a9a-103">Tento příklad ukazuje, jak upravit nebo odstranit mezer mezi odstavci v plovoucího obsahu.</span><span class="sxs-lookup"><span data-stu-id="d8a9a-103">This example shows how to adjust or eliminate spacing between paragraphs in flow content.</span></span>  
  
 <span data-ttu-id="d8a9a-104">V toku obsahu místo navíc, který se zobrazí mezi odstavci je výsledkem okraje nastavit na těchto odstavcích; Proto mohou být řízena mezer mezi odstavci nastavování okrajů v těchto odstavcích.</span><span class="sxs-lookup"><span data-stu-id="d8a9a-104">In flow content, extra space that appears between paragraphs is the result of margins set on these paragraphs; thus, the spacing between paragraphs can be controlled by adjusting the margins on those paragraphs.</span></span>  <span data-ttu-id="d8a9a-105">Úplně eliminovat nadbytečné mezery mezi dva odstavce, nastavit okraje pro odstavce na **0**.</span><span class="sxs-lookup"><span data-stu-id="d8a9a-105">To eliminate extra spacing between two paragraphs altogether, set the margins for the paragraphs to **0**.</span></span>  <span data-ttu-id="d8a9a-106">K dosažení jednotné mezer mezi odstavci v celém celý <xref:System.Windows.Documents.FlowDocument>, použití stylu pro nastavení jednotné okraj hodnoty pro všechny odstavce v <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="d8a9a-106">To achieve uniform spacing between paragraphs throughout an entire <xref:System.Windows.Documents.FlowDocument>, use styling to set a uniform margin value for all paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="d8a9a-107">Je důležité si uvědomit, že okraje pro dva odstavce sousedící bude "sbalit" větší z dva okraje, a nemuseli zdvojovací nahoru.</span><span class="sxs-lookup"><span data-stu-id="d8a9a-107">It is important to note that the margins for two adjacent paragraphs will "collapse" to the larger of the two margins, rather than doubling up.</span></span> <span data-ttu-id="d8a9a-108">Takže pokud dva odstavce sousedící okrajů 20 pixelů a 40 pixelů v uvedeném pořadí, je výsledný mezeru mezi odstavců 40 pixelů, větší z hodnoty dvě vlastnosti okraj.</span><span class="sxs-lookup"><span data-stu-id="d8a9a-108">So, if two adjacent paragraphs have margins of 20 pixels and 40 pixels respectively, the resulting space between the paragraphs is 40 pixels, the larger of the two margin values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="d8a9a-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="d8a9a-109">Example</span></span>  
 <span data-ttu-id="d8a9a-110">Následující příklad používá používání stylů pro nastavení okraje pro všechny <xref:System.Windows.Documents.Paragraph> prvků v <xref:System.Windows.Documents.FlowDocument> k **0**, což účinně eliminuje nadbytečné mezery mezi odstavci v <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="d8a9a-110">The following example uses styling to set the margin for all <xref:System.Windows.Documents.Paragraph> elements in a <xref:System.Windows.Documents.FlowDocument> to **0**, which effectively eliminates extra spacing between paragraphs in the <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 [!code-xaml[BlockSnippets#_ParagraphSpacingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/BlockSnippets/CSharp/Window1.xaml#_paragraphspacingxaml)]
