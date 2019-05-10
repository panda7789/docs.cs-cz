---
title: 'Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], data grids
- DataGridView control [Windows Forms], sort mode
- data grids [Windows Forms], sorting data
ms.assetid: 57dfed60-a608-40d5-86f9-d65686ffb325
ms.openlocfilehash: fd627e3aaed7330a05c46b9e2ca0a213404e0bfe
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64625752"
---
# <a name="how-to-set-the-sort-modes-for-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView
V <xref:System.Windows.Forms.DataGridView> ovládací prvek textové pole sloupce použijte automatické řazení ve výchozím nastavení, zatímco jiné typy sloupců nejsou seřazené automaticky. Někdy budete chtít přepsat tyto výchozí hodnoty. Například můžete zobrazit obrázky místo hodnoty text, čísla nebo výčet buňky. Zatímco nemohou být řazeny obrázky, lze je řadit podkladové hodnoty, které představují.  
  
 V <xref:System.Windows.Forms.DataGridView> ovládací prvek, <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> hodnota vlastnosti sloupce určuje jeho chování řazení.  
  
 Následující postup ukazuje `Priority` sloupec z [jak: Přizpůsobení formátování dat v ovládacím prvku Windows Forms DataGridView](how-to-customize-data-formatting-in-the-windows-forms-datagridview-control.md). Tento sloupec je sloupec image a není ve výchozím nastavení řazení. Obsahuje hodnoty skutečné buněk, které jsou řetězce, ale tak lze seřadit automaticky.  
  
### <a name="to-set-the-sort-mode-for-a-column"></a>Chcete-li nastavit režim řazení pro sloupce  
  
- Nastavte <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#066)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#066](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#066)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , která obsahuje sloupec s názvem `Priority`.  
  
- Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>
- [Řazení dat v ovládacím prvku Windows Forms DataGridView](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)
