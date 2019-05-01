---
title: 'Postupy: Použití atributů pro oddělení sloupců FlowDocument'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 27491b21da587fa198061ba52d8daed5d3f28de3
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62032033"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Postupy: Použití atributů pro oddělení sloupců FlowDocument
Tento příklad ukazuje, jak používat funkce oddělení sloupců <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje <xref:System.Windows.Documents.FlowDocument>a nastaví <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributy.  <xref:System.Windows.Documents.FlowDocument> Obsahuje jeden odstavec ukázkový obsah.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 Následující obrázek ukazuje účinky <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributů vykreslovaných <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Snímek obrazovky zobrazující atribut sloupec objektu FlowDocument.](./media/how-to-use-flowdocument-column-separating-attributes/flowdocument-intra-column.png)
