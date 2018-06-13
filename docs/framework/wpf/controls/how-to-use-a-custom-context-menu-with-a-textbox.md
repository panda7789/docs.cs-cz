---
title: 'Postupy: Použití vlastní místní nabídky u objektu TextBox'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- context menus [WPF], custom
- menus [WPF], custom
- custom context menus [WPF]
- TextBox control [WPF], custom content menus
ms.assetid: 842d3cd5-6fa0-4be4-8d90-6c7466213b1c
ms.openlocfilehash: edcf6bdf381ae51a3354f9bc0b3c91d86e1f8f44
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552776"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>Postupy: Použití vlastní místní nabídky u objektu TextBox
Tento příklad ukazuje, jak definovat a implementovat jednoduchý vlastní kontextovou nabídku pro <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad definuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který obsahuje vlastní Kontextová nabídka.  
  
 V místní nabídce je definován pomocí <xref:System.Windows.Controls.ContextMenu> elementu.  V místní nabídce samotné se skládá z řady <xref:System.Windows.Controls.MenuItem> elementy a <xref:System.Windows.Controls.Separator> elementy.  Každý <xref:System.Windows.Controls.MenuItem> element definuje příkaz v místní nabídce; <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> atribut definuje zobrazovaný text pro příkaz nabídky a <xref:System.Windows.Controls.MenuItem.Click> atribut určuje metody obslužné rutiny pro každou položku nabídky.  <xref:System.Windows.Controls.Separator> Element jednoduše způsobí, že dělicí řádku k vykreslení mezi položky nabídky předchozí a další.  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje kód implementace pro definici předchozí kontextové nabídky, a také kód, který povolí nebo zakáže v místní nabídce.  <xref:System.Windows.Controls.ContextMenu.Opened> Se používá k dynamicky povolit nebo zakázat některé příkazy v závislosti na aktuální stav <xref:System.Windows.Controls.TextBox>.  
  
 Chcete-li obnovit výchozí místní nabídku, použijte <xref:System.Windows.DependencyObject.ClearValue%2A> metoda zrušte hodnotu <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost.  Chcete-li zcela zakázat kontextové nabídky, nastavte <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost, která má odkaz s hodnotou null (`Nothing` v jazyce Visual Basic).  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>Viz také  
 [Použití kontroly pravopisu s místní nabídkou](../../../../docs/framework/wpf/controls/how-to-use-spell-checking-with-a-context-menu.md)  
 [TextBox – přehled](../../../../docs/framework/wpf/controls/textbox-overview.md)  
 [RichTextBox – přehled](../../../../docs/framework/wpf/controls/richtextbox-overview.md)
