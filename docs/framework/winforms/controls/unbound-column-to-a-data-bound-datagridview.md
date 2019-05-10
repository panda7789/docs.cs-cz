---
title: 'Postupy: Přidání nepřipojeného sloupce do ovládacího prvku Windows Forms DataGridView s datovou vazbou'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: d40eea54d908f17fc2fe893d5bc15a073a066ba1
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64651582"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Postupy: Přidání nepřipojeného sloupce do ovládacího prvku Windows Forms DataGridView s datovou vazbou
Data můžete zobrazit v <xref:System.Windows.Forms.DataGridView> ovládací prvek bude obvykle pocházejí ze zdroje dat určitého druhu, ale můžete chtít zobrazit sloupce dat, které nepochází ze zdroje dat. Tento typ sloupce se nazývá nepřipojeného sloupce. Nevázaného sloupce mohou mít mnoho forem. Často se používají k poskytnutí přístupu podrobné informace o datovém řádku.  
  
 Následující příklad kódu ukazuje, jak vytvořit nepřipojeného sloupce z **podrobnosti** tlačítka zobrazíte podřízené tabulky související s konkrétního řádku v nadřazené tabulce, Pokud implementujete scénář záznamů master/detail. Reakce na kliknutí na tlačítko, implementovat <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType> obslužná rutina události, které zobrazí formulář obsahující podřízené tabulky.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [jak: Přidat a odebrat sloupce v Windows Forms DataGridView pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
