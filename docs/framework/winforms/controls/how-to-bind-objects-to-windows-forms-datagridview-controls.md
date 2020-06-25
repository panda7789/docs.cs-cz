---
title: Vytvoření vazby objektů k ovládacím prvkům DataGridView
description: Naučte se, jak vytvořit vazby kolekce objektů k ovládacímu prvku DataGridView model Windows Forms, aby se každý objekt zobrazoval jako samostatný řádek.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: add0047937b404dcec1ea12bac8053bb9bdfcf1c
ms.sourcegitcommit: dc2feef0794cf41dbac1451a13b8183258566c0e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/24/2020
ms.locfileid: "85325854"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>Postupy: Připojení objektů k ovládacím prvkům Windows Forms DataGridView
Následující příklad kódu ukazuje, jak vytvořit vazby kolekce objektů k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku tak, aby se každý objekt zobrazoval jako samostatný řádek. Tento příklad také ukazuje, jak zobrazit vlastnost s výčtovým typem v <xref:System.Windows.Forms.DataGridViewComboBoxColumn> , aby rozevírací seznam pole se seznamem obsahoval hodnoty výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení System a System. Windows. Forms.  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Forms.DataGridView>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Přístup k objektům svázaným s řádky Windows Forms DataGridView](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
