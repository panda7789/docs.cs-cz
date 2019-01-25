---
title: 'Postupy: Připojení prvku ListBox k datům'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 6d37cda057ea1e7ca6761363857a2647da37afee
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54650649"
---
# <a name="how-to-bind-a-listbox-to-data"></a>Postupy: Připojení prvku ListBox k datům
Můžete vytvořit vývojář aplikace <xref:System.Windows.Controls.ListBox> ovládací prvky bez zadání obsah jednotlivých <xref:System.Windows.Controls.ListBoxItem> samostatně. Vytváření datových vazeb můžete použít k vytvoření vazby dat na jednotlivé položky.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.ListBox> , který naplní <xref:System.Windows.Controls.ListBoxItem> prvky pomocí datové vazby ke zdroji dat s názvem *barvy*. V tomto případě není nutné používat <xref:System.Windows.Controls.ListBoxItem> značky k určení obsahu každé položky.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [Ovládací prvky](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
