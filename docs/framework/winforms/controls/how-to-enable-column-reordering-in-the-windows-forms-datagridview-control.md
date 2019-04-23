---
title: 'Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: 625c4987a45ed3749284e7abc7b6cde6d24821ca
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59161470"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView
Při povolení změny pořadí sloupců v <xref:System.Windows.Forms.DataGridView> řízení, mohou uživatelé přesouvat sloupec na nové pozici přetažením záhlaví sloupce myší. V <xref:System.Windows.Forms.DataGridView> ovládací prvek, <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> vlastnost hodnota určuje, zda mohou uživatelé přesouvat na jinou pozici sloupce.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [jak: Povolit změnu pořadí sloupců v Windows Forms DataGridView pomocí návrháře](enable-column-reordering-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-enable-column-reordering-programmatically"></a>Povolit sloupců, změna pořadí prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Ukotvit sloupce v ovládacím prvku Windows Forms DataGridView](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
