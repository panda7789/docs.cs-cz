---
title: Nastavení stylů písma a barev v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell customization
- data grids [Windows Forms], customizing cells
- data grids [Windows Forms], font styles
- data grids [Windows Forms], color styles
ms.assetid: 588f2c57-d963-41b1-9c1d-d02d71818113
ms.openlocfilehash: f1ee9131cfc0b28a5f6263dcd6254d27a092cc62
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746755"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a>Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView
Můžete určit vizuální vzhled buněk v ovládacím prvku <xref:System.Windows.Forms.DataGridView> nastavením vlastností <xref:System.Windows.Forms.DataGridViewCellStyle> třídy. Můžete načíst instance této třídy z různých vlastností třídy <xref:System.Windows.Forms.DataGridView> a jejích doprovodných tříd, nebo můžete vytvořit instanci <xref:System.Windows.Forms.DataGridViewCellStyle> objektů pro přiřazení k těmto vlastnostem.  
  
 Následující postupy ukazují základní přizpůsobení vzhledu buňky pomocí vlastnosti <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A>. Každá buňka v ovládacím prvku dědí styly zadané přes tuto vlastnost, pokud nejsou přepsány na úrovni sloupce, řádku nebo buňky. Příklad dědičnosti stylu naleznete v tématu [How to: set pro výchozí styly buněk pro ovládací prvek DataGridView model Windows Forms](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Informace o dalších použitích třídy <xref:System.Windows.Forms.DataGridViewCellStyle> naleznete v tématech uvedených v části Viz také.  
  
 Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.  Viz také [Postupy: nastavení výchozích stylů buňky a datových formátů pro ovládací prvek DataGridView model Windows Forms pomocí návrháře](default-cell-styles-datagridview.md).  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a>Určení písma používaného buňkami DataGridView  
  
- Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>. Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> k nastavení písma pro celý ovládací prvek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a>Určení barvy popředí a pozadí buněk DataGridView  
  
- Nastavení vlastností <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>. Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> k nastavení těchto stylů pro celý ovládací prvek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a>Chcete-li určit barvy popředí a pozadí vybraných buněk DataGridView  
  
- Nastavení vlastností <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> <xref:System.Windows.Forms.DataGridViewCellStyle>. Následující příklad kódu používá vlastnost <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> k nastavení těchto stylů pro celý ovládací prvek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>a <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pro zajištění maximální škálovatelnosti byste měli sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč více řádky, sloupci nebo buňkami, které používají stejné styly, nikoli nastavovat vlastnosti stylu pro každý prvek samostatně. Další informace najdete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
