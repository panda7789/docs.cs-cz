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
ms.openlocfilehash: f50f32ad65dd621dee3847d72b5a186afcc4a86d
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69969156"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="fa208-102">DataGrid – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="fa208-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="fa208-103">Ovládací prvek nahrazuje a přidává funkce `DataGrid` `DataGrid` ovládacímu prvku. ovládací prvek je však ponechán pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte. <xref:System.Windows.Forms.DataGridView></span><span class="sxs-lookup"><span data-stu-id="fa208-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="fa208-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="fa208-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="fa208-105">Ovládací prvek `DataGrid` model Windows Forms poskytuje uživatelské rozhraní pro ADO.NET datových sad, zobrazení tabulkových dat a povolení aktualizací zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="fa208-105">The Windows Forms `DataGrid` control provides a user interface to ADO.NET datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="fa208-106">Když je `DataGrid` ovládací prvek nastaven na platný zdroj dat, ovládací prvek se vyplní automaticky a vytvoří sloupce a řádky založené na tvaru dat.</span><span class="sxs-lookup"><span data-stu-id="fa208-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="fa208-107">`DataGrid` Ovládací prvek lze použít k zobrazení jedné tabulky nebo hierarchických vztahů mezi sadou tabulek.</span><span class="sxs-lookup"><span data-stu-id="fa208-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="fa208-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="fa208-108">In This Section</span></span>  
 [<span data-ttu-id="fa208-109">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="fa208-110">Popisuje základní funkce `DataGrid` ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fa208-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="fa208-111">Postupy: Přidání tabulek a sloupců do ovládacího prvku model Windows Forms DataGrid pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="fa208-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="fa208-112">Popisuje, jak přidat tabulky a sloupce do `DataGrid` ovládacího prvku pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="fa208-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="fa208-113">Postupy: Přidání tabulek a sloupců do model Windows Forms ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="fa208-114">Popisuje, jak přidat tabulky a sloupce do `DataGrid` ovládacího prvku programově.</span><span class="sxs-lookup"><span data-stu-id="fa208-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="fa208-115">Postupy: Svázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="fa208-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="fa208-116">Popisuje, jak vytvořit datovou sadu ADO.NET s `DataGrid` ovládacím prvkem pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="fa208-116">Describes how to bind an ADO.NET dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="fa208-117">Postupy: Navázání model Windows Forms ovládacího prvku DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="fa208-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="fa208-118">Popisuje, jak vytvořit datovou sadu ADO.NET s `DataGrid` ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="fa208-118">Describes how to bind an ADO.NET dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="fa208-119">Postupy: Změna zobrazených dat v době běhu v ovládacím prvku model Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="fa208-120">Popisuje, jak změnit data programově v `DataGrid` ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="fa208-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="fa208-121">Postupy: Vytvoření seznamu hlavní-podrobnosti s ovládacím prvkem model Windows Forms DataGrid pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="fa208-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="fa208-122">Popisuje způsob zobrazení dvou tabulek, které jsou spojeny s relací nadřazený/podřízený ve dvou samostatných `DataGrid` ovládacích prvcích pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="fa208-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="fa208-123">Postupy: Vytvoření seznamu hlavní-podrobnosti pomocí model Windows Forms ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="fa208-124">V této části najdete popis postupu zobrazení dvou tabulek, které jsou spojeny s relací nadřazený-podřízený `DataGrid` ve dvou samostatných ovládacích prvcích.</span><span class="sxs-lookup"><span data-stu-id="fa208-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="fa208-125">Postupy: Odstranění nebo skrytí sloupců v model Windows Forms ovládacím prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="fa208-126">Popisuje, jak odebrat sloupce v `DataGrid` ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="fa208-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="fa208-127">Postupy: Formátování ovládacího prvku DataGrid model Windows Forms pomocí návrháře</span><span class="sxs-lookup"><span data-stu-id="fa208-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="fa208-128">V této části najdete popis postupu změny vlastností `DataGrid` ovládacího prvku souvisejících s jeho vzhledy pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="fa208-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="fa208-129">Postupy: Formátování model Windows Forms ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="fa208-130">Popisuje, jak změnit vlastnosti `DataGrid` ovládacího prvku souvisejícího s jeho zobrazením.</span><span class="sxs-lookup"><span data-stu-id="fa208-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="fa208-131">Klávesové zkratky pro ovládací prvek Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="fa208-132">Seznam klávesových zkratek pro navigaci `DataGrid` prostřednictvím ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="fa208-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="fa208-133">Postupy: Reakce na kliknutí v ovládacím prvku DataGrid model Windows Forms</span><span class="sxs-lookup"><span data-stu-id="fa208-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="fa208-134">Popisuje, jak určit, na kterou buňku uživatel kliknul v `DataGrid` ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="fa208-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="fa208-135">Postupy: Ověření vstupu pomocí model Windows Forms ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="fa208-136">Popisuje, jak ověřit vstup v datové sadě svázané s `DataGrid` ovládacím prvkem.</span><span class="sxs-lookup"><span data-stu-id="fa208-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="fa208-137">Reference</span><span class="sxs-lookup"><span data-stu-id="fa208-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="fa208-138">Poskytuje přehled <xref:System.Windows.Forms.DataGrid> třídy.</span><span class="sxs-lookup"><span data-stu-id="fa208-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="fa208-139">Poskytuje podrobnosti o použití této vlastnosti k navázání <xref:System.Windows.Forms.DataGrid> ovládacího prvku na data.</span><span class="sxs-lookup"><span data-stu-id="fa208-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="fa208-140">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="fa208-140">Related Sections</span></span>  
 [<span data-ttu-id="fa208-141">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="fa208-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="fa208-142">Obsahuje odkazy na témata týkající se datových vazeb v model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="fa208-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="fa208-143">Viz také:</span><span class="sxs-lookup"><span data-stu-id="fa208-143">See also</span></span>

- [<span data-ttu-id="fa208-144">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="fa208-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="fa208-145">Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid</span><span class="sxs-lookup"><span data-stu-id="fa208-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
