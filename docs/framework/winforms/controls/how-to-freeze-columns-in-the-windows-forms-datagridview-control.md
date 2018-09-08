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
ms.openlocfilehash: df8ac7e7db74d4e8df8872b5ec7f8f2ec774b3c8
ms.sourcegitcommit: c7f3e2e9d6ead6cc3acd0d66b10a251d0c66e59d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/08/2018
ms.locfileid: "44183402"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView
Když uživatelé zobrazit data zobrazená ve Windows Forms <xref:System.Windows.Forms.DataGridView> ovládacího prvku, někdy potřebují často odkazovat na jeden sloupec nebo sadu sloupců. Například při zobrazení informací o zákaznících, který obsahuje mnoho sloupců tabulky, je užitečné zobrazit název zákazníka po celou dobu při povolení další sloupce mimo viditelná oblast.  
  
 K dosažení tohoto chování, lze ukotvit sloupce v ovládacím prvku. Po ukotvení sloupce jsou zmražená i všechny sloupce na levé straně (nebo vpravo v skripty jazyka zprava doleva). Zmrazené sloupce zůstanou na místě, zatímco všechny ostatní sloupce můžete posouvat.  
  
> [!NOTE]
>  Pokud je zapnutá změnu pořadí sloupců, zmrazené sloupce jsou považovány za skupiny, která se liší od nezmrazeném sloupci. Uživatelům můžete přemístit sloupce v jedné skupině, ale sloupce z jedné skupiny nemůže přesunout do jiné.  
  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Vlastnost sloupec určuje, zda sloupec je vždy zobrazen v mřížce.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [postupy: zablokování sloupců v Windows Forms DataGridView ovládacího prvku pomocí návrháře](https://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).  
  
### <a name="to-freeze-a-column-programmatically"></a>Chcete-li ukotvit sloupec prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , která obsahuje sloupec s názvem `AddToCartButton`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
