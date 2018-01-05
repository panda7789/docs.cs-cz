---
title: "Postupy: Použití elementů obsahu toku"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- flow content elements [WPF]
- documents [WPF], flow content elements
ms.assetid: 70fa11cd-5fa7-4872-a1cc-04d80f1132be
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e637e114187d0864afe4211a45c346c1e5a449b6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-flow-content-elements"></a>Postupy: Použití elementů obsahu toku
Následující příklad ukazuje deklarativní využití pro různé prvky toku obsahu a přidružených atributů.  Elementy a atributy ukázán patří:  
  
-   <xref:System.Windows.Documents.Bold> – element  
  
-   <xref:System.Windows.Documents.Block.BreakPageBefore%2A>atribut  
  
-   <xref:System.Windows.Documents.TextElement.FontSize%2A>atribut  
  
-   <xref:System.Windows.Documents.Italic> – element  
  
-   <xref:System.Windows.Documents.LineBreak> – element  
  
-   <xref:System.Windows.Documents.List> – element  
  
-   <xref:System.Windows.Documents.ListItem> – element  
  
-   <xref:System.Windows.Documents.Paragraph> – element  
  
-   <xref:System.Windows.Documents.Run> – element  
  
-   <xref:System.Windows.Documents.Section> – element  
  
-   <xref:System.Windows.Documents.Span> – element  
  
-   <xref:System.Windows.Documents.Typography.Variants%2A>atribut (horní a dolní index)  
  
-   <xref:System.Windows.Documents.Underline> – element  
  
## <a name="example"></a>Příklad  
 [!code-xaml[FlowDocInlineSnippets#_InlineElementsXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocInlineSnippets/CS/document.xaml#_inlineelementsxaml)]
