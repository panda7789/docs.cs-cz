---
title: Povolit změnu pořadí sloupců v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], reordering columns
- columns [Windows Forms], reordering
ms.assetid: cc20eae3-e4db-493f-95ce-a4215e29472a
ms.openlocfilehash: 681489cdb874677079e2577140040921e587d21e
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76745493"
---
# <a name="how-to-enable-column-reordering-in-the-windows-forms-datagridview-control"></a>Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView
Pokud povolíte změnu pořadí sloupců v ovládacím prvku <xref:System.Windows.Forms.DataGridView>, uživatelé mohou přesunout sloupec na novou pozici přetažením záhlaví sloupce pomocí myši. V ovládacím prvku <xref:System.Windows.Forms.DataGridView> určuje <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> hodnota vlastnosti, zda uživatelé mohou přesouvat sloupce na jiné pozice.  
  
 Pro tuto úlohu se v aplikaci Visual Studio podporuje.  Také se [naučíte: Povolit změnu pořadí sloupců v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](enable-column-reordering-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-enable-column-reordering-programmatically"></a>Chcete-li povolit změnu pořadí sloupců pomocí kódu programu  
  
- Nastavte <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#060)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#060](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#060)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToOrderColumns%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)
