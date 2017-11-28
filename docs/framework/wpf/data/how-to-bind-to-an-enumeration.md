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
ms.openlocfilehash: 31fb9adbda47514e5405d465c0b5e2493b966d8c
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-bind-to-an-enumeration"></a>Postupy: Připojení k vyčíslení
Tento příklad ukazuje, jak vytvořit vazbu na výčet vazbou metodě GetValues ve výčtu.  
  
## <a name="example"></a>Příklad  
 V následujícím příkladu <xref:System.Windows.Controls.ListBox> zobrazí seznam <xref:System.Windows.HorizontalAlignment> hodnot výčtu prostřednictvím datové vazby. <xref:System.Windows.Controls.ListBox> a <xref:System.Windows.Controls.Button> jsou svázané s tak, že můžete změnit <xref:System.Windows.FrameworkElement.HorizontalAlignment%2A> hodnota vlastnosti <xref:System.Windows.Controls.Button> výběrem hodnoty v <xref:System.Windows.Controls.ListBox>.  
  
 [!code-xaml[BindToEnum#BindToEnum](../../../../samples/snippets/csharp/VS_Snippets_Wpf/BindToEnum/CS/Window1.xaml#bindtoenum)]  
  
## <a name="see-also"></a>Viz také  
 [Vytvoření vazby na třídu metodě](../../../../docs/framework/wpf/data/how-to-bind-to-a-method.md)  
 [Přehled vazba dat](../../../../docs/framework/wpf/data/data-binding-overview.md)  
 [Postupy: témata](../../../../docs/framework/wpf/data/data-binding-how-to-topics.md)
