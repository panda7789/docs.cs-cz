---
title: Vytvoření nevázaného ovládacího prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], unbound data
- DataGridView control [Windows Forms], displaying data without binding to a data source
- data [Windows Forms], unbound
ms.assetid: b5d4b47d-9a28-4d88-9dba-0a3c90fba71d
ms.openlocfilehash: 0b477eba6d8455554d72dc7ec8cfce68a91add38
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76731002"
---
# <a name="how-to-create-an-unbound-windows-forms-datagridview-control"></a>Postupy: Vytvoření nepřipojeného ovládacího prvku Windows Forms DataGridView
Následující příklad kódu ukazuje, jak naplnit ovládací prvek <xref:System.Windows.Forms.DataGridView> programově bez jeho svázání se zdrojem dat. To je užitečné v případě, že máte malé množství dat, která chcete zobrazit ve formátu tabulky.  
  
 Úplné vysvětlení tohoto příkladu kódu naleznete v tématu [Návod: Vytvoření nevázaného ovládacího prvku DataGridView model Windows Forms](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md).  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/CS/simpleunbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridViewSimpleUnbound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewSimpleUnbound/VB/simpleunbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System, System. Drawing a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Návod: Vytvoření nevázaného ovládacího prvku Windows Forms DataGridView](walkthrough-creating-an-unbound-windows-forms-datagridview-control.md)
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Režimy zobrazení dat v ovládacím prvku Windows Forms DataGridView](data-display-modes-in-the-windows-forms-datagridview-control.md)
