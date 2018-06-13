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
ms.openlocfilehash: 0a3c8a891bf3f8424158a7266c3752edc33e8805
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33527544"
---
# <a name="how-to-get-and-set-the-current-cell-in-the-windows-forms-datagridview-control"></a>Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView
Interakce se <xref:System.Windows.Forms.DataGridView> často vyžaduje prostřednictvím kódu programu zjistit buňku, která je aktuálně aktivní. Můžete také změnit aktuální buňky. Můžete provádět tyto úlohy se <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost.  
  
> [!NOTE]
>  Nelze nastavit aktuální buňky v řádku nebo sloupec, který má jeho <xref:System.Windows.Forms.DataGridViewBand.Visible%2A> vlastnost nastavena na hodnotu `false`.  
  
 V závislosti na tom <xref:System.Windows.Forms.DataGridView> režimu výběru ovládacího prvku, změna aktuální buňky můžete změnit výběr. Další informace najdete v tématu [režimy výběru v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md).  
  
### <a name="to-get-the-current-cell-programmatically"></a>Chcete-li získat aktuální buňky prostřednictvím kódu programu  
  
-   Použití <xref:System.Windows.Forms.DataGridView> ovládacího prvku <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#080)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#080](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#080)]  
  
### <a name="to-set-the-current-cell-programmatically"></a>K nastavení aktuální buňky prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridView.CurrentCell%2A> vlastnost <xref:System.Windows.Forms.DataGridView> ovládacího prvku. V následujícím příkladu kódu je nastavena aktuální buňky řádek 0, 1 sloupec.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#085)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#085](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#085)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   <xref:System.Windows.Forms.Button> ovládací prvky s názvem `getCurrentCellButton` a `setCurrentCellButton`. V jazyce Visual C#, musíte připojit <xref:System.Windows.Forms.Control.Click> události pro každé tlačítko obslužné rutině související události v ukázkovém kódu.  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.CurrentCell%2A?displayProperty=nameWithType>  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Režimy výběru v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/selection-modes-in-the-windows-forms-datagridview-control.md)
