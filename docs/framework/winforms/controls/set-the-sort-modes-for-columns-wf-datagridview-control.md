---
title: Nastavení režimů řazení pro sloupce v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: 45ee1e7d82f826cddbd3492fed0f63e7a9c2cf1d
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742995"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Nastavení režimů třídění pro sloupce v ovládacím prvku Windows Forms DataGridView
V ovládacím prvku <xref:System.Windows.Forms.DataGridView> sloupce textového pole používají automatické řazení ve výchozím nastavení, zatímco jiné typy sloupců se neřadí automaticky. Někdy budete chtít přepsat tato výchozí nastavení. Například můžete zobrazit obrázky místo textu, čísel nebo hodnot buněk výčtu. I když obrázky nelze seřadit, lze seřadit základní hodnoty, které představují.  
  
 V ovládacím prvku <xref:System.Windows.Forms.DataGridView> určuje hodnota vlastnosti <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> sloupce jeho chování při řazení.  
  
 Následující postup ukazuje sloupec `Priority` z tématu [Postupy: Přizpůsobení formátování dat v ovládacím prvku DataGridView model Windows Forms](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Tento sloupec je sloupcem obrázku a ve výchozím nastavení není standardně zařadit. Obsahuje skutečné hodnoty buňky, které jsou řetězce, ale lze je seřadit automaticky.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Nastavení režimu řazení pro sloupec  
  
- Nastavte vlastnost <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`, který obsahuje sloupec s názvem `Priority`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Řazení dat v ovládacím prvku Windows Forms DataGridView](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
