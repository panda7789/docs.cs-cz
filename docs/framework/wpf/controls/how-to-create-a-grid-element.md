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
# <a name="how-to-create-a-grid-element"></a>Postupy: Vytvoření elementu mřížky
## <a name="example"></a>Příklad  
 Následující příklad ukazuje, jak vytvořit a použít instanci <xref:System.Windows.Controls.Grid> pomocí [!INCLUDE[TLA#tla_xaml](../../../../includes/tlasharptla-xaml-md.md)] nebo kódu. Tento příklad používá tři <xref:System.Windows.Controls.ColumnDefinition> objekty a tři <xref:System.Windows.Controls.RowDefinition> objekty, chcete-li vytvořit tabulku, která obsahuje devět buňky, například v listu. Každá buňka obsahuje <xref:System.Windows.Controls.TextBlock> obsahuje element, který představuje data a do horního řádku <xref:System.Windows.Controls.TextBlock> s <xref:System.Windows.Controls.Grid.ColumnSpan%2A> použita vlastnost. Chcete-li zobrazit hranice každá buňka <xref:System.Windows.Controls.Grid.ShowGridLines%2A> je povolena vlastnost.  
  
 [!code-csharp[Grid#3](~/samples/snippets/csharp/VS_Snippets_Wpf/Grid/CSharp/Grid_Code.cs#3)]
 [!code-vb[Grid#3](~/samples/snippets/visualbasic/VS_Snippets_Wpf/Grid/VisualBasic/grid_vb.vb#3)]
 [!code-xaml[Grid#3](~/samples/snippets/xaml/VS_Snippets_Wpf/Grid/XAML/default.xaml#3)]  
  
  Kterýkoliv přístup vygeneruje uživatelské rozhraní, které vypadá mnohem stejně, jako je ten níže.

  ![snímek obrazovky znázorňuje uživatelské rozhraní WPF, které obsahuje dělí na tři sloupce mřížky.  Nese záhlaví "2018 produkty dodáno" pokrývající všechny sloupce do horního řádku a má tři sloupce, každý s prodeji pro určité čtvrtletí.  Dolní řádek obsahuje text pokrývání uzlů dva sloupce se zprávou ' celkový počet jednotek: 300,000'](././media/how-to-create-a-grid-element/how-to-create-a-grid-element.png)
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Grid>
- [Přehled panelu](panels-overview.md)
