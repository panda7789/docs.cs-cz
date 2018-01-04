---
title: "Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView"
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
- DataGridView control [Windows Forms], hiding columns
- data grids [Windows Forms], hiding columns
- columns [Windows Forms], hiding
ms.assetid: 3f94143a-2ef0-49a5-a22a-b2e6f9289642
caps.latest.revision: "19"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 8fb7c5f4d0700dc5e036f88592cc8f35ec7e2cac
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-hide-columns-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="06371-102">Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="06371-102">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="06371-103">Někdy budete chtít zobrazit jenom některé sloupce, které jsou k dispozici v systému Windows Forms <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="06371-103">Sometimes you will want to display only some of the columns that are available in a Windows Forms <xref:System.Windows.Forms.DataGridView> control.</span></span> <span data-ttu-id="06371-104">Například můžete chtít zobrazit zaměstnanec mzda sloupec uživatelů s přihlašovacími údaji správy při skrytí od jiných uživatelů.</span><span class="sxs-lookup"><span data-stu-id="06371-104">For example, you might want to show an employee salary column to users with management credentials while hiding it from other users.</span></span> <span data-ttu-id="06371-105">Alternativně můžete chtít vytvořit vazbu ovládacího prvku na zdroj dat, který obsahuje mnoho sloupců, jenom některé z nich chcete zobrazit.</span><span class="sxs-lookup"><span data-stu-id="06371-105">Alternately, you might want to bind the control to a data source that contains many columns, only some of which you want to display.</span></span> <span data-ttu-id="06371-106">V takovém případě budou sloupce můžete nejsou ve zobrazení místo skryjete odebrat obvykle.</span><span class="sxs-lookup"><span data-stu-id="06371-106">In this case, you will typically remove the columns you are not interested in displaying rather than hide them.</span></span>  
  
 <span data-ttu-id="06371-107">V <xref:System.Windows.Forms.DataGridView> ovládací prvek, <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> hodnota vlastnosti sloupce určuje, zda je tento sloupec zobrazovat.</span><span class="sxs-lookup"><span data-stu-id="06371-107">In the <xref:System.Windows.Forms.DataGridView> control, the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A> property value of a column determines whether that column is displayed.</span></span>  
  
 <span data-ttu-id="06371-108">Není poskytována podpora pro tuto úlohu v sadě Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="06371-108">There is support for this task in Visual Studio.</span></span>  <span data-ttu-id="06371-109">Viz také [postupy: skrytí sloupců v Windows Forms DataGridView – ovládací prvek pomocí návrháře](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span><span class="sxs-lookup"><span data-stu-id="06371-109">Also see [How to: Hide Columns in the Windows Forms DataGridView Control Using the Designer](http://msdn.microsoft.com/library/kaswfbes\(v=vs.110\)).</span></span>  
  
### <a name="to-hide-a-column-programmatically"></a><span data-ttu-id="06371-110">Skrytí sloupce prostřednictvím kódu programu</span><span class="sxs-lookup"><span data-stu-id="06371-110">To hide a column programmatically</span></span>  
  
-   <span data-ttu-id="06371-111">Nastavte <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> vlastnost `false`.</span><span class="sxs-lookup"><span data-stu-id="06371-111">Set the <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType> property to `false`.</span></span> <span data-ttu-id="06371-112">Skrytí `CustomerID` sloupec, který se automaticky vygeneroval během vazby dat, umístit v následujícím příkladu kódu <xref:System.Windows.Forms.DataGridView.DataBindingComplete> obslužné rutiny události.</span><span class="sxs-lookup"><span data-stu-id="06371-112">To hide a `CustomerID` column that is automatically generated during data binding, place the following code example in a <xref:System.Windows.Forms.DataGridView.DataBindingComplete> event handler.</span></span>  
  
     [!code-csharp[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/csharp/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/CS/datagridviewmisc.cs#063)]
     [!code-vb[System.Windows.Forms.DataGridViewMisc#063](../../../../samples/snippets/visualbasic/VS_Snippets_Winforms/System.Windows.Forms.DataGridViewMisc/VB/datagridviewmisc.vb#063)]  
  
## <a name="compiling-the-code"></a><span data-ttu-id="06371-113">Probíhá kompilace kódu</span><span class="sxs-lookup"><span data-stu-id="06371-113">Compiling the Code</span></span>  
 <span data-ttu-id="06371-114">Tento příklad vyžaduje:</span><span class="sxs-lookup"><span data-stu-id="06371-114">This example requires:</span></span>  
  
-   <span data-ttu-id="06371-115">A <xref:System.Windows.Forms.DataGridView> ovládací prvek s názvem `dataGridView1` , který obsahuje sloupec s názvem `CustomerID`.</span><span class="sxs-lookup"><span data-stu-id="06371-115">A <xref:System.Windows.Forms.DataGridView> control named `dataGridView1` that contains a column named `CustomerID`.</span></span>  
  
-   <span data-ttu-id="06371-116">Odkazuje na <xref:System?displayProperty=nameWithType> a <xref:System.Windows.Forms?displayProperty=nameWithType> sestavení.</span><span class="sxs-lookup"><span data-stu-id="06371-116">References to the <xref:System?displayProperty=nameWithType> and <xref:System.Windows.Forms?displayProperty=nameWithType> assemblies.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="06371-117">Viz také</span><span class="sxs-lookup"><span data-stu-id="06371-117">See Also</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <xref:System.Windows.Forms.DataGridViewColumn.Visible%2A?displayProperty=nameWithType>  
 [<span data-ttu-id="06371-118">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="06371-118">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-column-row-and-cell-features-wf-datagridview-control.md)  
 [<span data-ttu-id="06371-119">Postupy: Odebrání automaticky vygenerovaných sloupců z ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="06371-119">How to: Remove Autogenerated Columns from a Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/remove-autogenerated-columns-from-a-wf-datagridview-control.md)  
 [<span data-ttu-id="06371-120">Postupy: Změna pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="06371-120">How to: Change the Order of Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-change-the-order-of-columns-in-the-windows-forms-datagridview-control.md)
