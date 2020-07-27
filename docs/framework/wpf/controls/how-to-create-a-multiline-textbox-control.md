---
title: 'Postupy: Vytvoření víceřádkového ovládacího prvku TextBox'
description: Naučte se používat XAML k definování ovládacího prvku TextBox, který se rozbalí, aby odpovídal více řádkům textu v aplikaci Windows Presentation Foundation.
ms.date: 03/30/2017
helpviewer_keywords:
- TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
ms.openlocfilehash: 0a88d4d768884df135afddb491431650b9ba2d24
ms.sourcegitcommit: 87cfeb69226fef01acb17c56c86f978f4f4a13db
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/24/2020
ms.locfileid: "87166247"
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Postupy: Vytvoření víceřádkového ovládacího prvku TextBox
Tento příklad ukazuje, jak použít [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.TextBox> ovládacího prvku, který se automaticky rozbalí, aby odpovídal více řádkům textu.  
  
## <a name="example"></a>Příklad  
 Nastavením <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atributu pro **zabalení** dojde k zabalení zadaného textu do nového řádku, pokud <xref:System.Windows.Controls.TextBox> je dosaženo okraje ovládacího prvku, automatické rozšíření <xref:System.Windows.Controls.TextBox> ovládacího prvku tak, aby v případě potřeby zahrnoval prostor pro nový řádek.  
  
 Nastavením <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atributu na **hodnotu true** dojde k vložení nového řádku při stisknutí návratového klíče, jakmile se znovu automaticky rozbalí, <xref:System.Windows.Controls.TextBox> aby obsahovalo místo pro nový řádek (v případě potřeby).  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A>Atribut přidá posuvník do <xref:System.Windows.Controls.TextBox> , aby bylo možné obsah ovládacího panelu Procházet, <xref:System.Windows.Controls.TextBox> Pokud se <xref:System.Windows.Controls.TextBox> rozšíří nad rámec velikosti rámce nebo okna, které ho obklopuje.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.TextWrapping>
- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
