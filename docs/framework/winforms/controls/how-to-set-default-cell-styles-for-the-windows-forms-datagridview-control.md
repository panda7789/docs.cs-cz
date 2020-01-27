---
title: Nastavení výchozích stylů buňky pro ovládací prvek DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 6b2d7de671e48ae8f55987c262e15717138b3fb4
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76744865"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView
Pomocí ovládacího prvku <xref:System.Windows.Forms.DataGridView> můžete určit výchozí styly buněk pro celý ovládací prvek a pro konkrétní sloupce a řádky. Tyto výchozí hodnoty se filtrují z úrovně ovládacího prvku na úroveň sloupce a pak na úroveň řádku a na úroveň buňky. Pokud není nastavená určitá vlastnost <xref:System.Windows.Forms.DataGridViewCellStyle> na úrovni buňky, použije se výchozí nastavení vlastnosti na úrovni řádku. Pokud vlastnost není nastavena i na úrovni řádku, použije se výchozí nastavení sloupce. Nakonec, pokud vlastnost není nastavena také na úrovni sloupce, je použita výchozí hodnota <xref:System.Windows.Forms.DataGridView>. Pomocí tohoto nastavení můžete zabránit duplikaci nastavení vlastností na více úrovních. Na každé úrovni jednoduše určete styly, které se liší od úrovní nad ní. Další informace naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Existuje Rozsáhlá podpora pro tento úkol v aplikaci Visual Studio.  Viz také [Postupy: nastavení výchozích stylů buňky a datových formátů pro ovládací prvek DataGridView model Windows Forms pomocí návrháře](default-cell-styles-datagridview.md).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Chcete-li nastavit výchozí styly buněk programově  
  
1. Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> načtené prostřednictvím vlastnosti <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2. Umožňuje vytvořit a inicializovat nové objekty <xref:System.Windows.Forms.DataGridViewCellStyle> pro použití více řádků a sloupců.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3. Nastavte vlastnost `DefaultCellStyle` pro určité řádky a sloupce.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>a <xref:System.Windows.Forms?displayProperty=nameWithType>.  
  
## <a name="robust-programming"></a>Robustní programování  
 Chcete-li dosáhnout maximální škálovatelnosti při práci s velmi velkými datovými sadami, měli byste sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč více řádky, sloupci nebo buňkami, které používají stejné styly, nikoli nastavit vlastnosti stylu pro jednotlivé prvky samostatně. Kromě toho byste měli vytvořit sdílené řádky a přistupovat k nim pomocí vlastnosti <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType>. Další informace najdete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView](how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
