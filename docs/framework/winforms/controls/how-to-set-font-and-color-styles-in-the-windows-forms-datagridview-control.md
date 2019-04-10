---
title: 'Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView'
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
ms.openlocfilehash: 737a4b943125245a2916bbf6b24b8abdffa8e371
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59215338"
---
# <a name="how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control"></a>Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView
Můžete zadat vizuálního vzhledu buněk v rámci <xref:System.Windows.Forms.DataGridView> nastavením vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> třídy. Instance této třídy můžete načíst z různých vlastností <xref:System.Windows.Forms.DataGridView> třídy a jejich doprovodné třídy nebo můžete vytvořit instanci <xref:System.Windows.Forms.DataGridViewCellStyle> objekty pro přiřazení těchto vlastností.  
  
 Následující postupy ukazují základní přizpůsobení pomocí vzhledu buněk <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A> vlastnost. Všechny buňky v ovládacím prvku dědí zadaná pomocí tato vlastnost přepsána na úrovni buňky sloupce, řádku nebo styly. Příklad dědičnost stylů, najdete v části [jak: Nastavení výchozích stylů buňky pro Windows Forms DataGridView – ovládací prvek](how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control.md). Informace o další způsoby použití <xref:System.Windows.Forms.DataGridViewCellStyle> naleznete v tématech uvedených v části Viz také.  
  
 Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.  Viz také [jak: Nastavení výchozích stylů buňky a datových formátů pro Windows Forms DataGridView pomocí návrháře](default-cell-styles-datagridview.md).  
  
### <a name="to-specify-the-font-used-by-datagridview-cells"></a>Chcete-li určit písmo použité buněk DataGridView  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.Font%2A> vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle>. Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnosti chcete nastavit písmo pro celý ovládací prvek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#101)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#101](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#101)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-datagridview-cells"></a>K určení barvy popředí a pozadí buněk DataGridView  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.ForeColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.BackColor%2A> vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle>. Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnosti chcete nastavit tyto styly pro celý ovládací prvek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#102)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#102](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#102)]  
  
### <a name="to-specify-the-foreground-and-background-colors-of-selected-datagridview-cells"></a>K určení barvy popředí a pozadí vybraných buněk DataGridView  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionForeColor%2A> a <xref:System.Windows.Forms.DataGridViewCellStyle.SelectionBackColor%2A> vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle>. Následující příklad kódu používá <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnosti chcete nastavit tyto styly pro celý ovládací prvek.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#103)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#103](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#103)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#100)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#100](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#100)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pro maximální rozšiřitelnost, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádky, sloupce nebo buňky, které používají stejné styly, spíše než nastavení vlastnosti stylu pro každý prvek samostatně. Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
