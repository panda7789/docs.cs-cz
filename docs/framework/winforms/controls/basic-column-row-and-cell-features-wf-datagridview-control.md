---
title: Základní funkce sloupce, řádku a buňky v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
ms.openlocfilehash: 02f8ad7e11a61e9434748a8b3b2f853f98b013d1
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76746228"
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="28bec-102">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="28bec-103">Nastavení jednoduchých vlastností může upravit mnoho základních chování `DataGridView` buněk, řádků a sloupců.</span><span class="sxs-lookup"><span data-stu-id="28bec-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="28bec-104">Témata v této části popisují některé z nejčastěji používaných funkcí.</span><span class="sxs-lookup"><span data-stu-id="28bec-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="28bec-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="28bec-105">In This Section</span></span>  
 [<span data-ttu-id="28bec-106">Postupy: Skrytí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="28bec-107">Popisuje, jak zabránit zobrazení určitých sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="28bec-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="28bec-108">Postupy: Skrytí záhlaví sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="28bec-109">Popisuje, jak zabránit zobrazení záhlaví sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="28bec-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="28bec-110">Postupy: Povolení změny pořadí v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="28bec-111">Popisuje, jak uživatelům umožnit změnu uspořádání sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="28bec-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="28bec-112">Postupy: Zablokování sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="28bec-113">Popisuje, jak zabránit posouvání jednoho nebo více sousedících sloupců.</span><span class="sxs-lookup"><span data-stu-id="28bec-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="28bec-114">Postupy: Přepnutí sloupců do režimu jen pro čtení v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="28bec-115">Popisuje, jak zabránit uživatelům v úpravách konkrétních sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="28bec-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="28bec-116">Postupy: Zamezení přidávání a odstraňování řádků v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="28bec-117">Popisuje, jak odebrat řádek pro nové záznamy v dolní části ovládacího prvku a zabránit tak uživatelům v přidávání řádků.</span><span class="sxs-lookup"><span data-stu-id="28bec-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="28bec-118">Popisuje také, jak zabránit uživatelům v odstraňování řádků.</span><span class="sxs-lookup"><span data-stu-id="28bec-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="28bec-119">Postupy: Získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="28bec-120">Popisuje, jak získat přístup k buňce, která aktuálně má fokus v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="28bec-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="28bec-121">Postupy: Zobrazení obrázků v buňkách ovládacího prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="28bec-122">Popisuje, jak vytvořit sloupec obrázku, který v každé buňce zobrazuje ikonu.</span><span class="sxs-lookup"><span data-stu-id="28bec-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="28bec-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="28bec-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="28bec-124">Poskytuje referenční dokumentaci k ovládacímu prvku.</span><span class="sxs-lookup"><span data-stu-id="28bec-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="28bec-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="28bec-125">Related Sections</span></span>  
 [<span data-ttu-id="28bec-126">Základní formátování a práce se styly v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="28bec-127">Poskytuje témata, které popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat buněk.</span><span class="sxs-lookup"><span data-stu-id="28bec-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="28bec-128">Programování s buňkami, řádky a sloupci v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="28bec-129">Poskytuje témata, která popisují, jak programovat s objekty buňky, řádku a sloupce.</span><span class="sxs-lookup"><span data-stu-id="28bec-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="28bec-130">Viz také:</span><span class="sxs-lookup"><span data-stu-id="28bec-130">See also</span></span>

- [<span data-ttu-id="28bec-131">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-131">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="28bec-132">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="28bec-132">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
