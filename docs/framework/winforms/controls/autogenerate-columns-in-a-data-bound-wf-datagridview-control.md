---
title: Vygeneruje sloupce v ovládacím prvku DataGridView vázaného na data.
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data grids [Windows Forms], autogenerating columns
- columns [Windows Forms], autogenerating
- DataGridView control [Windows Forms], data-bound columns
ms.assetid: 699f6f9e-6aa5-4811-902b-6a2c57dec7d6
ms.openlocfilehash: 860e640e095537358d2f8778c810aa577e9d7ff0
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746230"
---
# <a name="how-to-autogenerate-columns-in-a-data-bound-windows-forms-datagridview-control"></a><span data-ttu-id="5d80e-102">Postupy: Automatické generování sloupců v daty připojeném ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5d80e-102">How to: Autogenerate Columns in a Data-Bound Windows Forms DataGridView Control</span></span>
<span data-ttu-id="5d80e-103">Následující příklad kódu ukazuje, jak zobrazit sloupce z vázaného zdroje dat v ovládacím prvku <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="5d80e-103">The following code example demonstrates how to display columns from a bound data source in a <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="5d80e-104">Pokud je hodnota vlastnosti <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> `true` (výchozí), vytvoří se <xref:System.Windows.Forms.DataGridViewColumn> pro každý sloupec v tabulce zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="5d80e-104">When the <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A> property value is `true` (the default), a <xref:System.Windows.Forms.DataGridViewColumn> is created for each column in the data source table.</span></span>  
  
 <span data-ttu-id="5d80e-105">Pokud ovládací prvek <xref:System.Windows.Forms.DataGridView> už má při nastavování vlastnosti <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> sloupce, existující vázané sloupce se porovnají se sloupci ve zdroji dat a zachovají se, kdykoli dojde ke shodě.</span><span class="sxs-lookup"><span data-stu-id="5d80e-105">If the <xref:System.Windows.Forms.DataGridView> control already has columns when you set the <xref:System.Windows.Forms.DataGridViewComboBoxColumn.DataSource%2A> property, the existing bound columns are compared to the columns in the data source and preserved whenever there is a match.</span></span> <span data-ttu-id="5d80e-106">Nevázané sloupce se vždycky zachovají.</span><span class="sxs-lookup"><span data-stu-id="5d80e-106">Unbound columns are always preserved.</span></span> <span data-ttu-id="5d80e-107">Z vázaných sloupců, pro které se neshodují žádné shody ve zdroji dat, se odeberou.</span><span class="sxs-lookup"><span data-stu-id="5d80e-107">Bound columns for which there is no match in the data source are removed.</span></span> <span data-ttu-id="5d80e-108">Sloupce ve zdroji dat, pro které neexistuje žádná shoda v ovládacím prvku generují nové <xref:System.Windows.Forms.DataGridViewColumn> objekty, které jsou přidány na konec <xref:System.Windows.Forms.DataGridView.Columns%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="5d80e-108">Columns in the data source for which there is no match in the control generate new <xref:System.Windows.Forms.DataGridViewColumn> objects, which are added to the end of the <xref:System.Windows.Forms.DataGridView.Columns%2A> collection.</span></span>  
  
## <a name="example"></a><span data-ttu-id="5d80e-109">Příklad</span><span class="sxs-lookup"><span data-stu-id="5d80e-109">Example</span></span>  
 [!code-csharp[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#020)]
 [!code-vb[System.Windows.Forms.DataGridViewMisc#020](~/samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#020)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="5d80e-110">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="5d80e-110">Compiling the Code</span></span>  
 <span data-ttu-id="5d80e-111">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="5d80e-111">This example requires:</span></span>  
  
- <span data-ttu-id="5d80e-112"><xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `customersDataGridView`.</span><span class="sxs-lookup"><span data-stu-id="5d80e-112">A <xref:System.Windows.Forms.DataGridView> control named `customersDataGridView`.</span></span>  
  
- <span data-ttu-id="5d80e-113">Objekt <xref:System.Data.DataSet> s názvem `customersDataSet` obsahující tabulku s názvem `Customers`.</span><span class="sxs-lookup"><span data-stu-id="5d80e-113">A <xref:System.Data.DataSet> object named `customersDataSet` that has a table named `Customers`.</span></span>  
  
- <span data-ttu-id="5d80e-114">Odkazy na sestavení <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>a <xref:System.Xml?displayProperty=nameWithType>.</span><span class="sxs-lookup"><span data-stu-id="5d80e-114">References to the <xref:System?displayProperty=nameWithType>, <xref:System.Windows.Forms?displayProperty=nameWithType>, <xref:System.Data?displayProperty=nameWithType>, and <xref:System.Xml?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="5d80e-115">Viz také</span><span class="sxs-lookup"><span data-stu-id="5d80e-115">See also</span></span>

- <xref:System.Windows.Forms.DataGridView>
- <xref:System.Windows.Forms.DataGridView.AutoGenerateColumns%2A?displayProperty=nameWithType>
- [<span data-ttu-id="5d80e-116">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5d80e-116">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)
- [<span data-ttu-id="5d80e-117">Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="5d80e-117">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](remove-autogenerated-columns-from-a-wf-datagridview-control.md)
