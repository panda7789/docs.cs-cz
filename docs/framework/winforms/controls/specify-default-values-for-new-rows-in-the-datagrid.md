---
title: Určení výchozích hodnot pro nové řádky v ovládacím prvku DataGridView
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
ms.openlocfilehash: 364f922aefc10e57f2ed7f3a0c2a5b25c922d87a
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742931"
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f7c2d-102">Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f7c2d-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="f7c2d-103">Když aplikace vyplní výchozí hodnoty pro nově přidané řádky, můžete zadat data lépe.</span><span class="sxs-lookup"><span data-stu-id="f7c2d-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="f7c2d-104">Pomocí třídy <xref:System.Windows.Forms.DataGridView> můžete do události <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> zadat výchozí hodnoty.</span><span class="sxs-lookup"><span data-stu-id="f7c2d-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="f7c2d-105">Tato událost se vyvolá, když uživatel zadá řádek pro nové záznamy.</span><span class="sxs-lookup"><span data-stu-id="f7c2d-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="f7c2d-106">Když kód zpracovává tuto událost, můžete požadované buňky naplnit hodnotami podle vašeho výběru.</span><span class="sxs-lookup"><span data-stu-id="f7c2d-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="f7c2d-107">Následující příklad kódu ukazuje, jak zadat výchozí hodnoty pro nové řádky pomocí události <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.</span><span class="sxs-lookup"><span data-stu-id="f7c2d-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="f7c2d-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="f7c2d-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="f7c2d-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="f7c2d-109">Compiling the Code</span></span>  
 <span data-ttu-id="f7c2d-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="f7c2d-110">This example requires:</span></span>  
  
- <span data-ttu-id="f7c2d-111"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="f7c2d-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
- <span data-ttu-id="f7c2d-112">Funkce `NewCustomerId` pro generování jedinečných `CustomerID`ch hodnot.</span><span class="sxs-lookup"><span data-stu-id="f7c2d-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
- <span data-ttu-id="f7c2d-113">Odkazy na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="f7c2d-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="f7c2d-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="f7c2d-114">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>
- [<span data-ttu-id="f7c2d-115">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f7c2d-115">Data Entry in the Windows Forms DataGridView Control</span></span>](data-entry-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="f7c2d-116">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f7c2d-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
