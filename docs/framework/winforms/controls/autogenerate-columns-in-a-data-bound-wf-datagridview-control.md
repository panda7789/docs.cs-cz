---
title: "Postupy: Automatické generování sloupců v daty připojeném ovládacím prvku Windows Forms DataGridView"
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
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
caps.latest.revision: "13"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: e1d6a790f8a43f4ea2f9d3ad2cdb282186554da6
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="19608-102">Postupy: Automatické generování sloupců v daty připojeném ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="19608-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="19608-103">Následující příklad kódu ukazuje, jak zobrazit sloupce z vázaný datový zdroj v <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="19608-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="19608-104">Když <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> hodnota vlastnosti je `true` (výchozí), <xref:System.Windows.Forms.DataGridViewColumn> se vytvoří pro každý sloupec v tabulce datového zdroje.</span><span class="sxs-lookup"><span data-stu-id="19608-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="19608-105">Pokud <xref:System.Windows.Forms.DataGridView> ovládací prvek již má sloupce, když nastavíte <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> vlastnost, existující hranice sloupce jsou ve srovnání s sloupce ve zdroji dat a zachovají vždy, když je nalezena shoda.</span><span class="sxs-lookup"><span data-stu-id="19608-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="19608-106">Nevázaných sloupců se vždycky zachovají.</span><span class="sxs-lookup"><span data-stu-id="19608-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="19608-107">Vázané sloupce, pro které neexistuje shoda ve zdroji dat, se odeberou.</span><span class="sxs-lookup"><span data-stu-id="19608-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="19608-108">Sloupce ve zdroji dat, pro které neexistuje shoda v ovládacím prvku generovat nové <xref:System.Windows.Forms.DataGridViewColumn> objekty, které jsou přidány na konec <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="19608-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="19608-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="19608-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="19608-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="19608-110">Compiling the Code</span></span>  
 <span data-ttu-id="19608-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="19608-111">This example requires:</span></span>  
  
-   <span data-ttu-id="19608-112">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `customersDataGridView`.</span><span class="sxs-lookup"><span data-stu-id="19608-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
-   <span data-ttu-id="19608-113">A <xref:System.Data.DataSet> objekt s názvem `customersDataSet` , obsahuje tabulku s názvem `Customers`.</span><span class="sxs-lookup"><span data-stu-id="19608-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
-   <span data-ttu-id="19608-114">Odkazuje na <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, a <xref:System.Xml?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="19608-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="19608-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="19608-115">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="19608-116">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="19608-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 [<span data-ttu-id="19608-117">Postupy: odebrání automaticky vygenerovaných sloupců z Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="19608-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)
