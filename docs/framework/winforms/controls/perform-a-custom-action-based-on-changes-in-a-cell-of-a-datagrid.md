---
title: 'Postupy: Provedení vlastní akce na základě změn v buňce ovládacího prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- cells [Windows Forms], detecting changes
- DataGridView control [Windows Forms], detecting changes in cells
- data grids [Windows Forms], detecting changes in cells
ms.assetid: 7fa44d01-97f4-4ccb-a149-bc72628d2c36
ms.openlocfilehash: 23753a2c0ceab9452bde24a1c56348eabf87d655
ms.sourcegitcommit: 2701302a99cafbe0d86d53d540eb0fa7e9b46b36
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/28/2019
ms.locfileid: "64654435"
---
# <a name="how-to-perform-a-custom-action-based-on-changes-in-a-cell-of-a-windows-forms-datagridview-control"></a>Postupy: Provedení vlastní akce na základě změn v buňce ovládacího prvku Windows Forms DataGridView
<xref:System.Windows.Forms.DataGridView> Ovládací prvek má několik událostí můžete použít k detekci změn stavu <xref:System.Windows.Forms.DataGridView> buňky. Dva z nejčastěji používané jsou <xref:System.Windows.Forms.DataGridView.CellValueChanged> a <xref:System.Windows.Forms.DataGridView.CellStateChanged> události.  
  
### <a name="to-detect-changes-in-the-values-of-datagridview-cells"></a>Ke zjištění změny hodnoty buněk DataGridView  
  
- Zápis obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellValueChanged> událostí.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#130)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#130](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#130)]  
  
### <a name="to-detect-changes-in-the-states-of-datagridview-cells"></a>Ke zjištění změny ve stavu buněk DataGridView  
  
- Zápis obslužné rutiny pro <xref:System.Windows.Forms.DataGridView.CellStateChanged> událostí.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#135)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#135](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#135)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`. Pro C#, obslužné rutiny událostí musí být připojený k odpovídající události.  
  
- Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CellValueChanged?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.CellStateChanged?displayProperty=nameWithType>
- [Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView](programming-with-cells-rows-and-columns-in-the-datagrid.md)
- [Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)
