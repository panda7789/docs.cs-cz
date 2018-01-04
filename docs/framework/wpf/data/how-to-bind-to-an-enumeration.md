---
title: "Postupy: Připojení k vyčíslení"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- binding data [WPF], enumeration
- data binding [WPF], enumeration
- enumeration [WPF]
ms.assetid: b9091eba-1119-424e-868b-d1a4168b3732
caps.latest.revision: "8"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 72439cdc1c1017378a5b6b3f6b4bf41a9eee2537
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-bind-to-an-enumeration"></a>Postupy: Připojení k vyčíslení
Tento příklad ukazuje, jak vytvořit vazbu na výčet vazbou metodě GetValues ve výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Controls.ListBox> zobrazí seznam <xref:System.Windows.HorizontalAlignment> hodnot výčtu prostřednictvím datové vazby. <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button> jsou svázané s tak, že můžete změnit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnota vlastnosti <xref:System.Windows.Controls.Button> výběrem hodnoty v <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby k metodě](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [Přehled datových vazeb](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Témata s postupy](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
