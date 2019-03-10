---
title: Řazení dat v ovládacím prvku Windows Forms DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 606ffc7bd6136b775adaaaa79cf5042cf1e2dd70
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57724918"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="f01c4-102">Řazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f01c4-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="f01c4-103">Ve výchozím nastavení, mohou uživatelé řadit data <xref:System.Windows.Forms.DataGridView> řízení kliknutím na záhlaví sloupce, pole textu (nebo stisknutím klávesy F3 při textového pole buňky se zaměřuje na rozhraní .NET Framework 4.7.2 a novějších verzí).</span><span class="sxs-lookup"><span data-stu-id="f01c4-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="f01c4-104">Můžete upravit <xref:System.Windows.Forms.DataGridViewColumn.SortMode> vlastnost konkrétní sloupce do mřížek uživatelům řazení pomocí jiných typů sloupce při je vhodné tak učinit.</span><span class="sxs-lookup"><span data-stu-id="f01c4-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="f01c4-105">Data můžete také řadit programově podle libovolného sloupce, nebo více sloupců.</span><span class="sxs-lookup"><span data-stu-id="f01c4-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="f01c4-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="f01c4-106">In this section</span></span>

[<span data-ttu-id="f01c4-107">Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f01c4-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="f01c4-108">Popisuje možnosti pro řazení dat v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="f01c4-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="f01c4-109">Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f01c4-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="f01c4-110">Popisuje, jak povolit uživatelům seřadit podle sloupce, které nejsou ve výchozím nastavení řazení.</span><span class="sxs-lookup"><span data-stu-id="f01c4-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="f01c4-111">Postupy: Přizpůsobení třídění v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f01c4-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="f01c4-112">Popisuje způsob řazení dat prostřednictvím kódu programu a tom, jak přizpůsobit pomocí řazení <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> události nebo implementací <xref:System.Collections.IComparer> rozhraní.</span><span class="sxs-lookup"><span data-stu-id="f01c4-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="f01c4-113">Odkaz</span><span class="sxs-lookup"><span data-stu-id="f01c4-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="f01c4-114">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="f01c4-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="f01c4-115">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.Sort%2A> metody.</span><span class="sxs-lookup"><span data-stu-id="f01c4-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="f01c4-116">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="f01c4-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="f01c4-117">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridViewColumnSortMode> výčtu.</span><span class="sxs-lookup"><span data-stu-id="f01c4-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="f01c4-118">Viz také:</span><span class="sxs-lookup"><span data-stu-id="f01c4-118">See also</span></span>

- [<span data-ttu-id="f01c4-119">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="f01c4-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="f01c4-120">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="f01c4-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
