---
title: Zadávání dat v ovládacím prvku DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
ms.openlocfilehash: e95095624f45cc1507735083a87293730e9133e9
ms.sourcegitcommit: de17a7a0a37042f0d4406f5ae5393531caeb25ba
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 01/24/2020
ms.locfileid: "76743997"
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="9289d-102">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="9289d-103">Ovládací prvek `DataGridView` poskytuje několik funkcí, které umožňují změnit způsob, jakým uživatelé přidávají nebo upravují data v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="9289d-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="9289d-104">Například můžete zvýšit efektivitu zadávání dat tím, že poskytnete výchozí hodnoty pro nové řádky a upozorníte uživatele, když dojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="9289d-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="9289d-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="9289d-105">In This Section</span></span>  
 [<span data-ttu-id="9289d-106">Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9289d-107">Popisuje, jak lze změnit způsob, jakým uživatelé začnou upravovat buňky.</span><span class="sxs-lookup"><span data-stu-id="9289d-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="9289d-108">Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="9289d-109">Popisuje, jak předvyplnit řádek pro nové záznamy pro uložení času zadávání dat.</span><span class="sxs-lookup"><span data-stu-id="9289d-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="9289d-110">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9289d-111">Popisuje řádek pro nové záznamy podrobně, včetně informací o jejich skrývání, přizpůsobení jejího vzhledu a způsobu, jak souvisí s kolekcí <xref:System.Windows.Forms.DataGridView.Rows%2A>.</span><span class="sxs-lookup"><span data-stu-id="9289d-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="9289d-112">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9289d-113">Popisuje ověření vstupu uživatele, aby nedocházelo k chybám při formátování datových položek.</span><span class="sxs-lookup"><span data-stu-id="9289d-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="9289d-114">Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="9289d-115">Popisuje způsob zpracování chyb při zadávání dat, které pocházejí ze zdroje dat, když se uživatel pokusí o potvrzení nové hodnoty.</span><span class="sxs-lookup"><span data-stu-id="9289d-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="9289d-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="9289d-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="9289d-117">Poskytuje referenční dokumentaci pro ovládací prvek <xref:System.Windows.Forms.DataGridView>.</span><span class="sxs-lookup"><span data-stu-id="9289d-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="9289d-118">Poskytuje referenční dokumentaci pro vlastnost <xref:System.Windows.Forms.DataGridView.EditMode%2A>.</span><span class="sxs-lookup"><span data-stu-id="9289d-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="9289d-119">Poskytuje referenční dokumentaci pro událost <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded>.</span><span class="sxs-lookup"><span data-stu-id="9289d-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="9289d-120">Poskytuje referenční dokumentaci pro událost <xref:System.Windows.Forms.DataGridView.DataError>.</span><span class="sxs-lookup"><span data-stu-id="9289d-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="9289d-121">Poskytuje referenční dokumentaci pro událost <xref:System.Windows.Forms.DataGridView.CellValidating>.</span><span class="sxs-lookup"><span data-stu-id="9289d-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="9289d-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="9289d-122">Related Sections</span></span>  
 [<span data-ttu-id="9289d-123">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="9289d-124">Poskytuje témata, která popisují, jak naplnit ovládací prvek daty buď ručně, nebo z externího zdroje dat.</span><span class="sxs-lookup"><span data-stu-id="9289d-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="9289d-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="9289d-125">See also</span></span>

- [<span data-ttu-id="9289d-126">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-126">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="9289d-127">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="9289d-127">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
