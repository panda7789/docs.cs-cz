---
title: 'Postupy: Povolení ořezávání textu'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text [WPF], trimming
- documents [WPF], trimming text
- trimming text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
ms.openlocfilehash: 25fff566868e792004a915fee195485c4a1f385f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61776103"
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="c0d3b-102">Postupy: Povolení ořezávání textu</span><span class="sxs-lookup"><span data-stu-id="c0d3b-102">How to: Enable Text Trimming</span></span>

<span data-ttu-id="c0d3b-103">Tento příklad ukazuje použití a efekty hodnot, které jsou k dispozici v <xref:System.Windows.TextTrimming> výčtu.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>

## <a name="example"></a><span data-ttu-id="c0d3b-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="c0d3b-104">Example</span></span>

<span data-ttu-id="c0d3b-105">Následující příklad definuje <xref:System.Windows.Controls.TextBlock> křížkem <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> sadu atributů.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>

[!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]

<span data-ttu-id="c0d3b-106">Nastavení odpovídající <xref:System.Windows.TextTrimming> vlastností v kódu je znázorněno níže.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-106">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>

[!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
[!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]

<span data-ttu-id="c0d3b-107">Jsou nyní tři možnosti pro oříznutí textu: **CharacterEllipsis**, **WordEllipsis**, a **žádný**.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-107">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>

<span data-ttu-id="c0d3b-108">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **CharacterEllipsis**, text je oříznut a pokračuje se třemi tečkami na znak, který je nejblíž k oříznutí edge.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-108">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="c0d3b-109">Toto nastavení obvykle mají být odebrány text, který lépe přizpůsobit na hranici ořezávání, ale může vést k slov, který částečně má být oříznut.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-109">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="c0d3b-110">Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobně jako výše.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-110">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>

<span data-ttu-id="c0d3b-111">![Příklad: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="c0d3b-111">![Example: TextTrimming.CharacterEllipsis](./media/texttrimming-character.png "TextTrimming_Character")</span></span>

<span data-ttu-id="c0d3b-112">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **WordEllipsis**, text je oříznut a pokračovat tři tečky na konci prvního úplné slovo nejbližší na hraničních zařízeních oříznutí.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-112">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="c0d3b-113">Toto nastavení částečně oříznutý slova se nezobrazí, ale obvykle nechcete trim co nejvíce oříznutí edge jako text **CharacterEllipsis** nastavení.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-113">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="c0d3b-114">Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> výše.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-114">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>

<span data-ttu-id="c0d3b-115">![Příklad: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="c0d3b-115">![Example: TextTrimming.WordEllipsis](./media/texttrimming-word.png "TextTrimming_Word")</span></span>

<span data-ttu-id="c0d3b-116">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastavena na **žádný**, se provádí bez ořezávání textu.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-116">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="c0d3b-117">V takovém případě text jednoduše ořízne na hranici jeho nadřazeného kontejneru text.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-117">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="c0d3b-118">Následující obrázek ukazuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobně jako výše.</span><span class="sxs-lookup"><span data-stu-id="c0d3b-118">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>

<span data-ttu-id="c0d3b-119">![Příklad: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="c0d3b-119">![Example: TextTrimming.None](./media/texttrimming-none.png "TextTrimming_None")</span></span>
