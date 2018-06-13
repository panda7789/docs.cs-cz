---
title: 'Postupy: Připojení prvku ListBox k datům'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 186d25750c5ce196a5e46c02f0f56e2440ea3a25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33552828"
---
# <a name="how-to-bind-a-listbox-to-data"></a>Postupy: Připojení prvku ListBox k datům
Můžete vytvořit vývojář aplikace <xref:System.Windows.Controls.ListBox> ovládacích prvků bez zadání obsah jednotlivých <xref:System.Windows.Controls.ListBoxItem> samostatně. Datová vazba slouží k vytvoření vazby dat na jednotlivé položky.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.ListBox> který naplní <xref:System.Windows.Controls.ListBoxItem> elementy podle datové vazby ke zdroji dat s názvem *barvy*. V takovém případě není nutné používat <xref:System.Windows.Controls.ListBoxItem> značky k určení obsahu jednotlivých položek.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[ListBoxEvent#7](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.ListBox>  
 <xref:System.Windows.Controls.ListBoxItem>  
 [Ovládací prvky](../../../../docs/framework/wpf/advanced/optimizing-performance-controls.md)
