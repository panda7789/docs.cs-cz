---
title: "DataGrid – ovládací prvek (Windows Forms)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
caps.latest.revision: "20"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: e0ad5ba4bdd283e411c746906adfed53282c55b9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="1e5c1-102">DataGrid – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="1e5c1-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="1e5c1-103"><xref:System.Windows.Forms.DataGridView> Řízení nahrazuje a přidá funkce `DataGrid` řízení; však `DataGrid` řízení se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud si zvolíte.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="1e5c1-104">Další informace najdete v tématu [rozdíly mezi systému Windows Forms DataGridView a DataGrid – ovládací prvky](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="1e5c1-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="1e5c1-105">Windows Forms `DataGrid` poskytuje uživatelské rozhraní pro řízení [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] aktualizací softwaru ke zdroji dat datové sady, zobrazení tabulková data a povolení.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-105">The Windows Forms `DataGrid` control provides a user interface to [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="1e5c1-106">Když `DataGrid` řízení je nastavené na platný zdroj dat, je ovládací prvek automaticky vyplněno, vytváření sloupců a řádků v závislosti na obrazec data.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="1e5c1-107">`DataGrid` Řízení lze zobrazit jednu tabulku nebo hierarchické vztahy mezi sadu tabulek.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="1e5c1-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="1e5c1-108">In This Section</span></span>  
 [<span data-ttu-id="1e5c1-109">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-109">DataGrid Control Overview</span></span>](../../../../docs/framework/winforms/controls/datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="1e5c1-110">Popisuje základní funkce `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="1e5c1-111">Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="1e5c1-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="1e5c1-112">Popisuje postup přidání tabulek a sloupců `DataGrid` řídit pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="1e5c1-113">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="1e5c1-114">Popisuje postup přidání tabulek a sloupců `DataGrid` řídit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="1e5c1-115">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="1e5c1-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](../../../../docs/framework/winforms/controls/bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="1e5c1-116">Popisuje, jak vytvořit vazbu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datovou sadu, která `DataGrid` řídit pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-116">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="1e5c1-117">Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="1e5c1-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](../../../../docs/framework/winforms/controls/how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="1e5c1-118">Popisuje, jak vytvořit vazbu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datovou sadu, která `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-118">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="1e5c1-119">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="1e5c1-120">Popisuje, jak změnit data prostřednictvím kódu programu v `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="1e5c1-121">Postupy: Vytváření hlavních-podrobných seznamů pomocí ovládacího prvku Windows Forms DataGrid pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="1e5c1-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="1e5c1-122">Popisuje způsob zobrazení dvou tabulek, svázané společně s relaci nadřazený podřízený, ve dvou samostatných `DataGrid` ovládací prvky pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="1e5c1-123">Postupy: vytváření hlavních podrobných seznamů s ovládacím prvkem Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="1e5c1-124">Popisuje způsob zobrazení dvou tabulek, svázané společně s relaci nadřazený podřízený, ve dvou samostatných `DataGrid` ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="1e5c1-125">Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="1e5c1-126">Popisuje postup odstranění sloupců v `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="1e5c1-127">Postupy: Formátování ovládacího prvku Windows Forms DataGrid pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="1e5c1-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="1e5c1-128">Popisuje, jak změnit vlastnosti týkající se vzhledu `DataGrid` řízení pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="1e5c1-129">Postupy: Formátování ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-129">How to: Format the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="1e5c1-130">Popisuje, jak změnit vlastnosti týkající se vzhledu `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="1e5c1-131">Klávesové zkratky pro ovládací prvek Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="1e5c1-132">Obsahuje seznam zástupců pro procházení `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="1e5c1-133">Postupy: Reakce na kliknutí v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="1e5c1-134">Popisuje, jak určit, které buňky a uživatel klikne v `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="1e5c1-135">Postupy: Ověřování vstupu s ovládacím prvkem Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](../../../../docs/framework/winforms/controls/how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="1e5c1-136">Popisuje, jak k ověření vstupu v datové sadě vázána `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="1e5c1-137">Odkaz</span><span class="sxs-lookup"><span data-stu-id="1e5c1-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="1e5c1-138">Obsahuje přehled <xref:System.Windows.Forms.DataGrid> třídy.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="1e5c1-139">Obsahuje podrobné informace o používání této vlastnosti se vytvořit vazbu <xref:System.Windows.Forms.DataGrid> řízení k datům.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="1e5c1-140">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="1e5c1-140">Related Sections</span></span>  
 [<span data-ttu-id="1e5c1-141">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="1e5c1-141">Windows Forms Data Binding</span></span>](../../../../docs/framework/winforms/windows-forms-data-binding.md)  
 <span data-ttu-id="1e5c1-142">Obsahuje odkazy na témata o datové vazby v systému Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="1e5c1-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="1e5c1-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="1e5c1-143">See Also</span></span>  
 [<span data-ttu-id="1e5c1-144">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="1e5c1-144">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="1e5c1-145">Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid</span><span class="sxs-lookup"><span data-stu-id="1e5c1-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](../../../../docs/framework/winforms/controls/differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
