---
title: 'Postupy: Povolení znaků tabulátoru v ovládacím prvku TextBox'
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], enabling tab characters
- tab characters [WPF], enabling
ms.assetid: 14b1b064-61f7-4958-be63-88d85b868d03
ms.openlocfilehash: 9203a09408b4f88f3fbe8c0d87e365c1d05a1462
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-enable-tab-characters-in-a-textbox-control"></a>Postupy: Povolení znaků tabulátoru v ovládacím prvku TextBox
Tento příklad ukazuje, jak povolit přijetí karta znaků jako normální vstup v <xref:System.Windows.Controls.TextBox> ovládacího prvku.  
  
## <a name="example"></a>Příklad  
 K povolení přijetí karta znaků jako vstup ve <xref:System.Windows.Controls.TextBox> , nastavte <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsTab%2A> atribut **true**.  
  
 [!code-xaml[TextBox_EnablingTab#_AcceptsTab](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_EnablingTab/CS/Window1.xaml#_acceptstab)]  
  
## <a name="see-also"></a>Viz také  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
