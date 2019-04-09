---
title: Zadávání dat v ovládacím prvku Windows Forms DataGridView
ms.date: 03/30/2017
helpviewer_keywords:
- DataGridView control [Windows Forms], data entry
- data entry [Windows Forms], dataGridView control
- data grids [Windows Forms], data entry
ms.assetid: 4a6d4676-d4e7-4b0e-9c22-50ce65ffe0d6
ms.openlocfilehash: 3ebfcaaf22ca632e5784dc1f01a351583e78e865
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59090703"
---
# <a name="data-entry-in-the-windows-forms-datagridview-control"></a><span data-ttu-id="82766-102">Zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="82766-102">Data Entry in the Windows Forms DataGridView Control</span></span>
<span data-ttu-id="82766-103">`DataGridView` Ovládacího prvku poskytuje několik funkcí, které umožňují změnit jak uživatelé přidávat nebo upravovat data v ovládacím prvku.</span><span class="sxs-lookup"><span data-stu-id="82766-103">The `DataGridView` control provides several features that let you change how users add or modify data in the control.</span></span> <span data-ttu-id="82766-104">Například můžete provést zadávání dat efektivnější tím, že poskytuje výchozí hodnoty pro nové řádky a upozorňování uživatelů, když dojde k chybám.</span><span class="sxs-lookup"><span data-stu-id="82766-104">For example, you can make data entry more efficient by providing default values for new rows and by alerting users when errors occur.</span></span>  
  
## <a name="in-this-section"></a><span data-ttu-id="82766-105">V tomto oddílu</span><span class="sxs-lookup"><span data-stu-id="82766-105">In This Section</span></span>  
 [<span data-ttu-id="82766-106">Postupy: Určení režimu úprav pro ovládací prvek Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="82766-106">How to: Specify the Edit Mode for the Windows Forms DataGridView Control</span></span>](how-to-specify-the-edit-mode-for-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="82766-107">Popisuje, jak změnit způsob, jakým uživatelé začít upravovat buňky.</span><span class="sxs-lookup"><span data-stu-id="82766-107">Describes how to change the way users start editing cells.</span></span>  
  
 [<span data-ttu-id="82766-108">Postupy: Určení výchozích hodnot pro nové řádky v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="82766-108">How to: Specify Default Values for New Rows in the Windows Forms DataGridView Control</span></span>](specify-default-values-for-new-rows-in-the-datagrid.md)  
 <span data-ttu-id="82766-109">Popisuje, jak předvyplní řádku pro nové záznamy šetří čas vstupní data.</span><span class="sxs-lookup"><span data-stu-id="82766-109">Describes how to prepopulate the row for new records to save data-entry time.</span></span>  
  
 [<span data-ttu-id="82766-110">Použití řádku pro nové záznamy v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="82766-110">Using the Row for New Records in the Windows Forms DataGridView Control</span></span>](using-the-row-for-new-records-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="82766-111">Popisuje řádku pro nové záznamy v podrobností, včetně informací o skrytím, přizpůsobením jejich vzhledu a na toho, jak souvisí <xref:System.Windows.Forms.DataGridView.Rows%2A> kolekce.</span><span class="sxs-lookup"><span data-stu-id="82766-111">Describes the row for new records in detail, including information on hiding it, on customizing its appearance, and on how it relates to the <xref:System.Windows.Forms.DataGridView.Rows%2A> collection.</span></span>  
  
 [<span data-ttu-id="82766-112">Návod: Ověřování dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="82766-112">Walkthrough: Validating Data in the Windows Forms DataGridView Control</span></span>](walkthrough-validating-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="82766-113">Popisuje způsob ověření vstupu uživatele, aby se zabránilo chyby formátování zadávání dat.</span><span class="sxs-lookup"><span data-stu-id="82766-113">Describes how to validate user input to prevent data-entry formatting errors.</span></span>  
  
 [<span data-ttu-id="82766-114">Návod: Zpracování chyb, k nimž došlo při zadávání dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="82766-114">Walkthrough: Handling Errors that Occur During Data Entry in the Windows Forms DataGridView Control</span></span>](handling-errors-that-occur-during-data-entry-in-the-datagrid.md)  
 <span data-ttu-id="82766-115">Popisuje způsob zpracování chyb zadávání dat, které pocházejí ze zdroje dat, když se uživatel pokusí o potvrzení novou hodnotu.</span><span class="sxs-lookup"><span data-stu-id="82766-115">Describes how to handle data-entry errors that originate from the data source when the user attempts to commit a new value.</span></span>  
  
## <a name="reference"></a><span data-ttu-id="82766-116">Odkaz</span><span class="sxs-lookup"><span data-stu-id="82766-116">Reference</span></span>  
 <xref:System.Windows.Forms.DataGridView>  
 <span data-ttu-id="82766-117">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView> ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="82766-117">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView> control.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.EditMode%2A?displayProperty=nameWithType>  
 <span data-ttu-id="82766-118">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.EditMode%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="82766-118">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.EditMode%2A> property.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded?displayProperty=nameWithType>  
 <span data-ttu-id="82766-119">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> událostí.</span><span class="sxs-lookup"><span data-stu-id="82766-119">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DefaultValuesNeeded> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.DataError?displayProperty=nameWithType>  
 <span data-ttu-id="82766-120">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.DataError> událostí.</span><span class="sxs-lookup"><span data-stu-id="82766-120">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.DataError> event.</span></span>  
  
 <xref:System.Windows.Forms.DataGridView.CellValidating?displayProperty=nameWithType>  
 <span data-ttu-id="82766-121">Poskytuje referenční dokumentaci pro <xref:System.Windows.Forms.DataGridView.CellValidating> událostí.</span><span class="sxs-lookup"><span data-stu-id="82766-121">Provides reference documentation for the <xref:System.Windows.Forms.DataGridView.CellValidating> event.</span></span>  
  
## <a name="related-sections"></a><span data-ttu-id="82766-122">Související oddíly</span><span class="sxs-lookup"><span data-stu-id="82766-122">Related Sections</span></span>  
 [<span data-ttu-id="82766-123">Zobrazení dat v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="82766-123">Displaying Data in the Windows Forms DataGridView Control</span></span>](displaying-data-in-the-windows-forms-datagridview-control.md)  
 <span data-ttu-id="82766-124">Obsahuje témata, které popisují, jak ručně nebo z externího zdroje dat naplnění ovládacího prvku s daty.</span><span class="sxs-lookup"><span data-stu-id="82766-124">Provides topics that describe how to populate the control with data either manually or from an external data source.</span></span>  
  
## <a name="see-also"></a><span data-ttu-id="82766-125">Viz také:</span><span class="sxs-lookup"><span data-stu-id="82766-125">See also</span></span>

- [<span data-ttu-id="82766-126">DataGridView – ovládací prvek</span><span class="sxs-lookup"><span data-stu-id="82766-126">DataGridView Control</span></span>](datagridview-control-windows-forms.md)
- [<span data-ttu-id="82766-127">Typy sloupců v ovládacím prvku Windows Forms DataGridView</span><span class="sxs-lookup"><span data-stu-id="82766-127">Column Types in the Windows Forms DataGridView Control</span></span>](column-types-in-the-windows-forms-datagridview-control.md)
