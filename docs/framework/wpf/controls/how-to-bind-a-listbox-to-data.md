---
title: "Postupy: Připojení prvku ListBox k datům"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- ListBox controls [WPF], binding data to
- data binding [WPF], ListBox control
- binding data [WPF], to ListBox control
ms.assetid: de93a907-709a-44a7-84bf-578b846a3d8b
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: a4701fe99231e115eb8cb14f7c1e5e003928bc5e
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
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
