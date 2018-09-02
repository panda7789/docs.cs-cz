---
title: 'Postupy: Přepnutí sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], read-only columns
- DataGridView control [Windows Forms], read-only columns
ms.assetid: 2bb73ebb-1a55-4362-9fda-e50574c087d5
ms.openlocfilehash: a8b5c0f9492941cf0e01e016d9fb097e1df44d2e
ms.sourcegitcommit: efff8f331fd9467f093f8ab8d23a203d6ecb5b60
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/01/2018
ms.locfileid: "43389712"
---
# <a name="how-to-make-columns-read-only-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="d8b17-102">Postupy: Přepnutí sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d8b17-102">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="d8b17-103">Všechna data je určena pro úpravy.</span><span class="sxs-lookup"><span data-stu-id="d8b17-103">Not all data is meant for editing.</span></span> <span data-ttu-id="d8b17-104">V <xref:System.Windows.Forms.DataGridView> ovládací prvek sloupec <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> vlastnost hodnota určuje, zda uživatelé mohou upravovat buňky ve sloupci.</span><span class="sxs-lookup"><span data-stu-id="d8b17-104">In the <xref:System.Windows.Forms.DataGridView> control, the column <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A> property value determines whether users can edit cells in that column.</span></span> <span data-ttu-id="d8b17-105">Informace o tom, jak nastavit ovládací prvek zcela jen pro čtení najdete v tématu [postupy: zabránění přidávání řádků a odstraňování v ovládacím prvku Windows Forms DataGridView](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span><span class="sxs-lookup"><span data-stu-id="d8b17-105">For information about how to make the control entirely read-only, see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md).</span></span>  
  
 <span data-ttu-id="d8b17-106">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="d8b17-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="d8b17-107">Viz také [jak: vytvořit sloupce jen pro čtení v Windows Forms DataGridView ovládacího prvku pomocí návrháře](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="d8b17-107">Also see [How to: Make Columns Read-Only in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/xd4k3c7e\(v=vs.110\)).</span></span>  
  
### <a name="to-make-a-column-read-only-programmatically"></a><span data-ttu-id="d8b17-108">Chcete-li sloupec jen pro čtení prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="d8b17-108">To make a column read-only programmatically</span></span>  
  
-   <span data-ttu-id="d8b17-109">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="d8b17-109">Set the <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType> property to `true`.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#064)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#064](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#064)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="d8b17-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="d8b17-110">Compiling the Code</span></span>  
 <span data-ttu-id="d8b17-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="d8b17-111">This example requires:</span></span>  
  
-   <span data-ttu-id="d8b17-112">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` sloupec s názvem `CompanyName`.</span><span class="sxs-lookup"><span data-stu-id="d8b17-112">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` with a column named `CompanyName`.</span></span>  
  
-   <span data-ttu-id="d8b17-113">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="d8b17-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="d8b17-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="d8b17-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.Columns%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridViewColumn.ReadOnly%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="d8b17-115">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d8b17-115">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="d8b17-116">Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="d8b17-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)
