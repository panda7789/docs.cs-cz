---
title: 'Postupy: Výběr mezi StackPanel a DockPanel'
ms.date: 03/30/2017
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
ms.openlocfilehash: bdf4b38e67a7856136224368e86609c135e5ad6f
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73976431"
---
# <a name="how-to-choose-between-stackpanel-and-dockpanel"></a>Postupy: Výběr mezi StackPanel a DockPanel
Tento příklad ukazuje, jak zvolit způsob použití <xref:System.Windows.Controls.StackPanel> nebo <xref:System.Windows.Controls.DockPanel> při vrstvení obsahu v <xref:System.Windows.Controls.Panel>.

## <a name="example"></a>Příklad
 I když můžete použít buď <xref:System.Windows.Controls.DockPanel> nebo <xref:System.Windows.Controls.StackPanel> k zásobníku podřízených prvků, tyto dva ovládací prvky vždy nepřinesou stejné výsledky. Například pořadí, ve kterém umístíte podřízené prvky, může ovlivnit velikost podřízených prvků v <xref:System.Windows.Controls.DockPanel>, ale ne v <xref:System.Windows.Controls.StackPanel>. K tomuto odlišnému chování dochází, protože <xref:System.Windows.Controls.StackPanel> míry v směru skládání do [dvojitých. PositiveInfinity](xref:System.Double.PositiveInfinity); Nicméně <xref:System.Windows.Controls.DockPanel> míry pouze dostupné velikosti.

 Následující příklad ukazuje tento klíčový rozdíl mezi <xref:System.Windows.Controls.DockPanel> a <xref:System.Windows.Controls.StackPanel>.

 [!code-cpp[StackPanelOvw4#1](~/samples/snippets/cpp/VS_Snippets_Wpf/StackPanelOvw4/CPP/StackPanel_Ovw_Sample4.cpp#1)]
 [!code-csharp[StackPanelOvw4#1](~/samples/snippets/csharp/VS_Snippets_Wpf/StackPanelOvw4/CSharp/StackPanel_Ovw_Sample4.cs#1)]
 [!code-vb[StackPanelOvw4#1](~/samples/snippets/visualbasic/VS_Snippets_Wpf/StackPanelOvw4/VisualBasic/StackPanelSamp.vb#1)]
 [!code-xaml[StackPanelOvw4#1](~/samples/snippets/xaml/VS_Snippets_Wpf/StackPanelOvw4/XAML/default.xaml#1)]

## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.StackPanel>
- <xref:System.Windows.Controls.DockPanel>
- [Přehled panelu](panels-overview.md)
