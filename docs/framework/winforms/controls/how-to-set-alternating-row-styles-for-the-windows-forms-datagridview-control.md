---
title: "Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], row styles
- data grids [Windows Forms], row styles
- rows [Windows Forms], data grids
ms.assetid: 699ef759-458c-426d-ac87-7c7e71b018ae
caps.latest.revision: "14"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c6e6b8938bfb2595f80ee71146d1de817cc9bcfd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control"></a>Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView
Tabulková data se často zobrazí uživatelům ve formátu, účetní knihy, kde střídavých řádků mají různých barev pozadí. Tento formát usnadňuje uživatelům říct buněk, které jsou v jednotlivých řádcích, zejména s wide tabulky, které mají mnoho sloupců.  
  
 Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete zadat informace o dokončení stylu střídavých řádků. Díky této může použít vlastnosti stylu jako barvu popředí a písma, kromě barvu pozadí k odlišení střídavých řádků.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [postupy: nastavení střídavých řádků styly Windows Forms DataGridView – ovládací prvek s využitím návrháře](http://msdn.microsoft.com/library/3z9sk148\(v=vs.110\)).  
  
### <a name="to-set-alternating-row-styles-programmatically"></a>Nastavení stylů střídavých řádků prostřednictvím kódu programu  
  
-   Nastavit vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> objektů vrácený <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnosti <xref:System.Windows.Forms.DataGridView>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#068)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#068](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#068)]  
  
    > [!NOTE]
    >  Styly definované, pomocí <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A> a <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A> vlastnosti přepsání styly definované ve sloupci a <xref:System.Windows.Forms.DataGridView> úrovni, ale jsou přepsány styly nastavit na úrovni jednotlivých řádku a buňky. Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="robust-programming"></a>Robustní programování  
 Pro maximální škálovatelnost, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádků, sloupců nebo buněk, které používají stejné styly, nikoli nastavení vlastnosti stylu pro každý prvek samostatně. Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView.AlternatingRowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.RowsDefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Postupy: Nastavení písma a barevných stylů v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-font-and-color-styles-in-the-windows-forms-datagridview-control.md)
