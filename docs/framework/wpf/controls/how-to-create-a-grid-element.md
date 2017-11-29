---
title: "Postupy: Vytvoření elementu mřížky"
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
helpviewer_keywords: Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: bd9614aee6e2bf7085b2fbee77993217439320a5
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-create-a-grid-element"></a>Postupy: Vytvoření elementu mřížky
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.Controls.Grid> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu. Tento příklad používá tři <xref:System.Windows.Controls.ColumnDefinition> objekty a tři <xref:System.Windows.Controls.RowDefinition> objekty, chcete-li vytvořit tabulku, která obsahuje 9 buněk, například v listu. Obsahuje jednotlivých buněk <xref:System.Windows.Controls.TextBlock> obsahuje element, který představuje data a horní řádek <xref:System.Windows.Controls.TextBlock> s <xref:System.Windows.Controls.Grid.ColumnSpan%2A> vlastnost použít. Zobrazit hranice jednotlivých buněk <xref:System.Windows.Controls.Grid.ShowGridLines%2A> vlastnost povolena.  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.Grid>  
 [Přehled panelů](../../../../docs/framework/wpf/controls/panels-overview.md)
