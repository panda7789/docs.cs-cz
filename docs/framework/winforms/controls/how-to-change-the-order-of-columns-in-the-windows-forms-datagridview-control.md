---
title: 'Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- columns [Windows Forms], changing order
- DataGridView control [Windows Forms], column order
- data grids [Windows Forms], changing column order
ms.assetid: 5e9ac3bc-b0f0-48cb-a3d5-b005af905395
ms.openlocfilehash: 75362a2623cfe685f38259b9e581b593b2bd8d17
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33530611"
---
# <a name="how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control"></a>Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView
Při použití <xref:System.Windows.Forms.DataGridView> k zobrazení dat ze zdroje dat, sloupce ve zdroji dat schématu někdy nejsou uvedeny v pořadí, které chcete zobrazit. Zobrazit pořadí sloupců můžete změnit pomocí <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A> vlastnost <xref:System.Windows.Forms.DataGridViewColumn> třídy.  
  
 Následující příklad kódu přemístí některé sloupce automaticky generuje při vytváření vazby pro tabulku zákazníků v ukázkové databázi Northwind. Další informace o tom, jak vytvořit vazbu <xref:System.Windows.Forms.DataGridView> řízení do databázové tabulky, najdete v části [postupy: vytvoření vazby dat ovládacího prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md).  
  
 Není poskytována podpora pro tuto úlohu v sadě Visual Studio.  Viz také [postupy: Změna pořadí sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/hb1dk7ax\(v=vs.110\))  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#040)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#040](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#040)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
-   A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `customersDataGridView` , je vázán k tabulce s názvy označeného sloupce, jako `Customers` tabulky v ukázkové databázi Northwind.  
  
-   Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, a <xref:System.Xml?displayProperty=nameWithType> sestavení.  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn>  
 <xref:System.Windows.Forms.DataGridViewColumn.DisplayIndex%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [Postupy: Vytvoření vazby dat k ovládacímu prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/how-to-bind-data-to-the-windows-forms-datagridview-control.md)
