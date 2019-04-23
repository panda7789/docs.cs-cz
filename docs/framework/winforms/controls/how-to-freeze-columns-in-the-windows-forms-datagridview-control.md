---
title: 'Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: a0b77a7356b09a5cc95ec165a62c45852f542b8a
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59187419"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView
Když uživatelé zobrazit data zobrazená ve Windows Forms <xref:System.Windows.Forms.DataGridView> ovládacího prvku, někdy potřebují často odkazovat na jeden sloupec nebo sadu sloupců. Například při zobrazení informací o zákaznících, který obsahuje mnoho sloupců tabulky, je užitečné zobrazit název zákazníka po celou dobu při povolení další sloupce mimo viditelná oblast.  
  
 K dosažení tohoto chování, lze ukotvit sloupce v ovládacím prvku. Po ukotvení sloupce jsou zmražená i všechny sloupce na levé straně (nebo vpravo v skripty jazyka zprava doleva). Zmrazené sloupce zůstanou na místě, zatímco všechny ostatní sloupce můžete posouvat.  
  
> [!NOTE]
>  Pokud je zapnutá změnu pořadí sloupců, zmrazené sloupce jsou považovány za skupiny, která se liší od nezmrazeném sloupci. Uživatelům můžete přemístit sloupce v jedné skupině, ale sloupce z jedné skupiny nemůže přesunout do jiné.  
  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Vlastnost sloupec určuje, zda sloupec je vždy zobrazen v mřížce.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [jak: Zablokování sloupců v Windows Forms DataGridView pomocí návrháře](freeze-columns-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-freeze-a-column-programmatically"></a>Chcete-li ukotvit sloupec prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , která obsahuje sloupec s názvem `AddToCartButton`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
