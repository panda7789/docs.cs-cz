---
title: 'Postupy: Ovládací prvky stylu na prvku ToolBar'
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: 580b56ebb47aa7bd50da0a966ccf60f7ea9fb2a7
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59217780"
---
# <a name="how-to-style-controls-on-a-toolbar"></a>Postupy: Ovládací prvky stylu na prvku ToolBar
<xref:System.Windows.Controls.ToolBar> Definuje <xref:System.Windows.ResourceKey> objekty k určení stylu ovládacích prvků v rámci <xref:System.Windows.Controls.ToolBar>.  K úpravě stylu ovládacího prvku v <xref:System.Windows.Controls.ToolBar>, nastavte `x:key` atribut styl, který má <xref:System.Windows.ResourceKey> definované v <xref:System.Windows.Controls.ToolBar>.  
  
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
 Následující příklad definuje styly pro ovládací prvky v rámci <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](styling-and-templating.md)
