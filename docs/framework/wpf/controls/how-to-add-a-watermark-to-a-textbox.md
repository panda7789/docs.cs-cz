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
ms.openlocfilehash: abe276c686d394ded13ec03f08deae65e4098d03
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69923580"
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="47f7a-102">Postupy: Přidání vodoznaku do pole TextBox</span><span class="sxs-lookup"><span data-stu-id="47f7a-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="47f7a-103">Následující příklad ukazuje, jak lze pomoc <xref:System.Windows.Controls.TextBox> při použitelnosti pomocí zobrazení vysvětlující obrázku pozadí v <xref:System.Windows.Controls.TextBox> rámci až do zadání textu, v němž je obrázek odstraněn.</span><span class="sxs-lookup"><span data-stu-id="47f7a-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="47f7a-104">Kromě toho je obrázek pozadí obnoven znovu, pokud uživatel odebere jejich vstup.</span><span class="sxs-lookup"><span data-stu-id="47f7a-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="47f7a-105">Viz ilustrace níže.</span><span class="sxs-lookup"><span data-stu-id="47f7a-105">See illustration below.</span></span>  
  
 <span data-ttu-id="47f7a-106">![Textové pole s obrázkem na pozadí](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="47f7a-106">![A TextBox with a background image](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
> <span data-ttu-id="47f7a-107">Důvod, proč se v tomto příkladu použije obrázek pozadí a pak jednoduše manipuluje <xref:System.Windows.Controls.TextBox.Text%2A> s <xref:System.Windows.Controls.TextBox>vlastností, je to, že obrázek pozadí nebude v konfliktu s datovou vazbou.</span><span class="sxs-lookup"><span data-stu-id="47f7a-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="47f7a-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="47f7a-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="47f7a-109">Viz také:</span><span class="sxs-lookup"><span data-stu-id="47f7a-109">See also</span></span>

- [<span data-ttu-id="47f7a-110">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="47f7a-110">TextBox Overview</span></span>](textbox-overview.md)
- [<span data-ttu-id="47f7a-111">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="47f7a-111">RichTextBox Overview</span></span>](richtextbox-overview.md)
