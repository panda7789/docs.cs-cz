---
title: 'Postupy: Použití atributů pro oddělení sloupců FlowDocument'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 8693c8973442a5c6e65e64c5c66194c11bbff119
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57363779"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Postupy: Použití atributů pro oddělení sloupců FlowDocument
Tento příklad ukazuje, jak používat funkce oddělení sloupců <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje <xref:System.Windows.Documents.FlowDocument>a nastaví <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributy.  <xref:System.Windows.Documents.FlowDocument> Obsahuje jeden odstavec ukázkový obsah.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 Následující obrázek ukazuje účinky <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributů vykreslovaných <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Snímek obrazovky: Sloupec objektu FlowDocument](./media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")
