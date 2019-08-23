---
title: 'Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
ms.openlocfilehash: d113c45469f6a78c94b9489bd82f9e55b5b96bba
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962274"
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView
Tabulková data se často prezentují uživatelům ve formátu, ve kterém mají střídavé řádky různé barvy na pozadí. Tento formát usnadňuje uživatelům informace o tom, které buňky jsou v jednotlivých řádcích, zejména u rozsáhlých tabulek, které mají mnoho sloupců.  
  
 <xref:System.Windows.Forms.DataGridView> Pomocí ovládacího prvku můžete zadat úplné informace o stylu pro střídavé řádky. To umožňuje použít charakteristiky stylu jako barvu popředí a písmo, kromě barvy pozadí pro odlišení střídajících se řádků.  
  
 Pro tuto úlohu se v aplikaci Visual Studio podporuje.  Podívejte [se také na postupy: Pomocí návrháře](set-alternating-row-styles-for-the-datagrid-using-the-designer.md)nastavte střídavé styly řádků pro ovládací prvek DataGridView model Windows Forms.  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Nastavení střídavých stylů řádků prostřednictvím kódu programu  
  
- Nastavte vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> objektů vrácených <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnostmi<xref:System.Windows.Forms.DataGridView>a.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    > Styly určené pomocí <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> vlastností a <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> přepíšou styly zadané na sloupci a <xref:System.Windows.Forms.DataGridView> úrovni, ale jsou přepsány styly nastavenými na úrovni jednotlivých řádků a buněk. Další informace naleznete v tématu [styly buněk v ovládacím prvku DataGridView model Windows Forms](cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Ovládací prvek s `dataGridView1`názvem. <xref:System.Windows.Forms.DataGridView>  
  
- Odkazy na <xref:System?displayProperty=nameWithType>sestavení, <xref:System.Drawing?displayProperty=nameWithType>a. <xref:System.Windows.Forms?displayProperty=nameWithType>  
  
## <a name="robust-programming"></a>Robustní programování  
 Pro zajištění maximální škálovatelnosti byste měli sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objekty napříč více řádky, sloupci nebo buňkami, které používají stejné styly, nikoli nastavovat vlastnosti stylu pro každý prvek samostatně. Další informace najdete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewCellStyle>
- [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)
- [Styly buňky v ovládacím prvku Windows Forms DataGridView](cell-styles-in-the-windows-forms-datagridview-control.md)
- [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](best-practices-for-scaling-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení stylů písma a barev v ovládacím prvku DataGridView model Windows Forms](how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
