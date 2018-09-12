---
title: 'Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGridView control [Windows Forms], disabling data entry
- data entry [Windows Forms], disabling in grids
- data grids [Windows Forms], disabling data entry
ms.assetid: ef9539ce-539b-404e-84b6-ac282b64b88c
ms.openlocfilehash: 6263c92e6a981983c19e9d7f2357c581bee5ec07
ms.sourcegitcommit: 8c2ece71e54f46aef9a2153540d0bda7e74b19a9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/12/2018
ms.locfileid: "44508709"
---
# <a name="how-to-prevent-row-addition-and-deletion-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="a4a83-102">Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4a83-102">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="a4a83-103">Někdy budete chtít zabránit uživatelům v nové řádky dat zadávat nebo odstranění existující řádky v vaše <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="a4a83-103">Sometimes you will want to prevent users from entering new rows of data or deleting existing rows in your <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="a4a83-104"><xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> Vlastnost určuje, zda je k dispozici v dolní části ovládacího prvku řádek pro nové záznamy, zatímco <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> vlastnost určuje, zda je možné odebrat řádky.</span><span class="sxs-lookup"><span data-stu-id="a4a83-104">The <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A> property indicates whether the row for new records is present at the bottom of the control, while the <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A> property indicates whether rows can be removed.</span></span> <span data-ttu-id="a4a83-105">Následující příklad kódu používá tyto vlastnosti a také se nastaví <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> vlastnost nastavit ovládací prvek zcela jen pro čtení.</span><span class="sxs-lookup"><span data-stu-id="a4a83-105">The following code example uses these properties and also sets the <xref:System.Windows.Forms.DataGridView.ReadOnly%2A> property to make the control entirely read-only.</span></span>  
  
 <span data-ttu-id="a4a83-106">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="a4a83-106">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="a4a83-107">Viz také [postupy: zabránění přidávání řádků a odstraňování v prvku DataGridView formuláře Windows ovládacího prvku pomocí návrháře](https://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="a4a83-107">Also see [How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control Using the Designer](https://msdn.microsoft.com/library/k5c88sw3\(v=vs.110\)).</span></span>  
  
## <a name="example"></a><span data-ttu-id="a4a83-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="a4a83-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#090)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#090](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#090)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="a4a83-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="a4a83-109">Compiling the Code</span></span>  
 <span data-ttu-id="a4a83-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="a4a83-110">This example requires:</span></span>  
  
-   <span data-ttu-id="a4a83-111">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="a4a83-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="a4a83-112">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="a4a83-112">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="a4a83-113">Viz také</span><span class="sxs-lookup"><span data-stu-id="a4a83-113">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.ReadOnly%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToAddRows%2A?displayProperty=nameWithType>  
 <xref:System.Windows.Forms.DataGridView.AllowUserToDeleteRows%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="a4a83-114">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="a4a83-114">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)
