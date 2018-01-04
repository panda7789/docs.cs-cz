---
title: "Postupy: Použití atributů pro oddělení sloupců FlowDocument"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 779dd7862ba9a6f0d8656decc3ca0791574033fe
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Postupy: Použití atributů pro oddělení sloupců FlowDocument
Tento příklad ukazuje způsob použití funkce dělicí sloupec <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje <xref:System.Windows.Documents.FlowDocument>a nastaví <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributy.  <xref:System.Windows.Documents.FlowDocument> Obsahuje jeden odstavec Ukázka obsahu.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 Následující obrázek znázorňuje důsledky <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributů v vykreslené <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Snímek obrazovky: Sloupec objektu FlowDocument](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")
