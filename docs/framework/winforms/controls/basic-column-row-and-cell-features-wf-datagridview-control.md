---
title: "Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], basic features
- columns [Windows Forms], DataGridView control
- data grids [Windows Forms], examples
- DataGridView control [Windows Forms], examples
ms.assetid: 78085f26-d5d2-4b75-813e-e932b72fd06f
caps.latest.revision: "12"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: eebd0f36fbf1bf3bfc37b8fa836d318a9b8ac007
ms.sourcegitcommit: 4f3fef493080a43e70e951223894768d36ce430a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/21/2017
---
# <a name="basic-column-row-and-cell-features-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="1329e-102">Základní funkce sloupce, řádku a buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1329e-102">Basic Column, Row, and Cell Features in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="1329e-103">Mnoho základní chování `DataGridView` buněk, řádků a sloupců může měnit nastavení jedné vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="1329e-103">Many basic behaviors of `DataGridView` cells, rows, and columns can be modified by setting single properties.</span></span> <span data-ttu-id="1329e-104">Témata v této části popisují některé z nejčastěji používaných těchto funkcí.</span><span class="sxs-lookup"><span data-stu-id="1329e-104">The topics in this section describe several of the most commonly used of these features.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1329e-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1329e-105">In This Section</span></span>  
 [<span data-ttu-id="1329e-106">Postupy: skrytí sloupců v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1329e-106">How to: Hide Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1329e-107">Popisuje, jak zabránit zobrazování v ovládacím prvku určité sloupce.</span><span class="sxs-lookup"><span data-stu-id="1329e-107">Describes how to prevent specific columns from appearing in the control.</span></span>  
  
 [<span data-ttu-id="1329e-108">Postupy: skrytí záhlaví sloupců v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1329e-108">How to: Hide Column Headers in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-hide-column-headers-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1329e-109">Popisuje, jak zabránit zobrazování v ovládacím prvku záhlaví sloupců.</span><span class="sxs-lookup"><span data-stu-id="1329e-109">Describes how to prevent the column headers from appearing in the control.</span></span>  
  
 [<span data-ttu-id="1329e-110">Postupy: povolení změny pořadí sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1329e-110">How to: Enable Column Reordering in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-enable-column-reordering-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1329e-111">Popisuje, jak povolit uživatelům změnit uspořádání sloupců v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="1329e-111">Describes how to enable users to rearrange columns in the control.</span></span>  
  
 [<span data-ttu-id="1329e-112">Postupy: zablokování sloupců v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1329e-112">How to: Freeze Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-freeze-columns-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1329e-113">Popisuje, jak jeden nebo více sloupců sousedících zabránit posouvání.</span><span class="sxs-lookup"><span data-stu-id="1329e-113">Describes how prevent one or more adjacent columns from scrolling.</span></span>  
  
 [<span data-ttu-id="1329e-114">Postupy: přepnutí sloupců jen pro čtení v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1329e-114">How to: Make Columns Read-Only in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-make-columns-read-only-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1329e-115">Popisuje, jak uživatelům zabránit v úpravy určité sloupce v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="1329e-115">Describes how to prevent users from editing specific columns in the control.</span></span>  
  
 [<span data-ttu-id="1329e-116">Postupy: zabránění řádek přidání a odstranění ve Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1329e-116">How to: Prevent Row Addition and Deletion in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/prevent-row-addition-and-deletion-datagridview.md)  
 <span data-ttu-id="1329e-117">Popisuje postup odstranění řádků pro nové záznamy v dolní části ovládacího prvku zabránit uživatelům v přidávání řádků.</span><span class="sxs-lookup"><span data-stu-id="1329e-117">Describes how to remove the row for new records at the bottom of the control to prevent users from adding rows.</span></span> <span data-ttu-id="1329e-118">Také popisuje, jak uživatelům zabránit v odstranění řádků.</span><span class="sxs-lookup"><span data-stu-id="1329e-118">Also describes how to prevent users from deleting rows.</span></span>  
  
 [<span data-ttu-id="1329e-119">Postupy: získání a nastavení aktuální buňky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1329e-119">How to: Get and Set the Current Cell in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/get-and-set-the-current-cell-wf-datagridview-control.md)  
 <span data-ttu-id="1329e-120">Popisuje, jak pro přístup k buňku, která má právě fokus v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="1329e-120">Describes how to access the cell that currently has focus in the control.</span></span>  
  
 [<span data-ttu-id="1329e-121">Postupy: zobrazení obrázků v buňkách Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1329e-121">How to: Display Images in Cells of the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-display-images-in-cells-of-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1329e-122">Popisuje postup vytvoření sloupec bitové kopie, který zobrazuje ikonu v každé buňce.</span><span class="sxs-lookup"><span data-stu-id="1329e-122">Describes how to create an image column that displays an icon in every cell.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1329e-123">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1329e-123">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="1329e-124">Poskytuje referenční dokumentaci k nástroji pro ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="1329e-124">Provides reference documentation for the control.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1329e-125">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1329e-125">Related Sections</span></span>  
 [<span data-ttu-id="1329e-126">Základní formátování a styly v systému Windows Forms DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1329e-126">Basic Formatting and Styling in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/basic-formatting-and-styling-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="1329e-127">Obsahuje témata, která popisují, jak upravit základní vzhled ovládacího prvku a formátování zobrazení dat v buňce.</span><span class="sxs-lookup"><span data-stu-id="1329e-127">Provides topics that describe how to modify the basic appearance of the control and the display formatting of cell data.</span></span>  
  
 [<span data-ttu-id="1329e-128">Programování s buněk, řádků a sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1329e-128">Programming with Cells, Rows, and Columns in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/programming-with-cells-rows-and-columns-in-the-datagrid.md)  
 <span data-ttu-id="1329e-129">Obsahuje témata, která popisují, jak programovat s buněk, řádků a sloupec objekty.</span><span class="sxs-lookup"><span data-stu-id="1329e-129">Provides topics that describe how to program with cell, row, and column objects.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1329e-130">Viz také</span><span class="sxs-lookup"><span data-stu-id="1329e-130">See Also</span></span>  
 [<span data-ttu-id="1329e-131">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="1329e-131">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="1329e-132">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="1329e-132">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
