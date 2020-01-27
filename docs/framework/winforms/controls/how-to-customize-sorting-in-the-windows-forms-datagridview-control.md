---
title: Přizpůsobení řazení v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 20f581b2df6fd172a0a1998aed60c56b0306f2eb
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743176"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView
Ovládací prvek <xref:System.Windows.Forms.DataGridView> poskytuje automatické řazení, ale v závislosti na vašich potřebách možná budete muset přizpůsobit operace řazení. Programové řazení můžete například použít k vytvoření alternativního uživatelského rozhraní (UI). Alternativně můžete zpracovat událost <xref:System.Windows.Forms.DataGridView.SortCompare> nebo volat přetížení `Sort(IComparer)` metody <xref:System.Windows.Forms.DataGridView.Sort%2A> pro větší flexibilitu řazení, jako je například řazení více sloupců.  
  
 Následující příklady kódu ukazují tyto tři přístupy k vlastnímu řazení. Další informace naleznete v tématu [režimy řazení sloupců v ovládacím prvku DataGridView model Windows Forms](column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Programové řazení  
 Následující příklad kódu ukazuje programové řazení pomocí vlastností <xref:System.Windows.Forms.DataGridView.SortOrder%2A> a <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> k určení směru řazení a vlastnost <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> k ručnímu nastavení glyfu řazení. `Sort(DataGridViewColumn,ListSortDirection)` přetížení metody <xref:System.Windows.Forms.DataGridView.Sort%2A> slouží k řazení dat pouze do jednoho sloupce.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Vlastní řazení pomocí události SortCompare  
 Následující příklad kódu ukazuje vlastní řazení pomocí <xref:System.Windows.Forms.DataGridView.SortCompare> obslužné rutiny události. Vybraná <xref:System.Windows.Forms.DataGridViewColumn> je seřazená a pokud ve sloupci existují duplicitní hodnoty, použije se k určení konečného pořadí sloupec ID.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Vlastní řazení pomocí rozhraní IComparer  
 Následující příklad kódu ukazuje vlastní řazení pomocí `Sort(IComparer)` přetížení metody <xref:System.Windows.Forms.DataGridView.Sort%2A>, která přebírá implementaci rozhraní <xref:System.Collections.IComparer> k provedení řazení ve více sloupcích.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tyto příklady vyžadují:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Řazení dat v ovládacím prvku Windows Forms DataGridView](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView](set-the-sort-modes-for-columns-wf-datagridview-control.md)
