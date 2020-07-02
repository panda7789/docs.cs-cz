---
title: Získání a nastavení aktuální buňky v ovládacím prvku DataGridView
description: Naučte se programově zjistit, která buňka je aktuálně aktivní, získáním a nastavením aktuální buňky v ovládacím prvku DataGridView model Windows Forms.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 1651ca9c8fa0329f9435a70ce777bce68f15ff63
ms.sourcegitcommit: e02d17b2cf9c1258dadda4810a5e6072a0089aee
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 07/01/2020
ms.locfileid: "85622208"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView
Interakce s <xref:System.Windows.Forms.DataGridView> často vyžaduje, abyste programově zjistili, která buňka je aktuálně aktivní. Je také možné, že budete muset změnit aktuální buňku. Tyto úlohy můžete provádět s <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastností.  
  
> [!NOTE]
> Nemůžete nastavit aktuální buňku v řádku nebo sloupci, kde má <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> vlastnost nastavenou na `false` .  
  
 V závislosti na <xref:System.Windows.Forms.DataGridView> režimu výběru ovládacího prvku může změna aktuální buňky změnit výběr. Další informace naleznete v tématu [režimy výběru v ovládacím prvku DataGridView model Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Získání aktuální buňky prostřednictvím kódu programu  
  
- Použijte <xref:System.Windows.Forms.DataGridView> vlastnost ovládacího prvku <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> .  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Chcete-li nastavit aktuální buňku programově  
  
- Nastavte <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost <xref:System.Windows.Forms.DataGridView> ovládacího prvku. V následujícím příkladu kódu je aktuální buňka nastavena na řádek 0, sloupec 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.Button>ovládací prvky s názvem `getCurrentCellButton` a `setCurrentCellButton` . V jazyce Visual C# je nutné připojit <xref:System.Windows.Forms.Control.Click> události pro každé tlačítko k přidružené obslužné rutině události v příkladu kódu.  
  
- <xref:System.Windows.Forms.DataGridView>Ovládací prvek s názvem `dataGridView1` .  
  
- Odkazy na <xref:System?displayProperty=nameWithType> sestavení a <xref:System.Windows.Forms?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Režimy výběru v ovládacím prvku Windows Forms DataGridView](selection-modes-in-the-windows-forms-datagridview-control.md)
