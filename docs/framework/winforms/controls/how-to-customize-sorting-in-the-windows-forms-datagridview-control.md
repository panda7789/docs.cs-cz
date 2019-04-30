---
title: 'Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- sorting [Windows Forms], DataGridView control
- DataGridView control [Windows Forms], sorting
- data grids [Windows Forms], customizing sorting
ms.assetid: 92fb5c14-afab-4cf5-a97e-924fd9cb99f5
ms.openlocfilehash: 0e7dffa45dc8d3ac467129d44a7c73a8c4b4bfa2
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61904329"
---
# <a name="how-to-customize-sorting-in-the-windows-forms-datagridview-control"></a>Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Řízení poskytuje automatické řazení, ale v závislosti na potřebách, možná budete muset přizpůsobit operace řazení. Například můžete řazení prostřednictvím kódu programu vytvořit alternativní uživatelské rozhraní (UI). Alternativně můžete zpracovávat <xref:System.Windows.Forms.DataGridView.SortCompare> události nebo volání `Sort(IComparer)` přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metodu pro vyšší flexibilitu řazení, jako je například řazení více sloupců.  
  
 Následující příklady kódu ukazují tyto tři přístupy k vlastní řazení. Další informace najdete v tématu [režimy třídění sloupce v ovládacím prvku Windows Forms DataGridView](column-sort-modes-in-the-windows-forms-datagridview-control.md).  
  
## <a name="programmatic-sorting"></a>Řazení prostřednictvím kódu programu  
 Následující příklad kódu ukazuje programová řazení pomocí <xref:System.Windows.Forms.DataGridView.SortOrder%2A> a <xref:System.Windows.Forms.DataGridView.SortedColumn%2A> vlastnosti k určení směru řazení a <xref:System.Windows.Forms.DataGridViewColumnHeaderCell.SortGlyphDirection%2A> vlastnost piktogram setřídit nastavit ručně. `Sort(DataGridViewColumn,ListSortDirection)` Přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda se používá k řazení dat pouze na jeden sloupec.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewProgrammaticSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewProgrammaticSort/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-sortcompare-event"></a>Vlastní řazení pomocí SortCompare události  
 Následující příklad kódu ukazuje vlastní řazení pomocí <xref:System.Windows.Forms.DataGridView.SortCompare> obslužné rutiny události. Vybrané <xref:System.Windows.Forms.DataGridViewColumn> je seřazený a, pokud existují duplicitní hodnoty ve sloupci, ID sloupce se používá k určení konečnou verzi objednávky.  
  
 [!code-csharp[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView.SortCompare#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView.SortCompare/VB/form1.vb#00)]  
  
## <a name="custom-sorting-using-the-icomparer-interface"></a>Vlastní řazení pomocí rozhraní IComparer  
 Následující příklad kódu ukazuje vlastní řazení pomocí `Sort(IComparer)` přetížení <xref:System.Windows.Forms.DataGridView.Sort%2A> metodu, která přebírá implementaci <xref:System.Collections.IComparer> rozhraní k provedení řazení více sloupců.  
  
 [!code-csharp[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/CS/form1.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewIComparerSort#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewIComparerSort/VB/form1.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tyto příklady vyžadují:  
  
- Odkazy na sestavení systému, System.Drawing a System.Windows.Forms.  
  
 Informace o vytváření těchto příkladech z příkazového řádku pro Visual Basic nebo Visual C# najdete v tématu [sestavení z příkazového řádku](../../../visual-basic/reference/command-line-compiler/building-from-the-command-line.md) nebo [sestavení pomocí příkazového řádku csc.exe](../../../csharp/language-reference/compiler-options/command-line-building-with-csc-exe.md). Tento příklad v sadě Visual Studio můžete také vytvořit vložením kódu do nového projektu.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Řazení dat v ovládacím prvku Windows Forms DataGridView](sorting-data-in-the-windows-forms-datagridview-control.md)
- [Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView](column-sort-modes-in-the-windows-forms-datagridview-control.md)
- [Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView](set-the-sort-modes-for-columns-wf-datagridview-control.md)
