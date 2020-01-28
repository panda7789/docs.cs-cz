---
title: Nastavit sloupce jen pro čtení v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: 11d008d47ec5edb594d3d862c68ff3b9920e0e25
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736181"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a>Postupy: Přepnutí sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView
Ne všechna data jsou určena pro úpravy. V ovládacím prvku <xref:System.Windows.Forms.DataGridView> vlastnost <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> sloupce určuje, zda uživatelé mohou upravovat buňky v tomto sloupci. Informace o tom, jak nastavit ovládací prvek jen pro čtení, naleznete [v tématu How to: prevence a Dissčítání řádků v ovládacím prvku DataGridView model Windows Forms](prevent-row-addition-and-deletion-datagridview.md).  
  
 Pro tuto úlohu se v aplikaci Visual Studio podporuje.  Přečtěte si také téma [How to: zpřístupnit sloupce jen pro čtení v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](make-columns-read-only-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-make-a-column-read-only-programmatically"></a>Zpřístupnění sloupce pouze pro čtení prostřednictvím kódu programu  
  
- Nastavte <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` se sloupcem s názvem `CompanyName`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView](prevent-row-addition-and-deletion-datagridview.md)
