---
title: DataGrid – ovládací prvek
ms.date: 03/30/2017
helpviewer_keywords:
- datasets [Windows Forms], user interface
- DataGrid control [Windows Forms]
- datasets [Windows Forms], displaying in DataGrid control
- displaying data [Windows Forms], on forms
- data [Windows Forms], displaying on Windows Forms
ms.assetid: 1d9d5683-43d2-42dd-b6c3-e43f4cf0de99
ms.openlocfilehash: efcc8770232f657c13135cefb4027f814d4d7d19
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76742516"
---
# <a name="datagrid-control-windows-forms"></a><span data-ttu-id="23894-102">DataGrid – ovládací prvek (Windows Forms)</span><span class="sxs-lookup"><span data-stu-id="23894-102">DataGrid Control (Windows Forms)</span></span>
> [!NOTE]
> <span data-ttu-id="23894-103">Ovládací prvek <xref:System.Windows.Forms.DataGridView> nahrazuje a přidává funkce do ovládacího prvku `DataGrid`; Nicméně ovládací prvek `DataGrid` se zachovává pro zpětnou kompatibilitu i pro budoucí použití, pokud zvolíte.</span><span class="sxs-lookup"><span data-stu-id="23894-103">The <xref:System.Windows.Forms.DataGridView> control replaces and adds functionality to the `DataGrid` control; however, the `DataGrid` control is retained for both backward compatibility and future use, if you choose.</span></span> <span data-ttu-id="23894-104">Další informace naleznete v tématu [rozdíly mezi ovládacími prvky model Windows Forms DataGridView a DataGrid](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span><span class="sxs-lookup"><span data-stu-id="23894-104">For more information, see [Differences Between the Windows Forms DataGridView and DataGrid Controls](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md).</span></span>  
  
 <span data-ttu-id="23894-105">Ovládací prvek model Windows Forms `DataGrid` poskytuje uživatelské rozhraní pro ADO.NET datových sad, zobrazení tabulkových dat a povolení aktualizací zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="23894-105">The Windows Forms `DataGrid` control provides a user interface to ADO.NET datasets, displaying tabular data and enabling updates to the data source.</span></span>  
  
 <span data-ttu-id="23894-106">Když je ovládací prvek `DataGrid` nastaven na platný zdroj dat, ovládací prvek se vyplní automaticky a vytvoří sloupce a řádky založené na tvaru dat.</span><span class="sxs-lookup"><span data-stu-id="23894-106">When the `DataGrid` control is set to a valid data source, the control is automatically populated, creating columns and rows based on the shape of the data.</span></span> <span data-ttu-id="23894-107">Ovládací prvek `DataGrid` lze použít k zobrazení jedné tabulky nebo hierarchických vztahů mezi sadou tabulek.</span><span class="sxs-lookup"><span data-stu-id="23894-107">The `DataGrid` control can be used to display either a single table or the hierarchical relationships between a set of tables.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="23894-108">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="23894-108">In This Section</span></span>  
 [<span data-ttu-id="23894-109">Přehled ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-109">DataGrid Control Overview</span></span>](datagrid-control-overview-windows-forms.md)  
 <span data-ttu-id="23894-110">Popisuje základní funkce ovládacího prvku `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="23894-110">Describes the basic features of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="23894-111">Postupy: Přidávání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="23894-111">How to: Add Tables and Columns to the Windows Forms DataGrid Control Using the Designer</span></span>](add-tables-and-columns-to-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="23894-112">Popisuje, jak přidat tabulky a sloupce do ovládacího prvku `DataGrid` pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="23894-112">Describes how to add tables and columns to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="23894-113">Postupy: Přidání tabulek a sloupců do ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-113">How to: Add Tables and Columns to the Windows Forms DataGrid Control</span></span>](how-to-add-tables-and-columns-to-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="23894-114">Popisuje, jak přidat tabulky a sloupce do ovládacího prvku `DataGrid` programově.</span><span class="sxs-lookup"><span data-stu-id="23894-114">Describes how to add tables and columns to the `DataGrid` control programmatically.</span></span>  
  
 [<span data-ttu-id="23894-115">Postupy: Vytvoření vazby ovládacího prvku Windows Forms DataGrid ke zdroji dat pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="23894-115">How to: Bind the Windows Forms DataGrid Control to a Data Source Using the Designer</span></span>](bind-wf-datagrid-control-to-a-data-source-using-the-designer.md)  
 <span data-ttu-id="23894-116">Popisuje, jak vytvořit datovou sadu ADO.NET k ovládacímu prvku `DataGrid` pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="23894-116">Describes how to bind an ADO.NET dataset to the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="23894-117">Postupy: Vázání ovládacího prvku Windows Forms DataGrid ke zdroji dat</span><span class="sxs-lookup"><span data-stu-id="23894-117">How to: Bind the Windows Forms DataGrid Control to a Data Source</span></span>](how-to-bind-the-windows-forms-datagrid-control-to-a-data-source.md)  
 <span data-ttu-id="23894-118">Popisuje, jak vytvořit datovou sadu ADO.NET s ovládacím prvkem `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="23894-118">Describes how to bind an ADO.NET dataset to the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="23894-119">Postupy: Změna zobrazených dat za běhu v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-119">How to: Change Displayed Data at Run Time in the Windows Forms DataGrid Control</span></span>](change-displayed-data-at-run-time-wf-datagrid-control.md)  
 <span data-ttu-id="23894-120">Popisuje, jak programově změnit data v ovládacím prvku `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="23894-120">Describes how to change data programmatically in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="23894-121">Postupy: Vytváření hlavních-podrobných seznamů pomocí ovládacího prvku Windows Forms DataGrid pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="23894-121">How to: Create Master-Details Lists with the Windows Forms DataGrid Control Using the Designer</span></span>](create-master-details-lists-with-wf-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="23894-122">Popisuje způsob zobrazení dvou tabulek, které jsou spojeny s relací nadřazený/podřízený ve dvou samostatných `DataGrid` ovládacích prvcích pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="23894-122">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls using the designer.</span></span>  
  
 <span data-ttu-id="23894-123">Postupy: vytváření seznamů hlavní-podrobnosti pomocí ovládacího prvku model Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-123">How to: Create Master-Details Lists with the Windows Forms DataGrid Control</span></span>  
 <span data-ttu-id="23894-124">V této části najdete popis postupu zobrazení dvou tabulek, které jsou spojeny s relací nadřazený/podřízený ve dvou samostatných ovládacích prvcích `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="23894-124">Describes how to display two tables, tied together with a parent/child relationship, in two separate `DataGrid` controls.</span></span>  
  
 [<span data-ttu-id="23894-125">Postupy: Odstranění či skrytí sloupců v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-125">How to: Delete or Hide Columns in the Windows Forms DataGrid Control</span></span>](how-to-delete-or-hide-columns-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="23894-126">Popisuje, jak odebrat sloupce v ovládacím prvku `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="23894-126">Describes how to remove columns in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="23894-127">Postupy: Formátování ovládacího prvku Windows Forms DataGrid pomocí Návrháře</span><span class="sxs-lookup"><span data-stu-id="23894-127">How to: Format the Windows Forms DataGrid Control Using the Designer</span></span>](how-to-format-the-windows-forms-datagrid-control-using-the-designer.md)  
 <span data-ttu-id="23894-128">Popisuje, jak změnit vlastnosti ovládacího prvku `DataGrid` související s vzhledy pomocí návrháře.</span><span class="sxs-lookup"><span data-stu-id="23894-128">Describes how to change the appearance-related properties of the `DataGrid` control using the designer.</span></span>  
  
 [<span data-ttu-id="23894-129">Postupy: Formátování ovládacího prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-129">How to: Format the Windows Forms DataGrid Control</span></span>](how-to-format-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="23894-130">Popisuje, jak změnit vlastnosti ovládacího prvku `DataGrid` týkající se vzhledu.</span><span class="sxs-lookup"><span data-stu-id="23894-130">Describes how to change the appearance-related properties of the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="23894-131">Klávesové zkratky pro ovládací prvek Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-131">Keyboard Shortcuts for the Windows Forms DataGrid Control</span></span>](keyboard-shortcuts-for-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="23894-132">Seznam klávesových zkratek pro navigaci pomocí ovládacího prvku `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="23894-132">Lists shortcuts for navigating through the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="23894-133">Postupy: Reakce na kliknutí v ovládacím prvku Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-133">How to: Respond to Clicks in the Windows Forms DataGrid Control</span></span>](how-to-respond-to-clicks-in-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="23894-134">Popisuje, jak určit, na kterou buňku uživatel kliknul v ovládacím prvku `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="23894-134">Describes how to determine which cell a user has clicked in the `DataGrid` control.</span></span>  
  
 [<span data-ttu-id="23894-135">Postupy: Ověřování vstupu s ovládacím prvkem Windows Forms DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-135">How to: Validate Input with the Windows Forms DataGrid Control</span></span>](how-to-validate-input-with-the-windows-forms-datagrid-control.md)  
 <span data-ttu-id="23894-136">Popisuje, jak ověřit vstup v datové sadě svázané s ovládacím prvkem `DataGrid`.</span><span class="sxs-lookup"><span data-stu-id="23894-136">Describes how to validate input in the dataset bound to the `DataGrid` control.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="23894-137">Referenční informace</span><span class="sxs-lookup"><span data-stu-id="23894-137">Reference</span></span>  
 <xref:System.Windows.Forms.DataGrid>  
 <span data-ttu-id="23894-138">Poskytuje přehled <xref:System.Windows.Forms.DataGrid> třídy.</span><span class="sxs-lookup"><span data-stu-id="23894-138">Provides an overview of the <xref:System.Windows.Forms.DataGrid> class.</span></span>  
  
 <xref:System.Windows.Forms.DataGrid.DataSource%2A>  
 <span data-ttu-id="23894-139">Poskytuje podrobnosti o použití této vlastnosti pro svázání ovládacího prvku <xref:System.Windows.Forms.DataGrid> s daty.</span><span class="sxs-lookup"><span data-stu-id="23894-139">Provides details about using this property to bind the <xref:System.Windows.Forms.DataGrid> control to data.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="23894-140">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="23894-140">Related Sections</span></span>  
 [<span data-ttu-id="23894-141">Windows Forms – datová vazba</span><span class="sxs-lookup"><span data-stu-id="23894-141">Windows Forms Data Binding</span></span>](../windows-forms-data-binding.md)  
 <span data-ttu-id="23894-142">Obsahuje odkazy na témata týkající se datových vazeb v model Windows Forms.</span><span class="sxs-lookup"><span data-stu-id="23894-142">Provides links to topics on data binding in Windows Forms.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="23894-143">Viz také</span><span class="sxs-lookup"><span data-stu-id="23894-143">See also</span></span>

- [<span data-ttu-id="23894-144">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="23894-144">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="23894-145">Rozdíly mezi ovládacími prvky Windows Forms DataGridView a DataGrid</span><span class="sxs-lookup"><span data-stu-id="23894-145">Differences Between the Windows Forms DataGridView and DataGrid Controls</span></span>](differences-between-the-windows-forms-datagridview-and-datagrid-controls.md)
