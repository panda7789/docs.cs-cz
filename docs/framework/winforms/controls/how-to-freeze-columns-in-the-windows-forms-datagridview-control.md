---
title: Ukotvit sloupce v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], freezing
- DataGridView control [Windows Forms], freezing columns
- DataGridView control [Windows Forms], columns always in view
ms.assetid: 2ef8b1de-782e-4867-af8d-58171ab5c106
ms.openlocfilehash: 6d1a98e5c4332078c6012cb7c9ed836108abd86c
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76736744"
---
# <a name="how-to-freeze-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView
Když uživatelé zobrazují data zobrazená v model Windows Forms <xref:System.Windows.Forms.DataGridView>m ovládacím prvku, někdy potřebují často odkazovat na jeden sloupec nebo na sadu sloupců. Když například zobrazíte tabulku s informacemi o zákaznících, které obsahují mnoho sloupců, je vhodné zobrazit jméno zákazníka vždy, když se ostatní sloupce posouvají mimo viditelnou oblast.  
  
 Chcete-li dosáhnout tohoto chování, můžete ukotvit sloupce v ovládacím prvku. Při ukotvení sloupce jsou zmrazeny také všechny sloupce vlevo (nebo napravo ve skriptech se zápisem zprava doleva). Zmrazené sloupce zůstávají na místě, zatímco všechny ostatní sloupce se můžou posouvat.  
  
> [!NOTE]
> Pokud je povoleno přeřazení sloupce, jsou zmrazené sloupce považovány za skupinu odlišnou od nezmrazených sloupců. Uživatelé mohou přemístit sloupce v obou skupinách, ale nemohou přesunout sloupec z jedné skupiny do druhé.  
  
 Vlastnost <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A> sloupce určuje, zda je sloupec v mřížce vždy zobrazen.  
  
 Pro tuto úlohu se v aplikaci Visual Studio podporuje.  Přečtěte si také téma [How to: mrazit sloupce v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](freeze-columns-in-the-datagrid-using-the-designer.md).  
  
### <a name="to-freeze-a-column-programmatically"></a>Postup zmrazení sloupce prostřednictvím kódu programu  
  
- Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType> vlastnost `true`.  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#061)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#061](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#061)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`, který obsahuje sloupec s názvem `AddToCartButton`.  
  
- Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridViewColumn.Frozen%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](basic-column-row-and-cell-features-wf-datagridview-control.md)
- [Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)
