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
ms.openlocfilehash: ebeca5f933eac4da2bf3d4f300866fd2ff52b32a
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69917676"
---
# <a name="how-to-change-the-border-and-gridline-styles-in-the-windows-forms-datagridview-control"></a>Postupy: Změna stylů ohraničení a mřížky v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Pomocí ovládacího prvku můžete přizpůsobit vzhled ohraničení a mřížky ovládacího prvku pro zlepšení uživatelského prostředí. Kromě stylů ohraničení buněk v ovládacím prvku můžete měnit barvu mřížky a styl ohraničení ovládacího prvku. Pro obyčejné buňky, buňky záhlaví řádku a buňky záhlaví sloupce můžete také použít jiné styly ohraničení buňky.  
  
> [!NOTE]
> Barva mřížky se používá pouze s <xref:System.Windows.Forms.DataGridViewCellBorderStyle.Single> <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleVertical> hodnotami <xref:System.Windows.Forms.DataGridViewCellBorderStyle> , <xref:System.Windows.Forms.DataGridViewCellBorderStyle.SingleHorizontal>a výčtů a <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle.Single> hodnotou <xref:System.Windows.Forms.DataGridViewHeaderBorderStyle> výčtu. Ostatní hodnoty těchto výčtů používají barvy určené operačním systémem. Kromě toho, pokud jsou vizuální styly povoleny v systému Windows XP a řada Windows Server 2003 pomocí <xref:System.Windows.Forms.Application.EnableVisualStyles%2A?displayProperty=nameWithType> metody <xref:System.Windows.Forms.DataGridView.GridColor%2A> , není použita hodnota vlastnosti.  
  
### <a name="to-change-the-gridline-color-programmatically"></a>Chcete-li změnit barvu mřížky programově  
  
- <xref:System.Windows.Forms.DataGridView.GridColor%2A> Nastavte vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#031)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#031](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#031)]  
  
### <a name="to-change-the-border-style-of-the-entire-datagridview-control-programmatically"></a>Změna stylu ohraničení celého ovládacího prvku DataGridView prostřednictvím kódu programu  
  
- Nastavte vlastnost na jednu z hodnot <xref:System.Windows.Forms.BorderStyle> výčtu. <xref:System.Windows.Forms.DataGridView.BorderStyle%2A>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#032)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#032](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#032)]  
  
### <a name="to-change-the-border-styles-for-datagridview-cells-programmatically"></a>Chcete-li změnit styly ohraničení pro buňky DataGridView programově  
  
- Nastavte vlastnosti <xref:System.Windows.Forms.DataGridView.CellBorderStyle%2A>, <xref:System.Windows.Forms.DataGridView.RowHeadersBorderStyle%2A>a <xref:System.Windows.Forms.DataGridView.ColumnHeadersBorderStyle%2A> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#033)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#033](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#033)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#030)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#030](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#030)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Ovládací prvek s `dataGridView1`názvem. <xref:System.Windows.Forms.DataGridView>  
  
- Odkazy na <xref:System?displayProperty=nameWithType>sestavení, <xref:System.Windows.Forms?displayProperty=nameWithType>a. <xref:System.Drawing?displayProperty=nameWithType>  
  
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
