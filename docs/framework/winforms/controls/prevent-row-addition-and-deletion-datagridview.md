---
title: 'Postupy: Zabránit řádku přidání a odstranění v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: 9f579720b4f3ff561ecd807e09db8d464abc9001
ms.sourcegitcommit: 2b986afe4ce9e13bbeec929c9737757eb61de60e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2019
ms.locfileid: "56664585"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a>Postupy: Zabránit řádku přidání a odstranění v ovládacím prvku Windows Forms DataGridView
Někdy budete chtít zabránit uživatelům v nové řádky dat zadávat nebo odstranění existující řádky v vaše <xref:System.Windows.Forms.DataGridView> ovládacího prvku. <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> Vlastnost určuje, zda je k dispozici v dolní části ovládacího prvku řádek pro nové záznamy, zatímco <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> vlastnost určuje, zda je možné odebrat řádky. Následující příklad kódu používá tyto vlastnosti a také se nastaví <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> vlastnost nastavit ovládací prvek zcela jen pro čtení.  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio. Viz také [jak: Zamezení přidávání řádků a odstranění v Windows Forms DataGridView pomocí návrháře](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.  
  
-   Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také:
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
