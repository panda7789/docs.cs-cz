---
title: Zabránit přidávání a odstraňování řádků v ovládacím prvku DataGridView
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: de8e0412faf8c3731f9356771b35a4a5d31b6ec7
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76728719"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9232d-102">Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9232d-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9232d-103">Někdy budete chtít uživatelům zabránit v zadávání nových řádků dat nebo odstranění existujících řádků v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9232d-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="9232d-104">Vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> označuje, zda je řádek pro nové záznamy přítomen v dolní části ovládacího prvku, zatímco vlastnost <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> označuje, zda lze odebrat řádky.</span><span class="sxs-lookup"><span data-stu-id="9232d-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="9232d-105">Následující příklad kódu používá tyto vlastnosti a také nastavuje vlastnost <xref:System.Windows.Forms.DataGridView.ReadOnly%2A>, aby byl ovládací prvek zcela určen jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="9232d-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="9232d-106">Pro tuto úlohu se v aplikaci Visual Studio podporuje.</span><span class="sxs-lookup"><span data-stu-id="9232d-106">There is support for this task in Visual Studio.</span></span> <span data-ttu-id="9232d-107">Viz také [Postupy: zabránění přidávání a odstraňování řádků v ovládacím prvku DataGridView model Windows Forms pomocí návrháře](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span><span class="sxs-lookup"><span data-stu-id="9232d-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](prevent-row-addition-and-deletion-in-the-datagrid-using-the-designer.md).</span></span>  
  
## <a name="example"></a><span data-ttu-id="9232d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="9232d-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="9232d-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="9232d-109">Compiling the Code</span></span>  
 <span data-ttu-id="9232d-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="9232d-110">This example requires:</span></span>  
  
- <span data-ttu-id="9232d-111"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="9232d-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="9232d-112">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="9232d-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9232d-113">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9232d-113">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>
- [<span data-ttu-id="9232d-114">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9232d-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](basic-column-row-and-cell-features-wf-datagridview-control.md)
