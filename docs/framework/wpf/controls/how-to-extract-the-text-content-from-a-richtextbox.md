---
title: 'Postupy: Extrahování textového obsahu z pole RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
ms.openlocfilehash: 309fe15c76c17a79e11341f3a50c0bf5a7a2cc21
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33553933"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a>Postupy: Extrahování textového obsahu z pole RichTextBox
Tento příklad ukazuje, jak extrahujte obsah <xref:System.Windows.Controls.RichTextBox> jako prostý text.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód popisuje pojmenovaná <xref:System.Windows.Controls.RichTextBox> ovládacího prvku s jednoduchým obsahem.  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a>Příklad  
 Následující kód implementuje metody, která přijímá <xref:System.Windows.Controls.RichTextBox> jako argument a vrátí řetězec představující obsah ve formátu prostého textu <xref:System.Windows.Controls.RichTextBox>.  
  
 Metoda vytvoří novou <xref:System.Windows.Documents.TextRange> z obsahu <xref:System.Windows.Controls.RichTextBox>pomocí <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> a <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> chcete období obsahu k extrakci.  <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> a <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> vlastnosti každého vrátí <xref:System.Windows.Documents.TextPointer>, na základní FlowDocument, který představuje obsah a jsou dostupné <xref:System.Windows.Controls.RichTextBox>.  <xref:System.Windows.Documents.TextRange> poskytuje vlastnosti textu, která vrátí části prostý text <xref:System.Windows.Documents.TextRange> jako řetězec.  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a>Viz také  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)
