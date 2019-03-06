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
ms.openlocfilehash: bcb368ababaac15dd92b11e43c22dfb705a7c0b3
ms.sourcegitcommit: 0c48191d6d641ce88d7510e319cf38c0e35697d0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/05/2019
ms.locfileid: "57365734"
---
# <a name="how-to-save-load-and-print-richtextbox-content"></a><span data-ttu-id="ea84c-102">Postupy: Uložení, načtení a tisk obsahu RichTextBox</span><span class="sxs-lookup"><span data-stu-id="ea84c-102">How to: Save, Load, and Print RichTextBox Content</span></span>
<span data-ttu-id="ea84c-103">Následující příklad ukazuje, jak uložit obsah <xref:System.Windows.Controls.RichTextBox> do souboru, načtení tohoto obsahu zpět do <xref:System.Windows.Controls.RichTextBox>a vytisknout obsah.</span><span class="sxs-lookup"><span data-stu-id="ea84c-103">The following example shows how to save content of a <xref:System.Windows.Controls.RichTextBox> to a file, load that content back into the <xref:System.Windows.Controls.RichTextBox>, and print the contents.</span></span>  
  
## <a name="example"></a><span data-ttu-id="ea84c-104">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea84c-104">Example</span></span>  
 <span data-ttu-id="ea84c-105">Níže je kód pro příklad.</span><span class="sxs-lookup"><span data-stu-id="ea84c-105">Below is the markup for the example.</span></span>  
  
 [!code-xaml[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml#saveloadprintrtbexamplewholepage)]  
  
## <a name="example"></a><span data-ttu-id="ea84c-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="ea84c-106">Example</span></span>  
 <span data-ttu-id="ea84c-107">Níže je kód za pro příklad.</span><span class="sxs-lookup"><span data-stu-id="ea84c-107">Below is the code behind for the example.</span></span>  
  
 [!code-csharp[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/CSharp/SaveLoadPrintRTB.xaml.cs#saveloadprintrtbcodeexamplewholepage)]
 [!code-vb[RichTextBoxMiscSnippets_snip#SaveLoadPrintRTBCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/RichTextBoxMiscSnippets_snip/VisualBasic/SaveLoadPrintRTB.xaml.vb#saveloadprintrtbcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="ea84c-108">Viz také:</span><span class="sxs-lookup"><span data-stu-id="ea84c-108">See also</span></span>
- [<span data-ttu-id="ea84c-109">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="ea84c-109">RichTextBox Overview</span></span>](richtextbox-overview.md)
- [<span data-ttu-id="ea84c-110">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="ea84c-110">TextBox Overview</span></span>](textbox-overview.md)
