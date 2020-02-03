---
title: Řazení dat v ovládacím prvku DataGridView
ms.date: 02/13/2018
helpviewer_keywords:
- data [Windows Forms], sorting in grids
- data grids [Windows Forms], sorting data
- DataGridView control [Windows Forms], sorting data
ms.assetid: c1d4f24c-d961-4181-809d-5a5caa6122e4
ms.openlocfilehash: 1fcd5a5f5c6d690c573c4c2c5fa7c32aa0292441
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742942"
---
# <a name="sorting-data-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="103d5-102">Řazení dat v ovládacím prvku DataGridView model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="103d5-102">Sorting data in the Windows Forms DataGridView control</span></span>

<span data-ttu-id="103d5-103">Ve výchozím nastavení mohou uživatelé řadit data v ovládacím prvku <xref:System.Windows.Forms.DataGridView> kliknutím na záhlaví sloupce textového pole (nebo stisknutím klávesy F3, když se buňka textového pole zaměřuje na .NET Framework 4.7.2 a novějších verzích).</span><span class="sxs-lookup"><span data-stu-id="103d5-103">By default, users can sort the data in a <xref:System.Windows.Forms.DataGridView> control by clicking the header of a text box column (or by pressing F3 when a text box cell is focused on .NET Framework 4.7.2 and later versions).</span></span> <span data-ttu-id="103d5-104">Můžete upravit vlastnost <xref:System.Windows.Forms.DataGridViewColumn.SortMode> určitých sloupců a umožnit tak uživatelům řazení podle jiných typů sloupců, když to bude mít smysl.</span><span class="sxs-lookup"><span data-stu-id="103d5-104">You can modify the <xref:System.Windows.Forms.DataGridViewColumn.SortMode> property of specific columns to allow users to sort by other column types when it makes sense to do so.</span></span> <span data-ttu-id="103d5-105">Data můžete také seřadit programově pomocí libovolného sloupce nebo více sloupců.</span><span class="sxs-lookup"><span data-stu-id="103d5-105">You can also sort the data programmatically by any column, or by multiple columns.</span></span>

## <a name="in-this-section"></a><span data-ttu-id="103d5-106">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="103d5-106">In this section</span></span>

[<span data-ttu-id="103d5-107">Režimy řazení sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="103d5-107">Column Sort Modes in the Windows Forms DataGridView Control</span></span>](column-sort-modes-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="103d5-108">Popisuje možnosti pro řazení dat v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="103d5-108">Describes the options for sorting data in the control.</span></span>

[<span data-ttu-id="103d5-109">Postupy: Nastavení režimů řazení pro sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="103d5-109">How to: Set the Sort Modes for Columns in the Windows Forms DataGridView Control</span></span>](set-the-sort-modes-for-columns-wf-datagridview-control.md)  
<span data-ttu-id="103d5-110">Popisuje, jak uživatelům umožnit řazení podle sloupců, které ve výchozím nastavení neodpovídají.</span><span class="sxs-lookup"><span data-stu-id="103d5-110">Describes how to enable users to sort by columns that are not sortable by default.</span></span>

[<span data-ttu-id="103d5-111">Postupy: Přizpůsobení řazení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="103d5-111">How to: Customize Sorting in the Windows Forms DataGridView Control</span></span>](how-to-customize-sorting-in-the-windows-forms-datagridview-control.md)  
<span data-ttu-id="103d5-112">Popisuje, jak řadit data programově a jak přizpůsobit řazení pomocí události <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> nebo implementací rozhraní <xref:System.Collections.IComparer>.</span><span class="sxs-lookup"><span data-stu-id="103d5-112">Describes how to sort data programmatically and how to customize sorting by using the <xref:System.Windows.Forms.DataGridView.SortCompare?displayProperty=nameWithType> event or by implementing the <xref:System.Collections.IComparer> interface.</span></span>

## <a name="reference"></a><span data-ttu-id="103d5-113">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="103d5-113">Reference</span></span>

<xref:System.Windows.Forms.DataGridView>  
<span data-ttu-id="103d5-114">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="103d5-114">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  

<xref:System.Windows.Forms.DataGridView.Sort%2A?displayProperty=nameWithType>  
<span data-ttu-id="103d5-115">Poskytuje referenční dokumentaci pro metodu <xref:System.Windows.Forms.DataGridView.Sort%2A>.</span><span class="sxs-lookup"><span data-stu-id="103d5-115">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.Sort%2A> method.</span></span>

<xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A?displayProperty=nameWithType>  
<span data-ttu-id="103d5-116">Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="103d5-116">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumn.SortMode%2A> property.</span></span>

<xref:System.Windows.Forms.DataGridViewColumnSortMode>  
<span data-ttu-id="103d5-117">Poskytuje referenční dokumentaci pro výčet <xref:System.Windows.Forms.DataGridViewColumnSortMode>.</span><span class="sxs-lookup"><span data-stu-id="103d5-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridViewColumnSortMode> enumeration.</span></span>

## <a name="see-also"></a><span data-ttu-id="103d5-118">Viz také</span><span class="sxs-lookup"><span data-stu-id="103d5-118">See also</span></span>

- [<span data-ttu-id="103d5-119">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="103d5-119">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="103d5-120">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="103d5-120">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
