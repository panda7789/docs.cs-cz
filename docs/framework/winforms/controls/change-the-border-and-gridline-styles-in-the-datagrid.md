---
title: 'Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 94e5ae11d7fb2b67e028f368183246f8d8543a08
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView
Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete přizpůsobit vzhled ovládacího prvku ohraničení a mřížky ke zlepšení činnost koncového uživatele. Můžete upravit barvy čar mřížky a styl ohraničení ovládacího prvku kromě styly ohraničení buněk v ovládacím prvku. Můžete také použít jinou buňku styly ohraničení pro běžné buněk, buňky záhlaví řádků a buňky záhlaví sloupce.  
  
> [!NOTE]
>  Barva čar mřížky se používá jenom s <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single>, <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>, a <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> hodnoty <xref:System.Windows.Forms.DataGridViewCellBorderStyle> – výčet a <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> hodnotu <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> – výčet. Ostatní hodnoty těchto výčty pomocí barvy definované v operačním systému. Kromě toho, když jsou vizuální styly povoleno na systémy Windows XP a řady Windows Server 2003 prostřednictvím <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody <xref:System.Windows.Forms.DataGridView.GridColor%2A> nepoužívá hodnotu vlastnosti.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Chcete-li změnit barvu čar mřížky prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.GridColor%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Chcete-li změnit styl ohraničení celý ovládací prvek DataGridView prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.BorderStyle%2A> vlastnost na jednu z <xref:System.Windows.Forms.BorderStyle> hodnot výčtu.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Chcete-li změnit styl buněk DataGridView prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>, a <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> vlastnosti.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, a <xref:System.Drawing?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.BorderStyle>  
 <xref:System.Windows.Forms.DataGridView.BorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.GridColor%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewCellBorderStyle>  
 <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle>  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
