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
ms.openlocfilehash: 9b16f2d99295a28725255361b0be3ef7f4245fd2
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459299"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Postupy: Nastavení obsahu textu ovládacího prvku TextBox

Tento příklad ukazuje, jak použít vlastnost <xref:System.Windows.Controls.TextBox.Text%2A> k nastavení počátečního textového obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku.

> [!NOTE]
> I když [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] verze příkladu může použít značky `<TextBox.Text>` kolem textu <xref:System.Windows.Controls.TextBox> obsahu jednotlivých tlačítek, není nutné, protože <xref:System.Windows.Controls.TextBox> použije atribut <xref:System.Windows.Markup.ContentPropertyAttribute> na vlastnost <xref:System.Windows.Controls.TextBox.Text%2A>. Další informace naleznete v tématu [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a>Příklad

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Příklad

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Viz také:

- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
