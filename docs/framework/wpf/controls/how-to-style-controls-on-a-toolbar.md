---
title: 'Postupy: Ovládací prvky stylu na objektu ToolBar'
ms.date: 03/30/2017
helpviewer_keywords:
- styling controls on toolbar [WPF]
- toolbars [WPF]
- customizing controls on toolbar [WPF]
ms.assetid: ba6ae056-d6a9-4c24-90f8-467ab0bc0b1a
ms.openlocfilehash: 78b9fc505c3c9045a0ca16ddaa1361c90bcc896a
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73459408"
---
# <a name="how-to-style-controls-on-a-toolbar"></a>Postupy: Ovládací prvky stylu na objektu ToolBar
<xref:System.Windows.Controls.ToolBar> definuje <xref:System.Windows.ResourceKey> objektů pro určení stylu ovládacích prvků v rámci <xref:System.Windows.Controls.ToolBar>.  Chcete-li nastavit styl ovládacího prvku v <xref:System.Windows.Controls.ToolBar>, nastavte atribut `x:key` stylu na <xref:System.Windows.ResourceKey> definovaný v <xref:System.Windows.Controls.ToolBar>.  
  
 <xref:System.Windows.Controls.ToolBar> definuje následující objekty <xref:System.Windows.ResourceKey>:  
  
- <xref:System.Windows.Controls.ToolBar.ButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.CheckBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ComboBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.MenuStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.RadioButtonStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.SeparatorStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.TextBoxStyleKey%2A>  
  
- <xref:System.Windows.Controls.ToolBar.ToggleButtonStyleKey%2A>  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje styly pro ovládací prvky v rámci <xref:System.Windows.Controls.ToolBar>.  
  
 [!code-xaml[ToolBar_snip#ToolBarAllStyles](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbarallstyles)]  
[!code-xaml[ToolBar_snip#ToolBar](~/samples/snippets/csharp/VS_Snippets_Wpf/ToolBar_snip/CS/pane1.xaml#toolbar)]  
  
## <a name="see-also"></a>Viz také:

- [Styly a šablony](../../../desktop-wpf/fundamentals/styles-templates-overview.md)
