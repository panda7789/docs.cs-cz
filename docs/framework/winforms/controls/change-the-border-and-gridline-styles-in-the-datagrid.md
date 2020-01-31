---
title: Změna stylů ohraničení a mřížky v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- gridlines [Windows Forms], changing styles
- data grids [Windows Forms], changing gridline styles
- DataGridView control [Windows Forms], border styles
- data grids [Windows Forms], changing border styles
- DataGridView control [Windows Forms], gridline styles
ms.assetid: 2f413c7a-4025-4171-8e3a-66ef908ea583
ms.openlocfilehash: 918102a87ee29a3d3b78d6e6eedce57237135a51
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744695"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView
Pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete přizpůsobit vzhled ohraničení a mřížky ovládacího prvku pro zlepšení uživatelského prostředí. Kromě stylů ohraničení buněk v ovládacím prvku můžete měnit barvu mřížky a styl ohraničení ovládacího prvku. Pro obyčejné buňky, buňky záhlaví řádku a buňky záhlaví sloupce můžete také použít jiné styly ohraničení buňky.  
  
> [!NOTE]
> Barva mřížky se používá pouze v hodnotách <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>a <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> hodnoty výčtu <xref:System.Windows.Forms.DataGridViewCellBorderStyle> a <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> hodnota výčtu <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>. Ostatní hodnoty těchto výčtů používají barvy určené operačním systémem. Kromě toho, pokud jsou vizuální styly povoleny v systému Windows XP a v rodině systému Windows Server 2003 pomocí metody <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType>, není použita hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.GridColor%2A>.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Chcete-li změnit barvu mřížky programově  
  
- Nastavte vlastnost <xref:System.Windows.Forms.DataGridView.GridColor%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Změna stylu ohraničení celého ovládacího prvku DataGridView prostřednictvím kódu programu  
  
- Vlastnost <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> nastavte na jednu z hodnot výčtu <xref:System.Windows.Forms.BorderStyle>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Chcete-li změnit styly ohraničení pro buňky DataGridView programově  
  
- Nastavte vlastnosti <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>a <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>a <xref:System.Drawing?displayProperty=nameWithType>.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.BorderStyle>
- <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellBorderStyle>
- <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
