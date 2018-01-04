---
title: "Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView"
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
- DataGridView control [Windows Forms], cell styles
- cells [Windows Forms], styles
- data grids [Windows Forms], cell styles
ms.assetid: 1aaaca43-5340-447e-99c0-9177d9776aa1
caps.latest.revision: "17"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: c817f62ede780ad0164ef78156b1a028e0c7a0a6
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-set-default-cell-styles-for-the-windows-forms-datagridview-control"></a>Postupy: Nastavení výchozích stylů buňky pro ovládací prvek Windows Forms DataGridView
Pomocí <xref:System.Windows.Forms.DataGridView> ovládací prvek, můžete zadat výchozích stylů buňky pro celý ovládací prvek a pro určité sloupce a řádky. Tyto výchozí hodnoty filtrovat dolů z úrovně řízení na úrovni sloupce, pak úroveň řádek, dále na úrovni buněk. Pokud určitý <xref:System.Windows.Forms.DataGridViewCellStyle> na úrovni buněk není nastavena vlastnost, bude použita výchozí nastavení vlastnosti na úrovni řádků. Pokud také není vlastnost nastavena na úrovni řádků, použije se výchozí nastavení sloupce. Nakonec pokud není vlastnost také nastavena na úrovni sloupce, výchozí <xref:System.Windows.Forms.DataGridView> nastavení se používá. Při tomto nastavení se můžete vyhnout nutnosti mít duplicitní hodnoty vlastností na více úrovních. Na každé úrovni jednoduše zadejte stylů, které se liší od úrovně nad ním. Další informace najdete v tématu [styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md).  
  
 Rozsáhlá podpora pro tuto úlohu v sadě Visual Studio není k dispozici.  Viz také [postup: nastavte výchozí styly buňky a Data formátů Windows Forms DataGridView – ovládací prvek s využitím návrháře](http://msdn.microsoft.com/library/95y5fz2x\(v=vs.110\)).  
  
### <a name="to-set-the-default-cell-styles-programmatically"></a>Nastavení výchozích stylů buňky prostřednictvím kódu programu  
  
1.  Nastavit vlastnosti <xref:System.Windows.Forms.DataGridViewCellStyle> načteny prostřednictvím <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#141)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#141](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#141)]  
  
2.  Vytvoření a inicializace nové <xref:System.Windows.Forms.DataGridViewCellStyle> objekty za účelem použití více řádků a sloupců.  
  
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
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Drawing?displayProperty=nameWithType>, a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="robust-programming"></a>Robustní programování  
 K dosažení maximální škálovatelnost při práci s velmi velkých datových sad, by měly sdílet <xref:System.Windows.Forms.DataGridViewCellStyle> objektů mezi více řádků, sloupců nebo buněk, které použít stejné styly, nikoli samostatně nastavte vlastnosti stylu pro jednotlivé elementy. Kromě toho by měl vytvořit sdílené řádky a přistupovat k nim pomocí <xref:System.Windows.Forms.DataGridViewRowCollection.SharedRow%2A?displayProperty=nameWithType> vlastnost. Další informace najdete v tématu [osvědčené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewCellStyle>  
 <xref:System.Windows.Forms.DataGridView.DefaultCellStyle%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewBand.DefaultCellStyle%2A?displayProperty=nameWithType>  
 [Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 [Styly buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/cell-styles-in-the-windows-forms-datagridview-control.md)  
 [Doporučené postupy pro změnu velikosti ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/best-practices-for-scaling-the-windows-forms-datagridview-control.md)  
 [Postupy: Nastavení střídavých stylů řádků pro ovládací prvek Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-set-alternating-row-styles-for-the-windows-forms-datagridview-control.md)
