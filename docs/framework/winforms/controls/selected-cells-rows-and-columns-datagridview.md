---
title: Získání vybraných buněk, řádků a sloupců v ovládacím prvku DataGridView
description: Naučte se, jak získat vybrané buňky, řádky nebo sloupce z ovládacího prvku DataGridView pomocí odpovídajících vlastností.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- selection [Windows Forms], DataGridView control [Windows Forms]
- DataGridView control [Windows Forms], getting selection
- getting selection [Windows Forms], DataGridView control [Windows Forms]
ms.assetid: d93c4b5b-498e-49bc-982a-2229d61778e4
ms.openlocfilehash: 32ddae34104d23b8e5fbc0cce7da79f33fcce1d2
ms.sourcegitcommit: 3824ff187947572b274b9715b60c11269335c181
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/17/2020
ms.locfileid: "84904166"
---
# <a name="how-to-get-the-selected-cells-rows-and-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Získání vybraných buněk, řádků a sloupců v ovládacím prvku Windows Forms DataGridView
Vybrané buňky, řádky nebo sloupce můžete získat z <xref:System.Windows.Forms.DataGridView> ovládacího prvku pomocí odpovídajících vlastností: <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> , <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> a <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> . V následujících postupech zobrazíte vybrané buňky a zobrazíte jejich indexy řádků a sloupců v <xref:System.Windows.Forms.MessageBox> .  
  
### <a name="to-get-the-selected-cells-in-a-datagridview-control"></a>Získání vybraných buněk v ovládacím prvku DataGridView  
  
- Použijte <xref:System.Windows.Forms.DataGridView.SelectedCells%2A> vlastnost.  
  
    > [!NOTE]
    > Použijte <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A> metodu k zamezení zobrazení potenciálně velkého počtu buněk.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#10)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#10](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#10)]  
  
### <a name="to-get-the-selected-rows-in-a-datagridview-control"></a>Získání vybraných řádků v ovládacím prvku DataGridView  
  
- Použijte <xref:System.Windows.Forms.DataGridView.SelectedRows%2A> vlastnost. Chcete-li uživatelům umožnit výběr řádků, je nutné nastavit <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> vlastnost na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullRowSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.RowHeaderSelect> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#20)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#20](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#20)]  
  
### <a name="to-get-the-selected-columns-in-a-datagridview-control"></a>Získání vybraných sloupců v ovládacím prvku DataGridView  
  
- Použijte <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A> vlastnost. Chcete-li uživatelům umožnit výběr sloupců, je nutné nastavit <xref:System.Windows.Forms.DataGridView.SelectionMode%2A> vlastnost na <xref:System.Windows.Forms.DataGridViewSelectionMode.FullColumnSelect> nebo <xref:System.Windows.Forms.DataGridViewSelectionMode.ColumnHeaderSelect> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/CS/DataGridViewSelectedCollections.cs#30)]
     [!code-vb[System.Windows.Forms.DataGridViewSelectedCollections#30](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSelectedCollections/VB/DataGridViewSelectedCollections.vb#30)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.Button>ovládací prvky s názvem `selectedCellsButton` , `selectedRowsButton` a `selectedColumnsButton` , každý s obslužnými rutinami pro <xref:System.Windows.Forms.Control.Click> připojenou událost.  
  
- <xref:System.Windows.Forms.DataGridView>Ovládací prvek s názvem `dataGridView1` .  
  
- Odkazy na <xref:System?displayProperty=nameWithType> sestavení, <xref:System.Windows.Forms?displayProperty=nameWithType> a <xref:System.Text?displayProperty=nameWithType> .  
  
## <a name="robust-programming"></a>Robustní programování  
 Kolekce popsané v tomto tématu neprovádějte efektivně, pokud je vybrán velký počet buněk, řádků nebo sloupců. Další informace o použití těchto kolekcí s velkým objemem dat naleznete v tématu [osvědčené postupy pro škálování ovládacího prvku DataGridView model Windows Forms](best-practices-for-scaling-the-windows-forms-datagridview-control.md).  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.SelectionMode%2A>
- <xref:System.Windows.Forms.DataGridView.AreAllCellsSelected%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedCells%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedRows%2A>
- <xref:System.Windows.Forms.DataGridView.SelectedColumns%2A>
- [Výběr a používání schránky s ovládacím prvkem Windows Forms DataGridView](selection-and-clipboard-use-with-the-windows-forms-datagridview-control.md)
