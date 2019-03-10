---
title: Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
ms.openlocfilehash: ed98c277661b141eaef2472b717ea595ca918b6a
ms.sourcegitcommit: 160a88c8087b0e63606e6e35f9bd57fa5f69c168
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/09/2019
ms.locfileid: "57706364"
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="09c99-102">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="09c99-103">Mnoho základní chování `DataGridView` buněk, řádků a sloupců je možné upravovat prostřednictvím jedné vlastnosti nastavení.</span><span class="sxs-lookup"><span data-stu-id="09c99-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="09c99-104">Témata v této části popisují některé z nejčastěji používaných z těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="09c99-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="09c99-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="09c99-105">In This Section</span></span>  
 [<span data-ttu-id="09c99-106">Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="09c99-107">Popisuje, jak zabránit určité sloupce v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="09c99-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="09c99-108">Postupy: Skrytí záhlaví sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="09c99-109">Popisuje, jak zabránit záhlaví sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="09c99-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="09c99-110">Postupy: Povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="09c99-111">Popisuje, jak povolit uživatelům změnit uspořádání sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="09c99-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="09c99-112">Postupy: Ukotvit sloupce v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="09c99-113">Popisuje, jak zabránit v jedné nebo více sousedící sloupce posouvání.</span><span class="sxs-lookup"><span data-stu-id="09c99-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="09c99-114">Postupy: Nastavení sloupců jen pro čtení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="09c99-115">Popisuje, jak zabránit uživatelům v úpravách určitými sloupci v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="09c99-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="09c99-116">Postupy: Zabránit řádku přidání a odstranění v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="09c99-117">Popisuje postup odstranění řádku pro nové záznamy v dolní části ovládacího prvku na zabrání uživatelům přidávat řádky.</span><span class="sxs-lookup"><span data-stu-id="09c99-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="09c99-118">Také popisuje, jak uživatelům zabránit v odstranění řádků.</span><span class="sxs-lookup"><span data-stu-id="09c99-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="09c99-119">Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="09c99-120">Popisuje, jak získat přístup k na buňku, která má právě fokus v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="09c99-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="09c99-121">Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="09c99-122">Popisuje, jak vytvořit image sloupec, který zobrazuje ikony v každé buňce.</span><span class="sxs-lookup"><span data-stu-id="09c99-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="09c99-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="09c99-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="09c99-124">Poskytuje referenční dokumentaci pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="09c99-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="09c99-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="09c99-125">Related Sections</span></span>  
 [<span data-ttu-id="09c99-126">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="09c99-127">Obsahuje témata, které popisují, jak změnit základní vzhled ovládacího prvku a formátování zobrazení dat v buňce.</span><span class="sxs-lookup"><span data-stu-id="09c99-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="09c99-128">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="09c99-129">Obsahuje témata, které popisují, jak programovat s buňky, řádku a sloupci objekty.</span><span class="sxs-lookup"><span data-stu-id="09c99-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="09c99-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="09c99-130">See also</span></span>
- [<span data-ttu-id="09c99-131">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="09c99-132">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="09c99-132">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
