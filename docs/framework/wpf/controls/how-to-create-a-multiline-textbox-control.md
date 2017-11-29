---
title: "Postupy: Vytvoření víceřádkového ovládacího prvku TextBox"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords: TextBox control [WPF], multiple lines of text
ms.assetid: 05914a93-d0ea-4a9a-b693-09df7d4e2ac2
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: 244eb38ea47bbd7376c2f8c6f5b2609fbd9c4330
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-multiline-textbox-control"></a>Postupy: Vytvoření víceřádkového ovládacího prvku TextBox
Tento příklad ukazuje, jak používat [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] k definování <xref:System.Windows.Controls.TextBox> ovládací prvek, který bude automaticky rozšířit, aby odpovídala více řádků textu.  
  
## <a name="example"></a>Příklad  
 Nastavení <xref:System.Windows.Controls.TextBox.TextWrapping%2A> atribut **zabalení** způsobí, že zadané text jej do nového řádku při okraji <xref:System.Windows.Controls.TextBox> ovládací prvek je dosaženo, automaticky se zvětšující <xref:System.Windows.Controls.TextBox> řízení zahrnout prostor pro nový řádek, pokud nezbytné.  
  
 Nastavení <xref:System.Windows.Controls.Primitives.TextBoxBase.AcceptsReturn%2A> atribut **true** způsobí, že má být vložen při stisknutí klávesy NÁVRATOVÝ, znovu automaticky rozšiřování nový řádek <xref:System.Windows.Controls.TextBox> zahrnout prostor pro nový řádek, v případě potřeby.  
  
 <xref:System.Windows.Controls.Primitives.TextBoxBase.VerticalScrollBarVisibility%2A> Přidá posuvníku do atribut <xref:System.Windows.Controls.TextBox>tak, aby obsah <xref:System.Windows.Controls.TextBox> posunout prostřednictvím Pokud <xref:System.Windows.Controls.TextBox> rozšíří překračuje velikost rámce nebo v okně, která obklopuje ho.  
  
 [!code-xaml[TextBox_MiscCode#_MultilineTextBoxXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_multilinetextboxxaml)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.TextWrapping>  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
