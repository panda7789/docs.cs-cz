---
title: 'Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], getting current cell
- DataGridView control [Windows Forms], setting current cell
- cells [Windows Forms], getting and setting current
ms.assetid: b0e41e57-493a-4bd0-9376-a6f76723540c
ms.openlocfilehash: 670708f342e1cd1ac495c215b7508093349ac2e4
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69933703"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView
Interakce s <xref:System.Windows.Forms.DataGridView> často vyžaduje, abyste programově zjistili, která buňka je aktuálně aktivní. Je také možné, že budete muset změnit aktuální buňku. Tyto úlohy můžete provádět s <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastností.  
  
> [!NOTE]
> Nemůžete nastavit aktuální buňku v řádku nebo sloupci, kde má <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> vlastnost nastavenou na. `false`  
  
 V závislosti na <xref:System.Windows.Forms.DataGridView> režimu výběru ovládacího prvku může změna aktuální buňky změnit výběr. Další informace naleznete v tématu [režimy výběru v ovládacím prvku DataGridView model Windows Forms](selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Získání aktuální buňky prostřednictvím kódu programu  
  
- <xref:System.Windows.Forms.DataGridView> Použijte vlastnost<xref:System.Windows.Forms.DataGridView.CurrentCell%2A> ovládacího prvku.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>Chcete-li nastavit aktuální buňku programově  
  
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> Nastavte vlastnost <xref:System.Windows.Forms.DataGridView> ovládacího prvku. V následujícím příkladu kódu je aktuální buňka nastavena na řádek 0, sloupec 1.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.Button>ovládací prvky `getCurrentCellButton` s `setCurrentCellButton`názvem a. V jazyce C#Visual je nutné připojit <xref:System.Windows.Forms.Control.Click> události pro každé tlačítko k přidružené obslužné rutině události v příkladu kódu.  
  
- Ovládací prvek s `dataGridView1`názvem. <xref:System.Windows.Forms.DataGridView>  
  
- Odkazy na <xref:System?displayProperty=nameWithType> sestavení a <xref:System.Windows.Forms?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Režimy výběru v ovládacím prvku Windows Forms DataGridView](selection-modes-in-the-windows-forms-datagridview-control.md)
