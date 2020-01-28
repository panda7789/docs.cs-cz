---
title: Přidání nevázaného sloupce do ovládacího prvku DataGridView vázaného na data
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], unbound data
- data grids [Windows Forms], adding unbound columns
- DataGridView control [Windows Forms], unbound data
ms.assetid: f7bdc4d8-ba8e-421b-ad62-82d936f01372
ms.openlocfilehash: 807bbc121f33c35d70068571e76637c078ecb3da
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76747061"
---
# <a name="how-to-add-an-unbound-column-to-a-data-bound-windows-forms-datagridview-control"></a>Postupy: Přidání nepřipojeného sloupce do daty připojeného ovládacího prvku Windows Forms DataGridView
Data, která zobrazíte v ovládacím prvku <xref:System.Windows.Forms.DataGridView>, budou normálně pocházet ze zdroje dat nějakého druhu, ale možná budete chtít zobrazit sloupec dat, která nepochází ze zdroje dat. Tento druh sloupce se nazývá nevázaný sloupec. Nevázané sloupce mohou mít mnoho forem. Často se používají k poskytnutí přístupu k podrobnostem datového řádku.  
  
 Následující příklad kódu ukazuje, jak vytvořit nevázaný sloupec tlačítek **podrobností** k zobrazení podřízené tabulky související s konkrétním řádkem v nadřazené tabulce při implementaci scénáře hlavní/podrobnosti. Chcete-li reagovat na kliknutí na tlačítko, Implementujte obslužnou rutinu události <xref:System.Windows.Forms.DataGridView.CellClick?displayProperty=nameWithType>, která zobrazí formulář obsahující podřízenou tabulku.  
  
 Pro tuto úlohu se v aplikaci Visual Studio podporuje.  Viz také [Postupy: Přidání a odebrání sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](add-and-remove-columns-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#010)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#010](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#010)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
