---
title: 'Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- TextBox control [WPF], detecting text change
- text change [WPF], detecting
- detecting text change [WPF]
ms.assetid: 1c39ee14-e37f-49fb-a0d1-a9824ca13584
ms.openlocfilehash: 1adadb0f071815930d34f40ddf244ffc8c19131b
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59091145"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox
Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> události a metody pokaždé, když se text v <xref:System.Windows.Controls.TextBox> ovládacího prvku se změnil.  
  
 Ve třídě použití modelu code-behind pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , která obsahuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který chcete monitorovat změny vložit metodu volat pokaždé, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> dojde k aktivaci události.  Tato metoda musí mít podpis, který odpovídá očekávání podle <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.  
  
 Obslužná rutina události je volána pokaždé, když obsah <xref:System.Windows.Controls.TextBox> změní ovládacího prvku, uživatelem nebo prostřednictvím kódu programu.  
  
 **Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> ovládacího prvku je vytvořen a zpočátku zobrazí s textem.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , který definuje vaši <xref:System.Windows.Controls.TextBox> řídit, zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributu s hodnotou, která odpovídá názvu metody obslužné rutiny události.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Příklad  
 Ve třídě použití modelu code-behind pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] , která obsahuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který chcete monitorovat změny vložit metodu volat pokaždé, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> dojde k aktivaci události.  Tato metoda musí mít podpis, který odpovídá očekávání podle <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Obslužná rutina události je volána pokaždé, když obsah <xref:System.Windows.Controls.TextBox> změní ovládacího prvku, uživatelem nebo prostřednictvím kódu programu.  
  
 **Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> ovládacího prvku je vytvořen a zpočátku zobrazí s textem.  
  
 Komentáře  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.TextChangedEventArgs>
- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
