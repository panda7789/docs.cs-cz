---
title: 'Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
ms.openlocfilehash: 8a90cbef7032fd3753a6c9ec0b856a4e2ea1db27
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59193691"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="c71a8-102">Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c71a8-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="c71a8-103">Zadávání dat můžete provést pohodlnější, když aplikace vyplní ve výchozí hodnoty pro nově přidané řádky.</span><span class="sxs-lookup"><span data-stu-id="c71a8-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="c71a8-104">S <xref:System.Windows.Forms.DataGridView> třídy, můžete přejít k vyplnění ve výchozí hodnoty <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.</span><span class="sxs-lookup"><span data-stu-id="c71a8-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="c71a8-105">Tato událost je aktivována, když uživatel zadá řádek pro nové záznamy.</span><span class="sxs-lookup"><span data-stu-id="c71a8-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="c71a8-106">Když váš kód zpracovává tuto událost, která můžete naplnit požadované buňky s hodnotami, které si vyberete.</span><span class="sxs-lookup"><span data-stu-id="c71a8-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="c71a8-107">Následující příklad kódu ukazuje, jak určit výchozí hodnoty pro nové řádky pomocí <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.</span><span class="sxs-lookup"><span data-stu-id="c71a8-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="c71a8-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="c71a8-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="c71a8-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="c71a8-109">Compiling the Code</span></span>  
 <span data-ttu-id="c71a8-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="c71a8-110">This example requires:</span></span>  
  
-   <span data-ttu-id="c71a8-111">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="c71a8-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="c71a8-112">A `NewCustomerId` funkce generuje jedinečný `CustomerID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="c71a8-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
-   <span data-ttu-id="c71a8-113">Odkazy <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="c71a8-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="c71a8-114">Viz také:</span><span class="sxs-lookup"><span data-stu-id="c71a8-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="c71a8-115">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c71a8-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="c71a8-116">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="c71a8-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
