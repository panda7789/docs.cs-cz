---
title: 'Postupy: Použití elementů obsahu toku'
ms.date: 03/30/2017
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
ms.openlocfilehash: 146a785ef4f6da650144ed6fc47633670304bde6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33544128"
---
# <a name="how-to-use-flow-content-elements"></a><span data-ttu-id="16ec3-102">Postupy: Použití elementů obsahu toku</span><span class="sxs-lookup"><span data-stu-id="16ec3-102">How to: Use Flow Content Elements</span></span>
<span data-ttu-id="16ec3-103">Následující příklad ukazuje deklarativní využití pro různé prvky toku obsahu a přidružených atributů.</span><span class="sxs-lookup"><span data-stu-id="16ec3-103">The following example demonstrates declarative usage for various flow content elements and associated attributes.</span></span>  <span data-ttu-id="16ec3-104">Elementy a atributy ukázán patří:</span><span class="sxs-lookup"><span data-stu-id="16ec3-104">Elements and attributes demonstrated include:</span></span>  
  
-   <span data-ttu-id="16ec3-105"><xref:System.Windows.Documents.Bold> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-105"><xref:System.Windows.Documents.Bold> element</span></span>  
  
-   <span data-ttu-id="16ec3-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> Atribut</span><span class="sxs-lookup"><span data-stu-id="16ec3-106"><xref:System.Windows.Documents.Block.BreakPageBefore%2A> attribute</span></span>  
  
-   <span data-ttu-id="16ec3-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> Atribut</span><span class="sxs-lookup"><span data-stu-id="16ec3-107"><xref:System.Windows.Documents.TextElement.FontSize%2A> attribute</span></span>  
  
-   <span data-ttu-id="16ec3-108"><xref:System.Windows.Documents.Italic> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-108"><xref:System.Windows.Documents.Italic> element</span></span>  
  
-   <span data-ttu-id="16ec3-109"><xref:System.Windows.Documents.LineBreak> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-109"><xref:System.Windows.Documents.LineBreak> element</span></span>  
  
-   <span data-ttu-id="16ec3-110"><xref:System.Windows.Documents.List> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-110"><xref:System.Windows.Documents.List> element</span></span>  
  
-   <span data-ttu-id="16ec3-111"><xref:System.Windows.Documents.ListItem> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-111"><xref:System.Windows.Documents.ListItem> element</span></span>  
  
-   <span data-ttu-id="16ec3-112"><xref:System.Windows.Documents.Paragraph> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-112"><xref:System.Windows.Documents.Paragraph> element</span></span>  
  
-   <span data-ttu-id="16ec3-113"><xref:System.Windows.Documents.Run> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-113"><xref:System.Windows.Documents.Run> element</span></span>  
  
-   <span data-ttu-id="16ec3-114"><xref:System.Windows.Documents.Section> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-114"><xref:System.Windows.Documents.Section> element</span></span>  
  
-   <span data-ttu-id="16ec3-115"><xref:System.Windows.Documents.Span> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-115"><xref:System.Windows.Documents.Span> element</span></span>  
  
-   <span data-ttu-id="16ec3-116"><xref:System.Windows.Documents.Typography.Variants%2A> atribut (horní a dolní index)</span><span class="sxs-lookup"><span data-stu-id="16ec3-116"><xref:System.Windows.Documents.Typography.Variants%2A> attribute (superscript and subscript)</span></span>  
  
-   <span data-ttu-id="16ec3-117"><xref:System.Windows.Documents.Underline> – element</span><span class="sxs-lookup"><span data-stu-id="16ec3-117"><xref:System.Windows.Documents.Underline> element</span></span>  
  
## <a name="example"></a><span data-ttu-id="16ec3-118">Příklad</span><span class="sxs-lookup"><span data-stu-id="16ec3-118">Example</span></span>  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
