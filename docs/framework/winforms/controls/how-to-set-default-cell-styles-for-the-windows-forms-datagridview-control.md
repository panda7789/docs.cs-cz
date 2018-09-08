---
title: 'Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
ms.openlocfilehash: 072a9ce7e28983683ac1104b70c160cf5eea12b7
ms.sourcegitcommit: 64f4baed249341e5bf64d1385bf48e3f2e1a0211
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2018
ms.locfileid: "44130981"
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView
S <xref:System.Windows.Forms.DataGridView> ovládacího prvku, můžete zadat výchozích stylů buňky pro celý ovládací prvek a pro určité sloupce a řádky. Tyto výchozí hodnoty vyfiltrovat z úrovně ovládacího prvku na úrovni sloupce pak na úrovni řádků a pak na úrovni buněk. Pokud konkrétní <xref:System.Windows.Forms.DataGridViewCellStyle> vlastnost není nastavená na úrovni buňky, bude použito výchozí nastavení vlastnosti na úrovni řádků. Pokud není vlastnost také nastavit na úrovni řádků, sloupců ve výchozím nastavení se používá. Nakonec pokud není vlastnost také nastavit na úrovni sloupce, výchozí <xref:System.Windows.Forms.DataGridView> nastavení se používá. Při tomto nastavení se vyhnete nutnosti mít duplicitní nastavení vlastnosti na více úrovních. Na každé úrovni zadejte jednoduše styly, které se liší od úrovně nad ním. Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Není k dispozici rozsáhlou podporu pro tuto úlohu v sadě Visual Studio.  Viz také [jak: nastavit výchozí stylů buňky a Data formátů pro ovládací prvek DataGridView formuláře Windows ovládacího prvku pomocí návrháře](https://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Nastavení výchozích stylů buňky prostřednictvím kódu programu  
  
1.  Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> získat pomocí <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  Vytváření a inicializace nového <xref:System.Windows.Forms.DataGridViewCellStyle> objekty používají více řádků a sloupců.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#142)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#142](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#142)]  
  
3.  Nastavte `DefaultCellStyle` vlastnost konkrétní řádků a sloupců.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#143)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#143](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#143)]  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#140)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#140](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#140)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pro dosažení maximální škálovatelnosti při práci s velmi velkými datovými sadami, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádky, sloupce nebo buňky, které použijte stejné styly, nikoli samostatně nastavte vlastnosti stylu pro jednotlivé prvky. Kromě toho by měl vytvořit sdílené řádky a k nim přistupovat pomocí <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> vlastnost. Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
