---
title: 'Postupy: Nastavení sloupců jen pro čtení v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: e57f926208e67ce894b58bdfaf5d0c3e3815b2ab
ms.sourcegitcommit: 6b308cf6d627d78ee36dbbae8972a310ac7fd6c8
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/23/2019
ms.locfileid: "54514878"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="fe7ce-102">Postupy: Nastavení sloupců jen pro čtení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="fe7ce-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="fe7ce-103">Všechna data je určena pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="fe7ce-103">Not all data is meant for editing.</span></span> <span data-ttu-id="fe7ce-104">V <xref:System.Windows.Forms.DataGridView> ovládací prvek sloupec <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost hodnota určuje, zda uživatelé mohou upravovat buňky ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="fe7ce-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="fe7ce-105">Informace o tom, jak nastavit ovládací prvek zcela jen pro čtení najdete v tématu [jak: Zamezení přidávání řádků a odstranění v Windows Forms DataGridView](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="fe7ce-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="fe7ce-106">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="fe7ce-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="fe7ce-107">Viz také [jak: Přepnutí sloupců jen pro čtení v Windows Forms DataGridView pomocí návrháře](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="fe7ce-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="fe7ce-108">Chcete-li sloupec jen pro čtení prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="fe7ce-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="fe7ce-109">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="fe7ce-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="fe7ce-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="fe7ce-110">Compiling the Code</span></span>  
 <span data-ttu-id="fe7ce-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="fe7ce-111">This example requires:</span></span>  
  
-   <span data-ttu-id="fe7ce-112">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` sloupec s názvem `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="fe7ce-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="fe7ce-113">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="fe7ce-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fe7ce-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fe7ce-114">See also</span></span>
- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>
- <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>
- [<span data-ttu-id="fe7ce-115">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="fe7ce-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
- [<span data-ttu-id="fe7ce-116">Postupy: Zabránit řádku přidání a odstranění v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="fe7ce-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
