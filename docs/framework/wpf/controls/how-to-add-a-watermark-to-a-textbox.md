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
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Postupy: Přidání vodoznaku do pole TextBox
Následující příklad ukazuje, jak možnost využití pomoci pro <xref:System.Windows.Controls.TextBox> zobrazte obrázek na pozadí vysvětlující uvnitř <xref:System.Windows.Controls.TextBox> dokud uživatel vstupů text, kdy bitová kopie je odebrána. Obrázek pozadí kromě toho je znovu obnovit, pokud uživatel odebere svůj vstup. Podívejte se na následující ilustraci.  
  
 ![Textové pole s imagí na pozadí](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
>  Z důvodu obrázku na pozadí se používá v tomto příkladu manipulace se místo toho pak stačí <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost <xref:System.Windows.Controls.TextBox>, je, že obrázek pozadí neovlivní datové vazby.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
