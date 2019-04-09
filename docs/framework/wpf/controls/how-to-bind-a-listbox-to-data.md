---
title: 'Postupy: Svázání prvku ListBox s daty'
ms.date: 03/30/2017
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
ms.openlocfilehash: 4dea53a524247d18628b3e7e7b2c06906dced53d
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59106431"
---
# <a name="how-to-bind-a-listbox-to-data"></a>Postupy: Svázání prvku ListBox s daty
Můžete vytvořit vývojář aplikace <xref:System.Windows.Controls.ListBox> ovládací prvky bez zadání obsah jednotlivých <xref:System.Windows.Controls.ListBoxItem> samostatně. Vytváření datových vazeb můžete použít k vytvoření vazby dat na jednotlivé položky.  
  
 Následující příklad ukazuje, jak vytvořit <xref:System.Windows.Controls.ListBox> , který naplní <xref:System.Windows.Controls.ListBoxItem> prvky pomocí datové vazby ke zdroji dat s názvem *barvy*. V tomto případě není nutné používat <xref:System.Windows.Controls.ListBoxItem> značky k určení obsahu každé položky.  
  
## <a name="example"></a>Příklad  
 [!code-xaml[ListBoxEvent#7](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#7)]  
[!code-xaml[ListBoxEvent#3](~/samples/snippets/csharp/VS_Snippets_Wpf/ListBoxEvent/CSharp/Pane1.xaml#3)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.ListBox>
- <xref:System.Windows.Controls.ListBoxItem>
- [Ovládací prvky](../advanced/optimizing-performance-controls.md)
