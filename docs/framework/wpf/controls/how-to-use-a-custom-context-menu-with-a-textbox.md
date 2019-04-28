---
title: 'Postupy: Použití vlastní místní nabídky s prvkem TextBox'
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
ms.openlocfilehash: b0507c6fa37f0f51f9e12ebe5f908c39c25b50d9
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61699172"
---
# <a name="how-to-use-a-custom-context-menu-with-a-textbox"></a>Postupy: Použití vlastní místní nabídky s prvkem TextBox
Tento příklad ukazuje, jak definovat a implementovat jednoduchý vlastní místní nabídky pro <xref:System.Windows.Controls.TextBox>.  
  
## <a name="example"></a>Příklad  
 Následující [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] příklad definuje <xref:System.Windows.Controls.TextBox> ovládací prvek, který obsahuje vlastní místní nabídky.  
  
 V místní nabídce je definován pomocí <xref:System.Windows.Controls.ContextMenu> elementu.  V místní nabídce, samotné se skládá z řady <xref:System.Windows.Controls.MenuItem> elementy a <xref:System.Windows.Controls.Separator> elementy.  Každý <xref:System.Windows.Controls.MenuItem> element definuje příkaz v místní nabídce; <xref:System.Windows.Controls.HeaderedItemsControl.Header%2A> atribut definuje zobrazovaný text pro příkaz nabídky a <xref:System.Windows.Controls.MenuItem.Click> atribut určuje metodu obslužné rutiny pro každou položku nabídky.  <xref:System.Windows.Controls.Separator> Element pouze zajistí, že dělicí řádku mají být vykresleny mezi položkami nabídky předchozí a dalších.  
  
 [!code-xaml[TextBox_ContextMenu#_TextBox_ContextMenuXAML](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml#_textbox_contextmenuxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad ukazuje implementaci kód pro předchozí definice kontextové nabídky, stejně jako kód, který povolí nebo zakáže v místní nabídce.  <xref:System.Windows.Controls.ContextMenu.Opened> Událost se používá k dynamicky povolit nebo zakázat některé příkazy v závislosti na aktuální stav <xref:System.Windows.Controls.TextBox>.  
  
 Chcete-li obnovit výchozí místní nabídku, použijte <xref:System.Windows.DependencyObject.ClearValue%2A> metoda smazat hodnotu <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost.  Chcete-li zcela zakázat v místní nabídce, nastavte <xref:System.Windows.FrameworkElement.ContextMenu%2A> vlastnost odkaz s hodnotou null (`Nothing` v jazyce Visual Basic).  
  
 [!code-csharp[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/csharp/VS_Snippets_Wpf/TextBox_ContextMenu/CSharp/Window1.xaml.cs#_textbox_contextmenu)]
 [!code-vb[TextBox_ContextMenu#_TextBox_ContextMenu](~/samples/snippets/visualbasic/VS_Snippets_Wpf/TextBox_ContextMenu/VisualBasic/Window1.xaml.vb#_textbox_contextmenu)]  
  
## <a name="see-also"></a>Viz také:

- [Použití kontroly pravopisu s místní nabídkou](how-to-use-spell-checking-with-a-context-menu.md)
- [TextBox – přehled](textbox-overview.md)
- [RichTextBox – přehled](richtextbox-overview.md)
