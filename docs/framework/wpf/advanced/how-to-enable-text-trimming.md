---
title: "Postupy: Povolení ořezávání textu"
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
- text [WPF], trimming
- documents [WPF], trimmng text
- trimmng text [WPF]
ms.assetid: dd8c9191-d2be-45fd-9fb4-3c75b65578c5
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: cdaafa62815c75d8ab364a18d909d867f90052c9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-enable-text-trimming"></a><span data-ttu-id="9b03a-102">Postupy: Povolení ořezávání textu</span><span class="sxs-lookup"><span data-stu-id="9b03a-102">How to: Enable Text Trimming</span></span>
<span data-ttu-id="9b03a-103">Tento příklad ukazuje použití a důsledků hodnoty, které jsou k dispozici v <xref:System.Windows.TextTrimming> výčtu.</span><span class="sxs-lookup"><span data-stu-id="9b03a-103">This example demonstrates the usage and effects of the values available in the <xref:System.Windows.TextTrimming> enumeration.</span></span>  
  
## <a name="example"></a><span data-ttu-id="9b03a-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b03a-104">Example</span></span>  
 <span data-ttu-id="9b03a-105">V následujícím příkladu definuje <xref:System.Windows.Controls.TextBlock> element s <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> nastaven atribut.</span><span class="sxs-lookup"><span data-stu-id="9b03a-105">The following example defines a <xref:System.Windows.Controls.TextBlock> element with the <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> attribute set.</span></span>  
  
 [!code-xaml[TextTrimmingSnippets#_TextTrimmingXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml#_texttrimmingxaml)]  
  
## <a name="example"></a><span data-ttu-id="9b03a-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="9b03a-106">Example</span></span>  
 <span data-ttu-id="9b03a-107">Nastavení odpovídající <xref:System.Windows.TextTrimming> je znázorněn vlastností v kódu.</span><span class="sxs-lookup"><span data-stu-id="9b03a-107">Setting the corresponding <xref:System.Windows.TextTrimming> property in code is demonstrated below.</span></span>  
  
 [!code-csharp[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextTrimmingSnippets/CSharp/Window1.xaml.cs#_texttrimmingsettexttrimming)]
 [!code-vb[TextTrimmingSnippets#_TextTrimmingSetTextTrimming](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextTrimmingSnippets/VisualBasic/Window1.xaml.vb#_texttrimmingsettexttrimming)]  
  
 <span data-ttu-id="9b03a-108">Jsou aktuálně tři možnosti pro text oříznutí: **CharacterEllipsis**, **WordEllipsis**, a **žádné**.</span><span class="sxs-lookup"><span data-stu-id="9b03a-108">There are currently three options for trimming text: **CharacterEllipsis**, **WordEllipsis**, and **None**.</span></span>  
  
 <span data-ttu-id="9b03a-109">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastaven na **CharacterEllipsis**, text je oříznut a dál se třemi tečkami na nejbližší okraj oříznutí znaků.</span><span class="sxs-lookup"><span data-stu-id="9b03a-109">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **CharacterEllipsis**, text is trimmed and continued with an ellipsis at the character closest to the trimming edge.</span></span>  <span data-ttu-id="9b03a-110">Toto nastavení se obvykle trim přizpůsobení přesněji na hranici oříznutí textu, ale může mít za následek slova částečně oříznuty.</span><span class="sxs-lookup"><span data-stu-id="9b03a-110">This setting tends to trim text to fit more closely to the trimming boundary, but may result in words being partially trimmed.</span></span>  <span data-ttu-id="9b03a-111">Následující obrázek znázorňuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobné definované výše.</span><span class="sxs-lookup"><span data-stu-id="9b03a-111">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="9b03a-112">![Příklad: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span><span class="sxs-lookup"><span data-stu-id="9b03a-112">![Example: TextTrimming.CharacterEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-character.png "TextTrimming_Character")</span></span>  
  
 <span data-ttu-id="9b03a-113">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastaven na **WordEllipsis**, text je oříznut a dál se třemi tečkami na konci prvního úplné slova nejbližší okraj oříznutí.</span><span class="sxs-lookup"><span data-stu-id="9b03a-113">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **WordEllipsis**, text is trimmed and continued with an ellipsis at the end of the first full word closest to the trimming edge.</span></span>  <span data-ttu-id="9b03a-114">Toto nastavení nebude zobrazit částečně oříznutý slova, ale obvykle není trim co nejvíce oříznutí okraj jako text **CharacterEllipsis** nastavení.</span><span class="sxs-lookup"><span data-stu-id="9b03a-114">This setting will not show partially trimmed words, but tends not to trim text as closely to the trimming edge as the **CharacterEllipsis** setting.</span></span>  <span data-ttu-id="9b03a-115">Následující obrázek znázorňuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> definované výše.</span><span class="sxs-lookup"><span data-stu-id="9b03a-115">The following figure shows the effect of this setting on the <xref:System.Windows.Controls.TextBlock> defined above.</span></span>  
  
 <span data-ttu-id="9b03a-116">![Příklad: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span><span class="sxs-lookup"><span data-stu-id="9b03a-116">![Example: TextTrimming.WordEllipsis](../../../../docs/framework/wpf/advanced/media/texttrimming-word.png "TextTrimming_Word")</span></span>  
  
 <span data-ttu-id="9b03a-117">Když <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> je nastaven na **žádné**, se provádí bez oříznutí text.</span><span class="sxs-lookup"><span data-stu-id="9b03a-117">When <xref:System.Windows.Controls.TextBlock.TextTrimming%2A> is set to **None**, no text trimming is performed.</span></span>  <span data-ttu-id="9b03a-118">V takovém případě text jednoduše oříznout na hranici nadřazený kontejner textu.</span><span class="sxs-lookup"><span data-stu-id="9b03a-118">In this case, text is simply cropped to the boundary of the parent text container.</span></span>  <span data-ttu-id="9b03a-119">Následující obrázek znázorňuje účinek tohoto nastavení na <xref:System.Windows.Controls.TextBlock> podobné definované výše.</span><span class="sxs-lookup"><span data-stu-id="9b03a-119">The following figure shows the effect of this setting on a <xref:System.Windows.Controls.TextBlock> similar to the one defined above.</span></span>  
  
 <span data-ttu-id="9b03a-120">![Příklad: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span><span class="sxs-lookup"><span data-stu-id="9b03a-120">![Example: TextTrimming.None](../../../../docs/framework/wpf/advanced/media/texttrimming-none.png "TextTrimming_None")</span></span>
