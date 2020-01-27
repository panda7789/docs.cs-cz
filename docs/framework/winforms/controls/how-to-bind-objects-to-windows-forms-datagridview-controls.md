---
title: Vytvoření vazby objektů k ovládacím prvkům DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: d5aa5cb64c7fb2b82d69d6c87134ee901b84f5c1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746699"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>Postupy: Připojení objektů k ovládacím prvkům Windows Forms DataGridView
Následující příklad kódu ukazuje, jak vytvořit vazby kolekce objektů k ovládacímu prvku <xref:System.Windows.Forms.DataGridView> tak, aby se každý objekt zobrazoval jako samostatný řádek. Tento příklad také ukazuje, jak zobrazit vlastnost s výčtovým typem v <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak, aby rozevírací seznam pole se seznamem obsahoval hodnoty výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Přístup k objektům svázaným s řádky Windows Forms DataGridView](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
