---
title: DataGrid – ovládací prvek (Windows Forms)
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: 5f8fcd21802c52d61d354c5ba85d665bd17237db
ms.sourcegitcommit: 0be8a279af6d8a43e03141e349d3efd5d35f8767
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/18/2019
ms.locfileid: "59078912"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="94497-102">DataGrid – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="94497-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
>  <span data-ttu-id="94497-103"><xref:System.Windows.Forms.DataGridView> Ovládací prvek nahradí a přidá funkce, které `DataGrid` řízení; však `DataGrid` ovládací prvek se zachovává kvůli zpětné kompatibilitě a budoucí použití, pokud se rozhodnete.</span><span class="sxs-lookup"><span data-stu-id="94497-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="94497-104">Další informace najdete v tématu [rozdíly mezi Windows Forms DataGridView a DataGrid – ovládací prvky](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="94497-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="94497-105">Windows Forms `DataGrid` řízení poskytuje uživatelské rozhraní pro [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] aktualizace datové sady, zobrazení tabulkových dat a povolení ke zdroji dat.</span><span class="sxs-lookup"><span data-stu-id="94497-105">The Windows Forms `DataGrid` control provides a user interface to [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="94497-106">Když `DataGrid` řízení je nastavené na platný zdroj dat, ovládací prvek se vyplní automaticky, vytváření sloupců a řádků v závislosti na struktuře dat.</span><span class="sxs-lookup"><span data-stu-id="94497-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="94497-107">`DataGrid` Ovládací prvek lze použít k zobrazení jedné tabulky nebo hierarchické vztahy mezi sadou tabulek.</span><span class="sxs-lookup"><span data-stu-id="94497-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="94497-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="94497-108">In This Section</span></span>  
 [<span data-ttu-id="94497-109">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="94497-110">Popisuje základní funkce `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94497-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="94497-111">Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="94497-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="94497-112">Popisuje postup přidání tabulky a sloupce, které chcete `DataGrid` řídit pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="94497-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="94497-113">Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="94497-114">Popisuje postup přidání tabulky a sloupce, které chcete `DataGrid` řídit prostřednictvím kódu programu.</span><span class="sxs-lookup"><span data-stu-id="94497-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="94497-115">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="94497-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="94497-116">Popisuje, jak vytvořit vazbu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datovou sadu, která `DataGrid` řídit pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="94497-116">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="94497-117">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="94497-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="94497-118">Popisuje, jak vytvořit vazbu [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] datovou sadu, která `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94497-118">Describes how to bind an [!INCLUDE[vstecado](../../../../includes/vstecado-md.md)] dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="94497-119">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="94497-120">Popisuje, jak změnit dat prostřednictvím kódu programu v `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94497-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="94497-121">Postupy: Vytváření hlavních podrobných seznamů pomocí ovládacího prvku Windows Forms DataGrid pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="94497-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="94497-122">Popisuje způsob zobrazení dvou tabulek, vázané nadřazené a podřízené relací, dva samostatné `DataGrid` ovládací prvky pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="94497-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="94497-123">Postupy: Vytváření hlavních podrobných seznamů pomocí ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="94497-124">Popisuje způsob zobrazení dvou tabulek, vázané nadřazené a podřízené relací, dva samostatné `DataGrid` ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="94497-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="94497-125">Postupy: Odstranit nebo skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="94497-126">Popisuje, jak odebrat sloupce v `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94497-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="94497-127">Postupy: Formátování v ovládacím prvku Windows Forms DataGrid pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="94497-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="94497-128">Popisuje, jak změnit vzhled související vlastnosti `DataGrid` řídit pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="94497-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="94497-129">Postupy: Formátování ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="94497-130">Popisuje, jak změnit vzhled související vlastnosti `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94497-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="94497-131">Klávesové zkratky pro ovládací prvek Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="94497-132">Uvádí klávesové zkratky pro navigaci `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94497-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="94497-133">Postupy: Reakce na kliknutí v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="94497-134">Popisuje, jak určit, která buňka uživatel klikne v `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94497-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="94497-135">Postupy: Ověřování vstupu s ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="94497-136">Popisuje, jak ověřit vstup v datové sadě vázán na `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="94497-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="94497-137">Odkaz</span><span class="sxs-lookup"><span data-stu-id="94497-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="94497-138">Najdete zde přehled <xref:System.Windows.Forms.DataGrid> třídy.</span><span class="sxs-lookup"><span data-stu-id="94497-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="94497-139">Poskytuje podrobnosti o použití této vlastnosti se vytvořit vazbu <xref:System.Windows.Forms.DataGrid> ovládacího prvku k datům.</span><span class="sxs-lookup"><span data-stu-id="94497-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="94497-140">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="94497-140">Related Sections</span></span>  
 [<span data-ttu-id="94497-141">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="94497-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="94497-142">Obsahuje odkazy na témata o datové vazby v modelu Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="94497-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="94497-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="94497-143">See also</span></span>

- [<span data-ttu-id="94497-144">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="94497-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="94497-145">Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid</span><span class="sxs-lookup"><span data-stu-id="94497-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
