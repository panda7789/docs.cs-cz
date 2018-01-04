---
title: "Zadávání dat v ovládacím prvku Windows Forms DataGridView"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-winforms
ms.tgt_pltfrm: 
ms.topic: article
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
caps.latest.revision: "11"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 399520738c53e149e7a5539a62a5d4599e26a8da
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="205e6-102">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="205e6-103">`DataGridView` Řízení poskytuje několik funkcí, která umožňují změnit jak uživatelé přidat nebo upravit dat v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="205e6-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="205e6-104">Například můžete nastavit zadávání dat efektivnější tím, že poskytuje výchozí hodnoty pro nové řádky a upozornění uživatelů při výskytu chyb.</span><span class="sxs-lookup"><span data-stu-id="205e6-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="205e6-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="205e6-105">In This Section</span></span>  
 [<span data-ttu-id="205e6-106">Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="205e6-107">Popisuje, jak změnit způsob uživatelé začít upravovat buňky.</span><span class="sxs-lookup"><span data-stu-id="205e6-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="205e6-108">Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="205e6-109">Popisuje, jak předem řádek pro nové záznamy ušetřit čas zadávání dat.</span><span class="sxs-lookup"><span data-stu-id="205e6-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="205e6-110">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="205e6-111">Popisuje řádek pro nové záznamy v podrobností, včetně informací o skrytí ho, k přizpůsobení její vzhled a na tom, jak souvisí se službou <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="205e6-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="205e6-112">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="205e6-113">Popisuje, jak k ověření vstupu uživatele, aby se zabránilo chybám při zadávání dat formátování.</span><span class="sxs-lookup"><span data-stu-id="205e6-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="205e6-114">Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="205e6-115">Popisuje, jak se budou zpracovávat chyby vkládání dat, které pocházejí ze zdroje dat, když se uživatel pokusí provést novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="205e6-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="205e6-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="205e6-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="205e6-117">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="205e6-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="205e6-118">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.EditMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="205e6-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="205e6-119">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.</span><span class="sxs-lookup"><span data-stu-id="205e6-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="205e6-120">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.DataError> událostí.</span><span class="sxs-lookup"><span data-stu-id="205e6-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="205e6-121">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.CellValidating> událostí.</span><span class="sxs-lookup"><span data-stu-id="205e6-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="205e6-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="205e6-122">Related Sections</span></span>  
 [<span data-ttu-id="205e6-123">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="205e6-124">Obsahuje témata, která popisují, jak ručně nebo z externího zdroje dat naplnit ovládací prvek s daty.</span><span class="sxs-lookup"><span data-stu-id="205e6-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="205e6-125">Viz také</span><span class="sxs-lookup"><span data-stu-id="205e6-125">See Also</span></span>  
 [<span data-ttu-id="205e6-126">Ovládací prvek DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-126">DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/datagridview-control-windows-forms.md)  
 [<span data-ttu-id="205e6-127">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="205e6-127">Column Types in the Windows Forms DataGridView Control</span></span>](../../../../docs/framework/winforms/controls/column-types-in-the-windows-forms-datagridview-control.md)
