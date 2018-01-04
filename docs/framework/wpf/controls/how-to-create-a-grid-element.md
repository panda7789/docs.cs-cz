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
ms.workload: dotnet
ms.openlocfilehash: 30fdd89a46e5d2027e9c525b0ca8cfcfb1d11ed2
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="bf6a1-102">Postupy: Vytvoření elementu mřížky</span><span class="sxs-lookup"><span data-stu-id="bf6a1-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="bf6a1-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="bf6a1-103">Example</span></span>  
 <span data-ttu-id="bf6a1-104">Následující příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.Controls.Grid> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="bf6a1-105">Tento příklad používá tři <xref:System.Windows.Controls.ColumnDefinition> objekty a tři <xref:System.Windows.Controls.RowDefinition> objekty, chcete-li vytvořit tabulku, která obsahuje 9 buněk, například v listu.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="bf6a1-106">Obsahuje jednotlivých buněk <xref:System.Windows.Controls.TextBlock> obsahuje element, který představuje data a horní řádek <xref:System.Windows.Controls.TextBlock> s <xref:System.Windows.Controls.Grid.ColumnSpan%2A> vlastnost použít.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="bf6a1-107">Zobrazit hranice jednotlivých buněk <xref:System.Windows.Controls.Grid.ShowGridLines%2A> vlastnost povolena.</span><span class="sxs-lookup"><span data-stu-id="bf6a1-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](../../../../samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](../../../../samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
## <a name="see-also"></a><span data-ttu-id="bf6a1-108">Viz také</span><span class="sxs-lookup"><span data-stu-id="bf6a1-108">See Also</span></span>  
 <xref:System.Windows.Controls.Grid>  
 [<span data-ttu-id="bf6a1-109">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="bf6a1-109">Panels Overview</span></span>](../../../../docs/framework/wpf/controls/panels-overview.md)
