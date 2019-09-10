---
title: 'Postupy: Nastavení obsahu textu ovládacího prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 2e2bc70b108991fd4e3c138bfac5bff942173e33
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70856108"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Postupy: Nastavení obsahu textu ovládacího prvku TextBox

Tento příklad ukazuje, jak použít <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost k nastavení počátečního textového obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku.

> [!NOTE]
> <xref:System.Windows.Controls.TextBox> <xref:System.Windows.Markup.ContentPropertyAttribute> <xref:System.Windows.Controls.TextBox.Text%2A> <xref:System.Windows.Controls.TextBox> Přestože verze příkladu by mohla `<TextBox.Text>` používat značky kolem textu každého tlačítka, není nutné, protože atribut aplikuje na vlastnost. [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] . Další informace naleznete v tématu [Přehled XAML (WPF)](../advanced/xaml-overview-wpf.md).

## <a name="example"></a>Příklad

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Příklad

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Viz také:

- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
