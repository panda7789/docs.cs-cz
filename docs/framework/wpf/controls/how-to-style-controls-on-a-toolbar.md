---
title: 'Postupy: Ovládací prvky stylu na objektu ToolBar'
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: cc5ac9dd64072c34ff999255a27dd92f311cda0f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-style-controls-on-a-toolbar"></a>Postupy: Ovládací prvky stylu na objektu ToolBar
<xref:System.Windows.Controls.ToolBar> Definuje <xref:System.Windows.ResourceKey> objekty, které chcete určit styl ovládacích prvků v rámci <xref:System.Windows.Controls.ToolBar>.  K formátování v ovládacím prvku <xref:System.Windows.Controls.ToolBar>, nastavte `x:key` styl do atribut <xref:System.Windows.ResourceKey> definované v <xref:System.Windows.Controls.ToolBar>.  
  
 <xref:System.Windows.Controls.ToolBar> Definuje následující <xref:System.Windows.ResourceKey> objekty:  
  
-   <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
-   <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu definuje styly pro ovládací prvky v rámci <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>Viz také  
 [Styly a šablony](../../../../docs/framework/wpf/controls/styling-and-templating.md)
