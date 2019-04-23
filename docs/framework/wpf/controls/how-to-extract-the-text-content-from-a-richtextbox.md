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
ms.openlocfilehash: 220da59ec893528c99014e9ec95fb185c461b291
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59086114"
---
# <a name="how-to-extract-the-text-content-from-a-richtextbox"></a><span data-ttu-id="f8abb-102">Postupy: Extrahování textového obsahu z pole RichTextBox</span><span class="sxs-lookup"><span data-stu-id="f8abb-102">How to: Extract the Text Content from a RichTextBox</span></span>
<span data-ttu-id="f8abb-103">Tento příklad ukazuje, jak extrahujte obsah <xref:System.Windows.Controls.RichTextBox> jako prostý text.</span><span class="sxs-lookup"><span data-stu-id="f8abb-103">This example shows how to extract the contents of a <xref:System.Windows.Controls.RichTextBox> as plain text.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f8abb-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8abb-104">Example</span></span>  
 <span data-ttu-id="f8abb-105">Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] kód popisuje pojmenovaná <xref:System.Windows.Controls.RichTextBox> ovládacího prvku s jednoduchým obsahem.</span><span class="sxs-lookup"><span data-stu-id="f8abb-105">The following [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] code describes a named <xref:System.Windows.Controls.RichTextBox> control with simple content.</span></span>  
  
 [!code-xaml[RichTextBoxSnippets#_RTB_XAML](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml#_rtb_xaml)]  
  
## <a name="example"></a><span data-ttu-id="f8abb-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="f8abb-106">Example</span></span>  
 <span data-ttu-id="f8abb-107">Následující kód implementuje metodu, která přijímá <xref:System.Windows.Controls.RichTextBox> jako argument a vrátí řetězec představující obsah ve formátu prostého textu <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f8abb-107">The following code implements a method that takes a <xref:System.Windows.Controls.RichTextBox> as an argument, and returns a string representing the plain text contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  
  
 <span data-ttu-id="f8abb-108">Metoda vytvoří nový <xref:System.Windows.Documents.TextRange> z obsahu <xref:System.Windows.Controls.RichTextBox>, použije <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> a <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> k označení rozsahu obsah k extrakci.</span><span class="sxs-lookup"><span data-stu-id="f8abb-108">The method creates a new <xref:System.Windows.Documents.TextRange> from the contents of the <xref:System.Windows.Controls.RichTextBox>, using the <xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> to indicate the range of the contents to extract.</span></span>  <span data-ttu-id="f8abb-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> a <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> vrátit jednotlivé vlastnosti <xref:System.Windows.Documents.TextPointer>a jsou k dispozici na základní FlowDocument, který představuje obsah <xref:System.Windows.Controls.RichTextBox>.</span><span class="sxs-lookup"><span data-stu-id="f8abb-109"><xref:System.Windows.Documents.FlowDocument.ContentStart%2A> and <xref:System.Windows.Documents.FlowDocument.ContentEnd%2A> properties each return a <xref:System.Windows.Documents.TextPointer>, and are accessible on the underlying FlowDocument that represents the contents of the <xref:System.Windows.Controls.RichTextBox>.</span></span>  <span data-ttu-id="f8abb-110"><xref:System.Windows.Documents.TextRange> poskytuje vlastnosti textu, která vrátí části ve formátu prostého textu <xref:System.Windows.Documents.TextRange> jako řetězec.</span><span class="sxs-lookup"><span data-stu-id="f8abb-110"><xref:System.Windows.Documents.TextRange> provides a Text property, which returns the plain text portions of the <xref:System.Windows.Documents.TextRange> as a string.</span></span>  
  
 [!code-csharp[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxSnippets/CSharp/Window1.xaml.cs#_rtb_stringfrom)]
 [!code-vb[RichTextBoxSnippets#_RTB_StringFrom](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxSnippets/visualbasic/window1.xaml.vb#_rtb_stringfrom)]  
  
## <a name="see-also"></a><span data-ttu-id="f8abb-111">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f8abb-111">See also</span></span>

- [<span data-ttu-id="f8abb-112">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="f8abb-112">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="f8abb-113">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="f8abb-113">TextBox Overview</span></span>](textbox-overview.md)
