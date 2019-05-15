---
title: 'Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], object binding
- data grids [Windows Forms], object binding
- object binding [Windows Forms], DataGridView control
ms.assetid: cb8f29fa-577e-4e2b-883f-3a01c6189b9c
ms.openlocfilehash: 8cdfd5d8e5ec3dcd22abb9e4efcec3bb61fee1d9
ms.sourcegitcommit: c7a7e1468bf0fa7f7065de951d60dfc8d5ba89f5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/14/2019
ms.locfileid: "65591317"
---
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a>Postupy: Vytvoření vazby objektů k ovládacím prvkům Windows Forms DataGridView
Následující příklad kódu ukazuje, jak vytvořit vazbu na kolekci objektů do <xref:System.Windows.Forms.DataGridView> tak, aby každý objekt zobrazí jako samostatný řádek. Tento příklad také znázorňuje způsob zobrazení vlastností s typem výčtu v <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak, aby rozevíracího seznamu pole se seznamem obsahuje hodnoty výčtu.  
  
## <a name="example"></a>Příklad  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a>Probíhá kompilace kódu  
 Tento příklad vyžaduje:  
  
- Odkazy na sestavení systému a System.Windows.Forms.  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Forms.DataGridView>
- [Zobrazení dat v ovládacím prvku Windows Forms DataGridView](displaying-data-in-the-windows-forms-datagridview-control.md)
- [Postupy: Přístup k objektům Svázaným Windows Forms DataGridView řádků](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
