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
ms.openlocfilehash: 6eb6fab4b147365221ba79a682c4eaf744d24b25
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView
Když uživatelé zobrazit data zobrazená v systému Windows Forms <xref:System.Windows.Forms.DataGridView> ovládací prvek, někdy potřebují k odkazování na jeden sloupec nebo sadu sloupců často. Například při zobrazení tabulku informace o zákazníkovi, který obsahuje mnoho sloupců, je vhodné zobrazované jméno zákazníka za všech okolností při povolování ostatních sloupců posun mimo oblast viditelné.  
  
 K dosažení toto chování, můžete zmrazení sloupců v ovládacím prvku. Po ukotvení sloupec se všechny sloupce na levé straně, (nebo záhlavím vpravo ve skriptech jazyk zprava doleva) jsou také pozastaveny. Ukotvené sloupce, takže zůstávají na svém místě, při lze posunout všech ostatních sloupců.  
  
> [!NOTE]
>  Pokud je povoleno změny pořadí sloupců, ukotvené sloupce jsou považovány za skupinu liší od neukotvené sloupce. Uživatelé mohou změnit umístění sloupce buď skupiny, ale sloupec nemůže přesunout z jedné skupiny na druhý.  
  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Vlastnost sloupce určuje, zda sloupec je vždy zobrazen v mřížce.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Informace v tématu [postupy: zablokování sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/717ss6s6\(v=vs.110\)).  
  
### <a name="to-freeze-a-column-programmatically"></a>Chcete-li ukotvit sloupec prostřednictvím kódu programu  
  
-   Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , který obsahuje sloupec s názvem `AddToCartButton`.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView>  
 [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
