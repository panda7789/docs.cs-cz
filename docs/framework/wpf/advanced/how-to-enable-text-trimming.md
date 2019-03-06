---
title: 'Postupy: Povolení ořezávání textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 367e1f46524d8135d8269a2e2159dfe7c2468c45
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57354463"
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="0d0c5-102">Postupy: Povolení ořezávání textu</span><span class="sxs-lookup"><span data-stu-id="0d0c5-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="0d0c5-103">Tento příklad ukazuje použití a efekty hodnot, které jsou k dispozici v <xref:System.Windows.TextTrimming> výčtu.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="0d0c5-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d0c5-104">Example</span></span>  
 <span data-ttu-id="0d0c5-105">Následující příklad definuje <xref:System.Windows.Controls.TextBlock> křížkem <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> sadu atributů.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="0d0c5-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="0d0c5-106">Example</span></span>  
 <span data-ttu-id="0d0c5-107">Nastavení odpovídající <xref:System.Windows.TextTrimming> vlastností v kódu je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="0d0c5-108">Jsou nyní tři možnosti pro oříznutí textu: **CharacterEllipsis**, **WordEllipsis**, a **žádný**.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="0d0c5-109">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **CharacterEllipsis**, text je oříznut a pokračuje se třemi tečkami na znak, který je nejblíž k oříznutí edge.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="0d0c5-110">Toto nastavení obvykle mají být odebrány text, který lépe přizpůsobit na hranici ořezávání, ale může vést k slov, který částečně má být oříznut.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="0d0c5-111">Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobně jako výše.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="0d0c5-112">![Příklad: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="0d0c5-112">![Example: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="0d0c5-113">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **WordEllipsis**, text je oříznut a pokračovat tři tečky na konci prvního úplné slovo nejbližší na hraničních zařízeních oříznutí.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="0d0c5-114">Toto nastavení částečně oříznutý slova se nezobrazí, ale obvykle nechcete trim co nejvíce oříznutí edge jako text **CharacterEllipsis** nastavení.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="0d0c5-115">Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> výše.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="0d0c5-116">![Příklad: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="0d0c5-116">![Example: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="0d0c5-117">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **žádný**, se provádí bez ořezávání textu.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="0d0c5-118">V takovém případě text jednoduše ořízne na hranici jeho nadřazeného kontejneru text.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="0d0c5-119">Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobně jako výše.</span><span class="sxs-lookup"><span data-stu-id="0d0c5-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="0d0c5-120">![Příklad: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="0d0c5-120">![Example: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span></span>
