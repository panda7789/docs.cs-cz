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
# <a name="how-to-add-a-watermark-to-a-textbox"></a>Postupy: Přidání vodoznaku do pole TextBox
Následující příklad ukazuje, jak lze pomoc <xref:System.Windows.Controls.TextBox> při použitelnosti pomocí zobrazení vysvětlující obrázku pozadí v <xref:System.Windows.Controls.TextBox> rámci až do zadání textu, v němž je obrázek odstraněn. Kromě toho je obrázek pozadí obnoven znovu, pokud uživatel odebere jejich vstup. Viz ilustrace níže.  
  
 ![Textové pole s obrázkem na pozadí](./media/editing-textbox-using-background-image.png "Editing_TextBox_using_background_image")  
  
> [!NOTE]
> Důvod, proč se v tomto příkladu použije obrázek pozadí a pak jednoduše manipuluje <xref:System.Windows.Controls.TextBox.Text%2A> s <xref:System.Windows.Controls.TextBox>vlastností, je to, že obrázek pozadí nebude v konfliktu s datovou vazbou.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[TextBoxMiscSnippets_snip#TextBoxBackgroundExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml#textboxbackgroundexamplewholepage)]  
  
 [!code-csharp[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/csharp/textbox_with_background_image.xaml.cs#textboxbackgroundcodeexamplewholepage)]
 [!code-vb[TextBoxMiscSnippets_snip#TextBoxBackgroundCodeExampleWholePage](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBoxMiscSnippets_snip/visualbasic/textbox_with_background_image.xaml.vb#textboxbackgroundcodeexamplewholepage)]  
  
## <a name="see-also"></a>Viz také:

- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
