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
ms.openlocfilehash: fbcafae2cb4e4cc320c31794269355d6312b95b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33532581"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView
Po povolení změny pořadí sloupců v <xref:System.Windows.Forms.DataGridView> řízení, mohou uživatelé přesouvat sloupce do nového umístění přetáhněte záhlaví sloupce pomocí myši. V <xref:System.Windows.Forms.DataGridView> ovládací prvek, <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> vlastnost hodnota určuje, zda mohou uživatelé přesouvat sloupce na jiné místo.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [postupy: povolení změny pořadí sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/8xwtyc86\(v=vs.110\))  
  
### <a name="to-enable-column-reordering-programmatically"></a>Chcete-li povolit sloupec změna prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
