---
title: "Řazení dat v ovládacím prvku Windows Forms DataGridView"
ms.date: 02/13/2018
ms.prod: .net-framework
ms.technology:
- dotnet-winforms
ms.topic: article
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload:
- dotnet
ms.openlocfilehash: 6ab4ec958a4275ed805ed33ee3eff9ab67fde3dc
ms.sourcegitcommit: 973a12d1e6962cd9a9c263fbfaad040ec8267fe9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/22/2018
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="2f780-102">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="2f780-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="2f780-103">Ve výchozím nastavení, mohou uživatelé seřadit data v <xref:System.Windows.Forms.DataGridView> řízení kliknutím na záhlaví sloupce pole text (nebo stiskněte F3 při buňku pole text se zaměřuje na rozhraní .NET Framework 4.7.2 a novější).</span><span class="sxs-lookup"><span data-stu-id="2f780-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="2f780-104">Můžete upravit <xref:System.Windows.Forms.DataGridViewColumn.SortMode> vlastnost konkrétní sloupců, aby uživatelé mohli seřadit jiné typy sloupců, když má smysl to udělat.</span><span class="sxs-lookup"><span data-stu-id="2f780-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="2f780-105">Data můžete také řadit prostřednictvím kódu programu žádný sloupec nebo více sloupců.</span><span class="sxs-lookup"><span data-stu-id="2f780-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="2f780-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="2f780-106">In this section</span></span>

[<span data-ttu-id="2f780-107">Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="2f780-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="2f780-108">Popisuje možnosti pro řazení dat v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="2f780-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="2f780-109">Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="2f780-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="2f780-110">Popisuje, jak povolit uživatelům řadit podle sloupce, které nejsou ve výchozím nastavení řazení.</span><span class="sxs-lookup"><span data-stu-id="2f780-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="2f780-111">Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="2f780-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="2f780-112">Popisuje, jak řadit data prostřednictvím kódu programu a postup přizpůsobení řazení pomocí <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> událostí nebo implementací <xref:System.Collections.IComparer> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="2f780-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="2f780-113">Odkaz</span><span class="sxs-lookup"><span data-stu-id="2f780-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="2f780-114">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="2f780-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="2f780-115">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.Sort%2A> metoda.</span><span class="sxs-lookup"><span data-stu-id="2f780-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="2f780-116">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="2f780-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="2f780-117">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewColumnSortMode> výčtu.</span><span class="sxs-lookup"><span data-stu-id="2f780-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="2f780-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="2f780-118">See also</span></span>

[<span data-ttu-id="2f780-119">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="2f780-119">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
[<span data-ttu-id="2f780-120">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="2f780-120">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)  