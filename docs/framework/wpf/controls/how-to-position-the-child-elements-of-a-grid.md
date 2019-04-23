---
title: 'Postupy: Umístění podřízených elementů mřížky'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- Grid control [WPF], positioning child elements
ms.assetid: 27b3ba9b-ad32-44e2-bcab-a79d573a463c
ms.openlocfilehash: c508f45c1ea3d0925503d6fe5600498a0558d5ad
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59202986"
---
# <a name="how-to-position-the-child-elements-of-a-grid"></a>Postupy: Umístění podřízených elementů mřížky
Tento příklad ukazuje způsob použití get a set metod, které jsou definovány na <xref:System.Windows.Controls.Grid> umístění podřízených elementů.  
  
## <a name="example"></a>Příklad  
 Následující příklad definuje nadřazený <xref:System.Windows.Controls.Grid> – element (`grid1`), který má tři sloupce a tři řádky. Podřízený <xref:System.Windows.Shapes.Rectangle> – element (`rect1`) se přidá do <xref:System.Windows.Controls.Grid> v pozici sloupce nula, řádek pozici nula. <xref:System.Windows.Controls.Button> elementy reprezentují metody, které lze volat pro přemístění <xref:System.Windows.Shapes.Rectangle> element v rámci <xref:System.Windows.Controls.Grid>. Když uživatel klikne na tlačítko, je aktivováno související metody.  
  
 [!code-xaml[gridGetSetMethods](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml)]  
  
 Následující příklad použití modelu code-behind zpracovává metody, která tlačítko <xref:System.Windows.Controls.Primitives.ButtonBase.Click> vyvolat události. Tento příklad zapíše tato volání metody <xref:System.Windows.Controls.TextBlock> prvky, které týkající se použití metody get na výstup nové hodnoty vlastnosti jako řetězce.  
  
 [!code-csharp[gridGetSetMethods#2](~/samples/snippets/csharp/VS_Snippets_Wpf/gridGetSetMethods/CSharp/Window1.xaml.cs#2)]
 [!code-vb[gridGetSetMethods#2](~/samples/snippets/visualbasic/VS_Snippets_Wpf/gridGetSetMethods/VisualBasic/Window1.xaml.vb#2)]  
 Tady je výsledku dokončeno!
 
 ![snímek obrazovky znázorňuje uživatelské rozhraní WPF se dvěma sloupci, pravé straně má mřížka 3 × 3 a levé straně tlačítka Přesunout barevný obdélník mezi sloupci a řádky mřížky](././media/grid-methods-sample.png) 
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.Grid>
- [Přehled panelu](panels-overview.md)
