---
title: "Postupy: Výběr mezi StackPanel a DockPanel"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
- cpp
helpviewer_keywords:
- controls [WPF], DockPanel
- DockPanel control [WPF], StackPanel control compared to
- StackPanel control [WPF], DockPanel control compared to
- controls [WPF], StackPanel
ms.assetid: f9239086-451f-42e6-81f7-ef89ef349742
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 0274a0f078c378a101bdf4a4ae456fd2ce9f4185
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Postupy: Výběr mezi StackPanel a DockPanel
Tento příklad ukazuje, jak si vybrat mezi pomocí <xref:System.Windows.Controls.StackPanel> nebo <xref:System.Windows.Controls.DockPanel> při zásobníku obsah <xref:System.Windows.Controls.Panel>.  
  
## <a name="example"></a>Příklad  
 I když můžete použít buď <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.StackPanel> do zásobníku podřízené elementy, dvou ovládacích prvků vždy nevedou stejné výsledky. Například pořadí umístit podřízené elementy může ovlivnit velikost podřízených elementů v <xref:System.Windows.Controls.DockPanel> , ale ne v <xref:System.Windows.Controls.StackPanel>. Různé chování dochází, protože <xref:System.Windows.Controls.StackPanel> míry ve směru překrývání v <xref:System.Double>.<xref:System.Double.PositiveInfinity>, nicméně <xref:System.Windows.Controls.DockPanel> měří pouze dostupné velikosti.  
  
 Následující příklad ukazuje tento spočívá hlavní rozdíl mezi <xref:System.Windows.Controls.DockPanel> a <xref:System.Windows.Controls.StackPanel>.  
  
 [!code-cpp[StackPanelOvw4#1](../../../../samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](../../../../samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](../../../../samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.StackPanel>  
 <xref:System.Windows.Controls.DockPanel>  
 [Přehled panelu](../../../../docs/framework/wpf/controls/panels-overview.md)
