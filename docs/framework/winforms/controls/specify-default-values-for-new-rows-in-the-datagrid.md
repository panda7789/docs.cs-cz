---
title: "Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], default values for new rows
- DataGridView control [Windows Forms], data entry
- rows [Windows Forms], specifying default values
- DataGridView control [Windows Forms], default values for new rows
ms.assetid: 8d127963-d9f8-4e4e-9f7f-beb66688f1f2
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 26f2ab0247c9d13a90560337c103a970afc8996c
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-specify-default-values-for-new-rows-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1bf51-102">Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1bf51-102">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1bf51-103">Vkládání dat můžete nastavit pohodlnější, když aplikace doplní ve výchozí hodnoty pro nově přidaného řádků.</span><span class="sxs-lookup"><span data-stu-id="1bf51-103">You can make data entry more convenient when the application fills in default values for newly added rows.</span></span> <span data-ttu-id="1bf51-104">S <xref:System.Windows.Forms.DataGridView> třídu, můžete vyplnit ve výchozí hodnoty <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.</span><span class="sxs-lookup"><span data-stu-id="1bf51-104">With the <xref:System.Windows.Forms.DataGridView> class, you can fill in default values with the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span> <span data-ttu-id="1bf51-105">Tato událost se vyvolá, když uživatel zadá řádek pro nové záznamy.</span><span class="sxs-lookup"><span data-stu-id="1bf51-105">This event is raised when the user enters the row for new records.</span></span> <span data-ttu-id="1bf51-106">Když váš kód zpracovává této události, může vyplnit požadované buněk s hodnotami dle vlastního výběru.</span><span class="sxs-lookup"><span data-stu-id="1bf51-106">When your code handles this event, you can populate desired cells with values of your choosing.</span></span>  
  
 <span data-ttu-id="1bf51-107">Následující příklad kódu ukazuje, jak zadat výchozí hodnoty pro nové řádky pomocí <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.</span><span class="sxs-lookup"><span data-stu-id="1bf51-107">The following code example demonstrates how to specify default values for new rows using the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
## <a name="example"></a><span data-ttu-id="1bf51-108">Příklad</span><span class="sxs-lookup"><span data-stu-id="1bf51-108">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#120)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#120](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#120)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="1bf51-109">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="1bf51-109">Compiling the Code</span></span>  
 <span data-ttu-id="1bf51-110">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="1bf51-110">This example requires:</span></span>  
  
-   <span data-ttu-id="1bf51-111">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1`.</span><span class="sxs-lookup"><span data-stu-id="1bf51-111">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1`.</span></span>  
  
-   <span data-ttu-id="1bf51-112">A `NewCustomerId` funkce pro generování jedinečný `CustomerID` hodnoty.</span><span class="sxs-lookup"><span data-stu-id="1bf51-112">A `NewCustomerId` function for generating unique `CustomerID` values.</span></span>  
  
-   <span data-ttu-id="1bf51-113">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="1bf51-113">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1bf51-114">Viz také</span><span class="sxs-lookup"><span data-stu-id="1bf51-114">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 [<span data-ttu-id="1bf51-115">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1bf51-115">Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/data-entry-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="1bf51-116">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1bf51-116">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)
