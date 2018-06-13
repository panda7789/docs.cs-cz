---
title: 'Postupy: Uložení, načtení a tisk obsahu RichTextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- saving RichTextBox controls [WPF]
- printing RichTextBox controls [WPF]
- loading RichTextBox controls [WPF]
- RichTextBox control [WPF], saving
- RichTextBox control [WPF], printing
- RichTextBox control [WPF], loading
ms.assetid: ffb113d3-c68a-47ca-8ac0-882283f38326
ms.openlocfilehash: df43a5f5cabd664bb8514967456a67ba3699d5a3
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552916"
---
# <a name="how-to-save-load-and-print-richtextbox-content"></a><span data-ttu-id="5f82c-102">Postupy: Uložení, načtení a tisk obsahu RichTextBox</span><span class="sxs-lookup"><span data-stu-id="5f82c-102">How to: Save, Load, and Print RichTextBox Content</span></span>
<span data-ttu-id="5f82c-103">Následující příklad ukazuje, jak uložit obsah <xref:System.Windows.Controls.RichTextBox> do souboru, načíst tento obsah zpět do <xref:System.Windows.Controls.RichTextBox>a tisknout obsah.</span><span class="sxs-lookup"><span data-stu-id="5f82c-103">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5f82c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f82c-104">Example</span></span>  
 <span data-ttu-id="5f82c-105">Níže je kód pro tento příklad.</span><span class="sxs-lookup"><span data-stu-id="5f82c-105">Below is the markup for the example.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="5f82c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="5f82c-106">Example</span></span>  
 <span data-ttu-id="5f82c-107">Níže je pro tento příklad kódu.</span><span class="sxs-lookup"><span data-stu-id="5f82c-107">Below is the code behind for the example.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5f82c-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="5f82c-108">See Also</span></span>  
 [<span data-ttu-id="5f82c-109">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="5f82c-109">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)  
 [<span data-ttu-id="5f82c-110">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="5f82c-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)
