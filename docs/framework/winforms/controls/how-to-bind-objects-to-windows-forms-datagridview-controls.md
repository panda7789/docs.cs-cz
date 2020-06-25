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
# <a name="how-to-bind-objects-to-windows-forms-datagridview-controls"></a><span data-ttu-id="e8f44-103">Postupy: Připojení objektů k ovládacím prvkům Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e8f44-103">How to: Bind Objects to Windows Forms DataGridView Controls</span></span>
<span data-ttu-id="e8f44-104">Následující příklad kódu ukazuje, jak vytvořit vazby kolekce objektů k <xref:System.Windows.Forms.DataGridView> ovládacímu prvku tak, aby se každý objekt zobrazoval jako samostatný řádek.</span><span class="sxs-lookup"><span data-stu-id="e8f44-104">The following code example demonstrates how to bind a collection of objects to a <xref:System.Windows.Forms.DataGridView> control so that each object displays as a separate row.</span></span> <span data-ttu-id="e8f44-105">Tento příklad také ukazuje, jak zobrazit vlastnost s výčtovým typem v <xref:System.Windows.Forms.DataGridViewComboBoxColumn> , aby rozevírací seznam pole se seznamem obsahoval hodnoty výčtu.</span><span class="sxs-lookup"><span data-stu-id="e8f44-105">This example also illustrates how to display a property with an enumeration type in a <xref:System.Windows.Forms.DataGridViewComboBoxColumn> so that the combo box drop-down list contains the enumeration values.</span></span>  
  
## <a name="example"></a><span data-ttu-id="e8f44-106">Příklad</span><span class="sxs-lookup"><span data-stu-id="e8f44-106">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/CS/collectionbound.cs#00)]
 [!code-vb[System.Windows.Forms.DataGridView._CollectionBound#00](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridView._CollectionBound/VB/collectionbound.vb#00)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="e8f44-107">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="e8f44-107">Compiling the Code</span></span>  
 <span data-ttu-id="e8f44-108">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="e8f44-108">This example requires:</span></span>  
  
- <span data-ttu-id="e8f44-109">Odkazy na sestavení System a System. Windows. Forms.</span><span class="sxs-lookup"><span data-stu-id="e8f44-109">References to the System and System.Windows.Forms assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="e8f44-110">Viz také</span><span class="sxs-lookup"><span data-stu-id="e8f44-110">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- [<span data-ttu-id="e8f44-111">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e8f44-111">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="e8f44-112">Postupy: Přístup k objektům svázaným s řádky Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="e8f44-112">How to: Access Objects Bound to Windows Forms DataGridView Rows</span></span>](how-to-access-objects-bound-to-windows-forms-datagridview-rows.md)
