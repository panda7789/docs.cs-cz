---
title: "Postupy: Přidání vodoznaku do pole TextBox"
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
- displaying a background image inside a text box to aid user input [WPF]
- aid usability of a TextBox using a background image [WPF]
ms.assetid: df89bdd8-a0fb-45e0-b312-dd53332d01a8
caps.latest.revision: "5"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 4497b72f229a8f3d62ecb1829fda88ea3d76bbb0
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-add-a-watermark-to-a-textbox"></a><span data-ttu-id="5a5b0-102">Postupy: Přidání vodoznaku do pole TextBox</span><span class="sxs-lookup"><span data-stu-id="5a5b0-102">How to: Add a Watermark to a TextBox</span></span>
<span data-ttu-id="5a5b0-103">Následující příklad ukazuje, jak můžete docílit použitelnost <xref:System.Windows.Controls.TextBox> zobrazením obrázek pozadí vysvětlující uvnitř <xref:System.Windows.Controls.TextBox> dokud uživatel vstup text, v tomto okamžiku bitová kopie je odebrána.</span><span class="sxs-lookup"><span data-stu-id="5a5b0-103">The following example shows how to aid usability of a <xref:System.Windows.Controls.TextBox> by displaying an explanatory background image inside of the <xref:System.Windows.Controls.TextBox> until the user inputs text, at which point the image is removed.</span></span> <span data-ttu-id="5a5b0-104">Kromě toho je obrázku pozadí obnoven znovu, pokud uživatel odebere jejich vstup.</span><span class="sxs-lookup"><span data-stu-id="5a5b0-104">In addition, the background image is restored again if the user removes their input.</span></span> <span data-ttu-id="5a5b0-105">Viz následující obrázek.</span><span class="sxs-lookup"><span data-stu-id="5a5b0-105">See illustration below.</span></span>  
  
 <span data-ttu-id="5a5b0-106">![Textové pole s obrázek pozadí](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span><span class="sxs-lookup"><span data-stu-id="5a5b0-106">![A TextBox with a background image](../../../../docs/framework/wpf/controls/media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="5a5b0-107">Z důvodu obrázek na pozadí se používá v tomto příkladu místo pak jednoduše manipulace s nimi <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox>, je, že obrázek pozadí nebude ovlivňovat datová vazba.</span><span class="sxs-lookup"><span data-stu-id="5a5b0-107">The reason a background image is used in this example rather then simply manipulating the <xref:System.Windows.Controls.TextBox.Text%2A> property of <xref:System.Windows.Controls.TextBox>, is that a background image will not interfere with data binding.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5a5b0-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="5a5b0-108">Example</span></span>  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a><span data-ttu-id="5a5b0-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="5a5b0-109">See Also</span></span>  
 [<span data-ttu-id="5a5b0-110">TextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="5a5b0-110">TextBox Overview</span></span>](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [<span data-ttu-id="5a5b0-111">RichTextBox – přehled</span><span class="sxs-lookup"><span data-stu-id="5a5b0-111">RichTextBox Overview</span></span>](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
