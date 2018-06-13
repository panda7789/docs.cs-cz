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
# <a name="how-to-use-flowdocument-column-separating-attributes"></a><span data-ttu-id="5fa8f-102">Postupy: Použití atributů pro oddělení sloupců FlowDocument</span><span class="sxs-lookup"><span data-stu-id="5fa8f-102">How to: Use FlowDocument Column-Separating Attributes</span></span>
<span data-ttu-id="5fa8f-103">Tento příklad ukazuje způsob použití funkce dělicí sloupec <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="5fa8f-103">This example shows how to use the column-separating features of a <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5fa8f-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5fa8f-104">Example</span></span>  
 <span data-ttu-id="5fa8f-105">V následujícím příkladu definuje <xref:System.Windows.Documents.FlowDocument>a nastaví <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributy.</span><span class="sxs-lookup"><span data-stu-id="5fa8f-105">The following example defines a <xref:System.Windows.Documents.FlowDocument>, and sets the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes.</span></span>  <span data-ttu-id="5fa8f-106"><xref:System.Windows.Documents.FlowDocument> Obsahuje jeden odstavec Ukázka obsahu.</span><span class="sxs-lookup"><span data-stu-id="5fa8f-106">The <xref:System.Windows.Documents.FlowDocument> contains a single paragraph of sample content.</span></span>  
  
 [!code-xaml[FlowDocumentSnippets#_FlowDocumentColumnStuffXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/FlowDocumentSnippets/CSharp/Window1.xaml#_flowdocumentcolumnstuffxaml)]  
  
 <span data-ttu-id="5fa8f-107">Následující obrázek znázorňuje důsledky <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, a <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> atributů v vykreslené <xref:System.Windows.Documents.FlowDocument>.</span><span class="sxs-lookup"><span data-stu-id="5fa8f-107">The following figure shows the effects of the <xref:System.Windows.Documents.FlowDocument.ColumnGap%2A>, <xref:System.Windows.Documents.FlowDocument.ColumnRuleBrush%2A>, and <xref:System.Windows.Documents.FlowDocument.ColumnRuleWidth%2A> attributes in a rendered <xref:System.Windows.Documents.FlowDocument>.</span></span>  
  
 <span data-ttu-id="5fa8f-108">![Snímek obrazovky: Sloupec objektu FlowDocument](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")</span><span class="sxs-lookup"><span data-stu-id="5fa8f-108">![Screenshot: FlowDocument Intra Column](../../../../docs/framework/wpf/advanced/media/flowdocumentintracolumn.png "FlowDocumentIntraColumn")</span></span>
