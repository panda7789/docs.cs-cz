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
ms.openlocfilehash: 1befd18220488334319a55bce2ce602aef20d3d6
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552949"
---
# <a name="how-to-detect-when-text-in-a-textbox-has-changed"></a>Postupy: Zjištění, kdy došlo ke změně textu v prvku TextBox
Tento příklad ukazuje jeden ze způsobů použití <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> události spuštění metody vždy, když text v <xref:System.Windows.Controls.TextBox> došlo ke změně ovládacího prvku.  
  
 Ve třídě kódu pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahující <xref:System.Windows.Controls.TextBox> vložit ovládací prvek, který chcete monitorovat změny, metoda k volání vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> je aktivována událost.  Tato metoda musí mít podpis, který odpovídá očekávané pomocí <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.  
  
 Je volána obslužná rutina události vždy, když obsah <xref:System.Windows.Controls.TextBox> řízení se změní, uživatelem nebo prostřednictvím kódu programu.  
  
 **Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> řízení se vytvoří a zpočátku zobrazí s textem.  
  
## <a name="example"></a>Příklad  
 V [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] , který definuje váš <xref:System.Windows.Controls.TextBox> řídit, zadejte <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> atributu s hodnotou, která odpovídá názvu metoda obslužná rutina události.  
  
 [!code-xaml[TextBox_MiscCode#_TextChangedXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml#_textchangedxaml)]  
  
## <a name="example"></a>Příklad  
 Ve třídě kódu pro [!INCLUDE[TLA2#tla_xaml](../../../../includes/tla2sharptla-xaml-md.md)] obsahující <xref:System.Windows.Controls.TextBox> vložit ovládací prvek, který chcete monitorovat změny, metoda k volání vždy, když <xref:System.Windows.Controls.Primitives.TextBoxBase.TextChanged> je aktivována událost.  Tato metoda musí mít podpis, který odpovídá očekávané pomocí <xref:System.Windows.Controls.TextChangedEventHandler> delegovat.  
  
 [!code-csharp[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_MiscCode/CSharp/Window1.xaml.cs#_textchangedeventhandler)]
 [!code-vb[TextBox_MiscCode#_TextChangedEventHandler](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_MiscCode/VisualBasic/Window1.xaml.vb#_textchangedeventhandler)]  
  
 Je volána obslužná rutina události vždy, když obsah <xref:System.Windows.Controls.TextBox> řízení se změní, uživatelem nebo prostřednictvím kódu programu.  
  
 **Poznámka:** Tato událost aktivuje, když <xref:System.Windows.Controls.TextBox> řízení se vytvoří a zpočátku zobrazí s textem.  
  
 Komentáře  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.TextChangedEventArgs>  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
