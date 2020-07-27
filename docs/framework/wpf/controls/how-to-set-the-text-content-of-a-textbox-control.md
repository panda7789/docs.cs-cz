---
title: 'Postupy: Nastavení obsahu textu ovládacího prvku TextBox'
description: Naučte se používat vlastnost text k nastavení počátečního textového obsahu ovládacího prvku TextBox Windows Presentation Foundation.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- text content [WPF], setting
- TextBox control [WPF], setting text content
ms.assetid: bcd25fc7-a52f-4453-b802-2c8d2b335ab8
ms.openlocfilehash: 41efb69e297b3c6fdb1203c358dcc72d7a9f806f
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87168048"
---
# <a name="how-to-set-the-text-content-of-a-textbox-control"></a>Postupy: Nastavení obsahu textu ovládacího prvku TextBox

Tento příklad ukazuje, jak použít <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost k nastavení počátečního textového obsahu <xref:System.Windows.Controls.TextBox> ovládacího prvku.

> [!NOTE]
> Přestože [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] verze příkladu může používat `<TextBox.Text>` značky kolem textu každého tlačítka <xref:System.Windows.Controls.TextBox> , není nutné, protože <xref:System.Windows.Controls.TextBox> atribut aplikuje na <xref:System.Windows.Markup.ContentPropertyAttribute> <xref:System.Windows.Controls.TextBox.Text%2A> vlastnost. Další informace naleznete v tématu [Přehled XAML (WPF)](../../../desktop-wpf/fundamentals/xaml.md).

## <a name="example"></a>Příklad

[!code-xaml[TextBox_MiscCode#_TextBoxSetTextXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxsettextxaml)]

## <a name="example"></a>Příklad

[!code-csharp[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textboxsettext)]
[!code-vb[TextBox_MiscCode#_TextBoxSetText](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textboxsettext)]

## <a name="see-also"></a>Viz také

- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
