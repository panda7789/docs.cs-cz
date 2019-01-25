---
title: 'Postupy: Skrytí záhlaví sloupců v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], hiding column headers
- column headers [Windows Forms], hiding
- DataGridView control [Windows Forms], column headers
ms.assetid: e4ad5f68-50d2-4b9e-93ee-9d622423a8ab
ms.openlocfilehash: 80377aa598938031f9708c4b7657594985ec0746
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54717061"
---
# <a name="how-to-hide-column-headers-in-the-windows-forms-datagridview-control"></a>Postupy: Skrytí záhlaví sloupců v ovládacím prvku Windows Forms DataGridView
Někdy budete chtít zobrazit <xref:System.Windows.Forms.DataGridView> bez záhlaví sloupců. V <xref:System.Windows.Forms.DataGridView> ovládací prvek, <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A> vlastnost hodnota určuje, zda jsou zobrazena záhlaví sloupců.  
  
### <a name="to-hide-the-column-headers"></a>Skrytí záhlaví sloupců  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType> vlastnost `false`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#062)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#062](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#062)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.ColumnHeadersVisible%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
