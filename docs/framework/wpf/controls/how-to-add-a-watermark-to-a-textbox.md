---
title: 'Postupy: Přidání vodoznaku do pole TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
ms.openlocfilehash: ef2536f03ba6ed08e27d2fcf30cd1f72df2cf460
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61911613"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="bab42-102">Postupy: Přidání vodoznaku do pole TextBox</span><span class="sxs-lookup"><span data-stu-id="bab42-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="bab42-103">Následující příklad ukazuje, jak možnost využití pomoci pro <xref:System.Windows.Controls.TextBox> zobrazte obrázek na pozadí vysvětlující uvnitř <xref:System.Windows.Controls.TextBox> dokud uživatel vstupů text, kdy bitová kopie je odebrána.</span><span class="sxs-lookup"><span data-stu-id="bab42-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="bab42-104">Obrázek pozadí kromě toho je znovu obnovit, pokud uživatel odebere svůj vstup.</span><span class="sxs-lookup"><span data-stu-id="bab42-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="bab42-105">Podívejte se na následující ilustraci.</span><span class="sxs-lookup"><span data-stu-id="bab42-105">See illustration below.</span></span>  
  
 <span data-ttu-id="bab42-106">![Textové pole s imagí na pozadí](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="bab42-106">![A TextBox with a background image](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="bab42-107">Z důvodu obrázku na pozadí se používá v tomto příkladu manipulace se místo toho pak stačí <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox>, je, že obrázek pozadí neovlivní datové vazby.</span><span class="sxs-lookup"><span data-stu-id="bab42-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="bab42-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="bab42-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="bab42-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="bab42-109">See also</span></span>

- [<span data-ttu-id="bab42-110">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="bab42-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="bab42-111">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="bab42-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
