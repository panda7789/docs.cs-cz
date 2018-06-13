---
title: 'Postupy: Použití atributů pro oddělení sloupců FlowDocument'
ms.date: 03/30/2017
helpviewer_keywords:
- FlowDocument column-separating attributes
- column-separating attributes
- documents [WPF], FlowDocument column-separating attributes
ms.assetid: c7a822f8-aeca-45bd-a258-2852ff28005c
ms.openlocfilehash: 678e01a35c286ea03f0385291d64f2f900f068c5
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33543768"
---
# <a name="how-to-use-flowdocument-column-separating-attributes"></a>Postupy: Použití atributů pro oddělení sloupců FlowDocument
Tento příklad ukazuje způsob použití funkce dělicí sloupec <xref:System.Windows.Documents.FlowDocument>.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje <xref:System.Windows.Documents.FlowDocument>a nastaví <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributy.  <xref:System.Windows.Documents.FlowDocument> Obsahuje jeden odstavec Ukázka obsahu.  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 Následující obrázek znázorňuje důsledky <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributů v vykreslené <xref:System.Windows.Documents.FlowDocument>.  
  
 ![Snímek obrazovky: Sloupec objektu FlowDocument](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")
