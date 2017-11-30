---
title: "Postupy: Extrahování textového obsahu z pole RichTextBox"
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
- text content [WPF], extracting
- RichTextBox control [WPF], extracting text content
- content [WPF], extracting
- extracting text content [WPF]
ms.assetid: f13c093f-1a05-45b3-ac8f-c9ea5e4a11c5
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: f24b71bcb5f013c4b7054dd0948e5f2709230a99
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a><span data-ttu-id="6b64c-102">Postupy: Extrahování textového obsahu z pole RichTextBox</span><span class="sxs-lookup"><span data-stu-id="6b64c-102">How to: Extract the Text Content from a RichTextBox</span></span>
<span data-ttu-id="6b64c-103">Tento příklad ukazuje, jak extrahujte obsah <xref:System.Windows.Controls.RichTextBox> jako prostý text.</span><span class="sxs-lookup"><span data-stu-id="6b64c-103">This example shows how to extract the contents of a <xref:System.Windows.Controls.RichTextBox> as plain text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="6b64c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b64c-104">Example</span></span>  
 <span data-ttu-id="6b64c-105">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód popisuje pojmenovaná <xref:System.Windows.Controls.RichTextBox> ovládacího prvku s jednoduchým obsahem.</span><span class="sxs-lookup"><span data-stu-id="6b64c-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a><span data-ttu-id="6b64c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="6b64c-106">Example</span></span>  
 <span data-ttu-id="6b64c-107">Následující kód implementuje metody, která přijímá <xref:System.Windows.Controls.RichTextBox> jako argument a vrátí řetězec představující obsah ve formátu prostého textu <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="6b64c-107">The following code implements a method that takes a <xref:System.Windows.Controls.RichTextBox> as an argument, and returns a string representing the plain text contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="6b64c-108">Metoda vytvoří novou <xref:System.Windows.Documents.TextRange> z obsahu <xref:System.Windows.Controls.RichTextBox>pomocí <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> a <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> chcete období obsahu k extrakci.</span><span class="sxs-lookup"><span data-stu-id="6b64c-108">The method creates a new <xref:System.Windows.Documents.TextRange> from the contents of the <xref:System.Windows.Controls.RichTextBox>, using the <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> to indicate the range of the contents to extract.</span></span>  <span data-ttu-id="6b64c-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A>a <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> vlastnosti každého vrátí <xref:System.Windows.Documents.TextPointer>, na základní FlowDocument, který představuje obsah a jsou dostupné <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="6b64c-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> properties each return a <xref:System.Windows.Documents.TextPointer>, and are accessible on the underlying FlowDocument that represents the contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  <span data-ttu-id="6b64c-110"><xref:System.Windows.Documents.TextRange>poskytuje vlastnosti textu, která vrátí části prostý text <xref:System.Windows.Documents.TextRange> jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="6b64c-110"><xref:System.Windows.Documents.TextRange> provides a Text property, which returns the plain text portions of the <xref:System.Windows.Documents.TextRange> as a string.</span></span>  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a><span data-ttu-id="6b64c-111">Viz také</span><span class="sxs-lookup"><span data-stu-id="6b64c-111">See Also</span></span>  
 [<span data-ttu-id="6b64c-112">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="6b64c-112">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="6b64c-113">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="6b64c-113">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
