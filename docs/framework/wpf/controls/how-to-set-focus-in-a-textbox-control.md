---
title: 'Postupy: Nastavení fokusu v ovládacím prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- focus [WPF], setting
- TextBox control [WPF], setting focus
ms.assetid: 24b61b45-dc2d-425e-9839-b017af7ab86f
ms.openlocfilehash: f4ba367ea9bdfcd6dbab7a5015472ec33adfe46f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "62024349"
---
# <a name="how-to-set-focus-in-a-textbox-control"></a>Postupy: Nastavení fokusu v ovládacím prvku TextBox
Tento příklad ukazuje způsob použití <xref:System.Windows.UIElement.Focus%2A> zaměřit se na metodu <xref:System.Windows.Controls.TextBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad popisuje jednoduchý <xref:System.Windows.Controls.TextBox> ovládací prvek s názvem *tbFocusMe*  
  
 [!code-xaml[TextBox_MiscCode#_TextBoxFocusXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textboxfocusxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad volá <xref:System.Windows.UIElement.Focus%2A> metoda se zaměřit na <xref:System.Windows.Controls.TextBox> ovládací prvek s názvem *tbFocusMe*.  
  
 [!code-csharp[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_focustextbox)]
 [!code-vb[TextBox_MiscCode#_FocusTextBox](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_focustextbox)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.UIElement.Focusable%2A>
- <xref:System.Windows.UIElement.IsFocused%2A>
- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
