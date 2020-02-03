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
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="c2373-102">Postupy: Připojení objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c2373-102">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="c2373-103">Následující příklad kódu ukazuje, jak vytvořit vazby kolekce objektů k ovládacímu prvku <xref:System.Windows.Forms.DataGridView> tak, aby se každý objekt zobrazoval jako samostatný řádek.</span><span class="sxs-lookup"><span data-stu-id="c2373-103">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="c2373-104">Tento příklad také ukazuje, jak zobrazit vlastnost s výčtovým typem v <xref:System.Windows.Forms.DataGridViewComboBoxColumn> tak, aby rozevírací seznam pole se seznamem obsahoval hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="c2373-104">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c2373-105">Příklad</span><span class="sxs-lookup"><span data-stu-id="c2373-105">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c2373-106">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c2373-106">Compiling the Code</span></span>  
 <span data-ttu-id="c2373-107">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c2373-107">This example requires:</span></span>  
  
- <span data-ttu-id="c2373-108">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="c2373-108">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c2373-109">Viz také</span><span class="sxs-lookup"><span data-stu-id="c2373-109">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="c2373-110">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c2373-110">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c2373-111">Postupy: Přístup k objektům svázaným s řádky Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c2373-111">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
