---
title: 'Postupy: Vytvoření elementu mřížky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], creating [WPF], grid instance
ms.assetid: b2f07626-9df8-43b8-8d36-492f3cb42837
ms.openlocfilehash: ebb9369da73bd595338e5b6ef42bda639bde6ed4
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59134534"
---
# <a name="how-to-create-a-grid-element"></a><span data-ttu-id="1f619-102">Postupy: Vytvoření elementu mřížky</span><span class="sxs-lookup"><span data-stu-id="1f619-102">How to: Create a Grid Element</span></span>
## <a name="example"></a><span data-ttu-id="1f619-103">Příklad</span><span class="sxs-lookup"><span data-stu-id="1f619-103">Example</span></span>  
 <span data-ttu-id="1f619-104">Následující příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.Controls.Grid> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu.</span><span class="sxs-lookup"><span data-stu-id="1f619-104">The following example shows how to create and use an instance of <xref:System.Windows.Controls.Grid> by using either [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] or code.</span></span> <span data-ttu-id="1f619-105">Tento příklad používá tři <xref:System.Windows.Controls.ColumnDefinition> objekty a tři <xref:System.Windows.Controls.RowDefinition> objekty, chcete-li vytvořit tabulku, která obsahuje devět buňky, například v listu.</span><span class="sxs-lookup"><span data-stu-id="1f619-105">This example uses three <xref:System.Windows.Controls.ColumnDefinition> objects and three <xref:System.Windows.Controls.RowDefinition> objects to create a grid that has nine cells, such as in a worksheet.</span></span> <span data-ttu-id="1f619-106">Každá buňka obsahuje <xref:System.Windows.Controls.TextBlock> obsahuje element, který představuje data a do horního řádku <xref:System.Windows.Controls.TextBlock> s <xref:System.Windows.Controls.Grid.ColumnSpan%2A> použita vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1f619-106">Each cell contains a <xref:System.Windows.Controls.TextBlock> element that represents data, and the top row contains a <xref:System.Windows.Controls.TextBlock> with the <xref:System.Windows.Controls.Grid.ColumnSpan%2A> property applied.</span></span> <span data-ttu-id="1f619-107">Chcete-li zobrazit hranice každá buňka <xref:System.Windows.Controls.Grid.ShowGridLines%2A> je povolena vlastnost.</span><span class="sxs-lookup"><span data-stu-id="1f619-107">To show the boundaries of each cell, the <xref:System.Windows.Controls.Grid.ShowGridLines%2A> property is enabled.</span></span>  
  
 [!code-csharp[Grid#3](~/samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](~/samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  <span data-ttu-id="1f619-108">Kterýkoliv přístup vygeneruje uživatelské rozhraní, které vypadá mnohem stejně, jako je ten níže.</span><span class="sxs-lookup"><span data-stu-id="1f619-108">Either approach will generate a user interface that looks much the same, like the one below.</span></span>

  ![snímek obrazovky znázorňuje uživatelské rozhraní WPF, které obsahuje dělí na tři sloupce mřížky.](././media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a><span data-ttu-id="1f619-112">Viz také:</span><span class="sxs-lookup"><span data-stu-id="1f619-112">See also</span></span>

- <xref:System.Windows.Controls.Grid>
- [<span data-ttu-id="1f619-113">Přehled panelu</span><span class="sxs-lookup"><span data-stu-id="1f619-113">Panels Overview</span></span>](panels-overview.md)
