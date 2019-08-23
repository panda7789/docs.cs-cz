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
ms.openlocfilehash: a83c5078d67be40fda2ae3382b8124594ee78103
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69966650"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView
Když uživatelé zobrazují data zobrazená v ovládacím <xref:System.Windows.Forms.DataGridView> prvku model Windows Forms, někdy potřebují často odkazovat na jeden sloupec nebo na sadu sloupců. Když například zobrazíte tabulku s informacemi o zákaznících, které obsahují mnoho sloupců, je vhodné zobrazit jméno zákazníka vždy, když se ostatní sloupce posouvají mimo viditelnou oblast.  
  
 Chcete-li dosáhnout tohoto chování, můžete ukotvit sloupce v ovládacím prvku. Při ukotvení sloupce jsou zmrazeny také všechny sloupce vlevo (nebo napravo ve skriptech se zápisem zprava doleva). Zmrazené sloupce zůstávají na místě, zatímco všechny ostatní sloupce se můžou posouvat.  
  
> [!NOTE]
> Pokud je povoleno přeřazení sloupce, jsou zmrazené sloupce považovány za skupinu odlišnou od nezmrazených sloupců. Uživatelé mohou přemístit sloupce v obou skupinách, ale nemohou přesunout sloupec z jedné skupiny do druhé.  
  
 <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> Vlastnost sloupce určuje, zda je sloupec v mřížce vždy zobrazen.  
  
 Pro tuto úlohu se v aplikaci Visual Studio podporuje.  Podívejte [se také na postupy: Ukotvit sloupce v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](freeze-columns-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-freeze-a-column-programmatically"></a>Postup zmrazení sloupce prostřednictvím kódu programu  
  
- Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Ovládací prvek s `dataGridView1` názvem, který obsahuje sloupec s názvem `AddToCartButton`. <xref:System.Windows.Forms.DataGridView>  
  
- Odkazy na <xref:System?displayProperty=nameWithType> sestavení a <xref:System.Windows.Forms?displayProperty=nameWithType> .  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Povolit změnu pořadí sloupců v ovládacím prvku DataGridView model Windows Forms](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
