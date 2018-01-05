---
title: "Postupy: Implementace ověření pomocí ovládacího prvku DataGrid"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-wpf
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
caps.latest.revision: "9"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 78846e2b6a1d73e011441b0ccb46b8aad365d5dd
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a><span data-ttu-id="3832d-102">Postupy: Implementace ověření pomocí ovládacího prvku DataGrid</span><span class="sxs-lookup"><span data-stu-id="3832d-102">How to: Implement Validation with the DataGrid Control</span></span>
<span data-ttu-id="3832d-103"><xref:System.Windows.Controls.DataGrid> Řízení umožňuje provést ověření na úrovni buněk i řádek.</span><span class="sxs-lookup"><span data-stu-id="3832d-103">The <xref:System.Windows.Controls.DataGrid> control enables you to perform validation at both the cell and row level.</span></span> <span data-ttu-id="3832d-104">S ověřováním na úrovni buněk ověřit jednotlivé vlastnosti vázaný datový objekt když uživatel aktualizuje hodnotu.</span><span class="sxs-lookup"><span data-stu-id="3832d-104">With cell-level validation, you validate individual properties of a bound data object when a user updates a value.</span></span> <span data-ttu-id="3832d-105">S ověřováním na úrovni řádků ověřit celé datové objekty když uživatel provede změny na řádek.</span><span class="sxs-lookup"><span data-stu-id="3832d-105">With row-level validation, you validate entire data objects when a user commits changes to a row.</span></span> <span data-ttu-id="3832d-106">Můžete také poskytnout vlastní visual zpětnou vazbu pro chyby ověření, nebo použít výchozí vizuální zpětnou vazbu, <xref:System.Windows.Controls.DataGrid> řízení.</span><span class="sxs-lookup"><span data-stu-id="3832d-106">You can also provide customized visual feedback for validation errors, or use the default visual feedback that the <xref:System.Windows.Controls.DataGrid> control provides.</span></span>  
  
 <span data-ttu-id="3832d-107">Následující postupy popisují, jak se má použít pravidla ověřování <xref:System.Windows.Controls.DataGrid> vazby a přizpůsobení vizuální zpětnou vazbu.</span><span class="sxs-lookup"><span data-stu-id="3832d-107">The following procedures describe how to apply validation rules to <xref:System.Windows.Controls.DataGrid> bindings and customize the visual feedback.</span></span>  
  
### <a name="to-validate-individual-cell-values"></a><span data-ttu-id="3832d-108">Ověření hodnoty jednotlivých buněk</span><span class="sxs-lookup"><span data-stu-id="3832d-108">To validate individual cell values</span></span>  
  
-   <span data-ttu-id="3832d-109">Zadejte jeden nebo více pravidel ověřování na vazba použitá s sloupec.</span><span class="sxs-lookup"><span data-stu-id="3832d-109">Specify one or more validation rules on the binding used with a column.</span></span> <span data-ttu-id="3832d-110">Toto je podobná ověřování dat v jednoduchých ovládacích prvků, jak je popsáno v [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).</span><span class="sxs-lookup"><span data-stu-id="3832d-110">This is similar to validating data in simple controls, as described in [Data Binding Overview](../../../../docs/framework/wpf/data/data-binding-overview.md).</span></span>  
  
     <span data-ttu-id="3832d-111">Následující příklad ukazuje <xref:System.Windows.Controls.DataGrid> ovládacího prvku pomocí čtyři sloupce, které jsou vázány na jiné vlastnosti objektu firmy.</span><span class="sxs-lookup"><span data-stu-id="3832d-111">The following example shows a <xref:System.Windows.Controls.DataGrid> control with four columns bound to different properties of a business object.</span></span> <span data-ttu-id="3832d-112">Tři sloupce zadejte <xref:System.Windows.Controls.ExceptionValidationRule> nastavením <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> vlastnost `true`.</span><span class="sxs-lookup"><span data-stu-id="3832d-112">Three of the columns specify the <xref:System.Windows.Controls.ExceptionValidationRule> by setting the <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> property to `true`.</span></span>  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     <span data-ttu-id="3832d-113">Když uživatel zadá neplatnou hodnotu (například jiný-celé číslo ve sloupci ID kurzu), zobrazí se kolem buňky červené ohraničení.</span><span class="sxs-lookup"><span data-stu-id="3832d-113">When a user enters an invalid value (such as a non-integer in the Course ID column), a red border appears around the cell.</span></span> <span data-ttu-id="3832d-114">Tato výchozí ověření zpětná vazba jak je popsáno v následujícím postupu můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="3832d-114">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-cell-validation-feedback"></a><span data-ttu-id="3832d-115">Chcete-li přizpůsobit buňky ověření zpětné vazby</span><span class="sxs-lookup"><span data-stu-id="3832d-115">To customize cell validation feedback</span></span>  
  
-   <span data-ttu-id="3832d-116">Nastavit sloupce <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> vlastnost styl vhodné pro sloupec je úpravy ovládacího prvku.</span><span class="sxs-lookup"><span data-stu-id="3832d-116">Set the column's <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> property to a style appropriate for the column's editing control.</span></span> <span data-ttu-id="3832d-117">Protože ovládací prvky pro úpravy budou vytvořeny v době běhu, nemůžete použít <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> přidružená vlastnost jako v jednoduchých ovládacích prvků.</span><span class="sxs-lookup"><span data-stu-id="3832d-117">Because the editing controls are created at run time, you cannot use the <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> attached property like you would with simple controls.</span></span>  
  
     <span data-ttu-id="3832d-118">Následující příklad aktualizuje předchozí příklad přidáním stylu chyby sdíleny tři sloupce s ověřovacích pravidel.</span><span class="sxs-lookup"><span data-stu-id="3832d-118">The following example updates the previous example by adding an error style shared by the three columns with validation rules.</span></span> <span data-ttu-id="3832d-119">Když uživatel zadá neplatnou hodnotu, styl změní barvu pozadí buněk a přidá popisek.</span><span class="sxs-lookup"><span data-stu-id="3832d-119">When a user enters an invalid value, the style changes the cell background color and adds a ToolTip.</span></span> <span data-ttu-id="3832d-120">Všimněte si použití aktivační událost k určení, zda dochází k chybě ověření.</span><span class="sxs-lookup"><span data-stu-id="3832d-120">Note the use of a trigger to determine whether there is a validation error.</span></span> <span data-ttu-id="3832d-121">To je potřeba, protože nyní neexistuje žádná šablona vyhrazené chyby pro buněk.</span><span class="sxs-lookup"><span data-stu-id="3832d-121">This is required because there is currently no dedicated error template for cells.</span></span>  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     <span data-ttu-id="3832d-122">Můžete implementovat širší přizpůsobení nahrazením <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> používá podle sloupce.</span><span class="sxs-lookup"><span data-stu-id="3832d-122">You can implement more extensive customization by replacing the <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> used by the column.</span></span>  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a><span data-ttu-id="3832d-123">K ověření na jednom řádku více hodnot</span><span class="sxs-lookup"><span data-stu-id="3832d-123">To validate multiple values in a single row</span></span>  
  
1.  <span data-ttu-id="3832d-124">Implementace <xref:System.Windows.Controls.ValidationRule> podtřídami, která kontroluje více vlastností vázaný datový objekt.</span><span class="sxs-lookup"><span data-stu-id="3832d-124">Implement a <xref:System.Windows.Controls.ValidationRule> subclass that checks multiple properties of the bound data object.</span></span> <span data-ttu-id="3832d-125">V vaše <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementace metod přetypovat `value` hodnotu parametru <xref:System.Windows.Data.BindingGroup> instance.</span><span class="sxs-lookup"><span data-stu-id="3832d-125">In your <xref:System.Windows.Controls.ValidationRule.Validate%2A> method implementation, cast the `value` parameter value to a <xref:System.Windows.Data.BindingGroup> instance.</span></span> <span data-ttu-id="3832d-126">Máte přístup prostřednictvím datový objekt <xref:System.Windows.Data.BindingGroup.Items%2A> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3832d-126">You can then access the data object through the <xref:System.Windows.Data.BindingGroup.Items%2A> property.</span></span>  
  
     <span data-ttu-id="3832d-127">Následující příklad ukazuje, tento proces ověření zda `StartDate` hodnota vlastnosti pro `Course` objekt je starší než jeho `EndDate` hodnotu vlastnosti.</span><span class="sxs-lookup"><span data-stu-id="3832d-127">The following example demonstrates this process to validate whether the `StartDate` property value for a `Course` object is earlier than its `EndDate` property value.</span></span>  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  <span data-ttu-id="3832d-128">Přidat pravidlo ověření, které <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> kolekce.</span><span class="sxs-lookup"><span data-stu-id="3832d-128">Add the validation rule to the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> collection.</span></span> <span data-ttu-id="3832d-129"><xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> Vlastnost poskytuje přímý přístup k <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> vlastnost <xref:System.Windows.Data.BindingGroup> instance, které jsou seskupeny všechny vazby používané ovládací prvek.</span><span class="sxs-lookup"><span data-stu-id="3832d-129">The <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property provides direct access to the <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> property of a <xref:System.Windows.Data.BindingGroup> instance that groups all the bindings used by the control.</span></span>  
  
     <span data-ttu-id="3832d-130">Následující příklad nastavuje <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> vlastnost v jazyce XAML.</span><span class="sxs-lookup"><span data-stu-id="3832d-130">The following example sets the <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> property in XAML.</span></span> <span data-ttu-id="3832d-131"><xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tak, aby ověření dojde až po aktualizaci vázaný datový objekt.</span><span class="sxs-lookup"><span data-stu-id="3832d-131">The <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> property is set to <xref:System.Windows.Controls.ValidationStep.UpdatedValue> so that the validation occurs only after the bound data object is updated.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     <span data-ttu-id="3832d-132">Když uživatel určuje koncové datum, která je starší než počáteční datum, zobrazí se v řádku záhlaví červený vykřičník (!).</span><span class="sxs-lookup"><span data-stu-id="3832d-132">When a user specifies an end date that is earlier than the start date, a red exclamation mark (!) appears in the row header.</span></span> <span data-ttu-id="3832d-133">Tato výchozí ověření zpětná vazba jak je popsáno v následujícím postupu můžete změnit.</span><span class="sxs-lookup"><span data-stu-id="3832d-133">You can change this default validation feedback as described in the following procedure.</span></span>  
  
### <a name="to-customize-row-validation-feedback"></a><span data-ttu-id="3832d-134">Chcete-li přizpůsobit řádek ověření zpětné vazby</span><span class="sxs-lookup"><span data-stu-id="3832d-134">To customize row validation feedback</span></span>  
  
-   <span data-ttu-id="3832d-135">Nastavte <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3832d-135">Set the <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span> <span data-ttu-id="3832d-136">Tato vlastnost umožňuje přizpůsobit řádek ověření zpětné vazby pro jednotlivé <xref:System.Windows.Controls.DataGrid> ovládací prvky.</span><span class="sxs-lookup"><span data-stu-id="3832d-136">This property enables you to customize row validation feedback for individual <xref:System.Windows.Controls.DataGrid> controls.</span></span> <span data-ttu-id="3832d-137">Můžete také ovlivnit více ovládacích prvků pomocí styl implicitní řádek nastavit <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> vlastnost.</span><span class="sxs-lookup"><span data-stu-id="3832d-137">You can also affect multiple controls by using an implicit row style to set the <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> property.</span></span>  
  
     <span data-ttu-id="3832d-138">Následující příklad nahradí zpětnou vazbu výchozí řádek ověření více viditelných indikátoru.</span><span class="sxs-lookup"><span data-stu-id="3832d-138">The following example replaces the default row validation feedback with a more visible indicator.</span></span> <span data-ttu-id="3832d-139">Když uživatel zadá neplatnou hodnotu, zobrazí se v řádku záhlaví červené kolečko obsahující bílý vykřičník.</span><span class="sxs-lookup"><span data-stu-id="3832d-139">When a user enters an invalid value, a red circle with a white exclamation mark appears in the row header.</span></span> <span data-ttu-id="3832d-140">K tomu dochází na řádku a buňky chyby ověření.</span><span class="sxs-lookup"><span data-stu-id="3832d-140">This occurs for both row and cell validation errors.</span></span> <span data-ttu-id="3832d-141">Související chybové zprávě se zobrazí ve formě popisu tlačítka.</span><span class="sxs-lookup"><span data-stu-id="3832d-141">The associated error message is displayed in a ToolTip.</span></span>  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a><span data-ttu-id="3832d-142">Příklad</span><span class="sxs-lookup"><span data-stu-id="3832d-142">Example</span></span>  
 <span data-ttu-id="3832d-143">Následující příklad obsahuje kompletní ukázka pro buňku a řádek ověření.</span><span class="sxs-lookup"><span data-stu-id="3832d-143">The following example provides a complete demonstration for cell and row validation.</span></span> <span data-ttu-id="3832d-144">`Course` Třída poskytuje ukázkový datový objekt, který implementuje <xref:System.ComponentModel.IEditableObject> pro podporu transakcí.</span><span class="sxs-lookup"><span data-stu-id="3832d-144">The `Course` class provides a sample data object that implements <xref:System.ComponentModel.IEditableObject> to support transactions.</span></span> <span data-ttu-id="3832d-145"><xref:System.Windows.Controls.DataGrid> Řízení komunikuje s <xref:System.ComponentModel.IEditableObject> umožňuje uživatelům vrátit změny stisknutím klávesy ESC.</span><span class="sxs-lookup"><span data-stu-id="3832d-145">The <xref:System.Windows.Controls.DataGrid> control interacts with <xref:System.ComponentModel.IEditableObject> to enable users to revert changes by pressing ESC.</span></span>  
  
> [!NOTE]
>  <span data-ttu-id="3832d-146">Pokud používáte Visual Basic, v prvním řádku MainWindow.xaml, nahraďte `x:Class="DataGridValidation.MainWindow"` s `x:Class="MainWindow"`.</span><span class="sxs-lookup"><span data-stu-id="3832d-146">If you are using Visual Basic, in the first line of MainWindow.xaml, replace `x:Class="DataGridValidation.MainWindow"` with `x:Class="MainWindow"`.</span></span>  
  
 <span data-ttu-id="3832d-147">Chcete-li otestovat ověření, vyzkoušejte následující:</span><span class="sxs-lookup"><span data-stu-id="3832d-147">To test the validation, try the following:</span></span>  
  
-   <span data-ttu-id="3832d-148">Ve sloupci ID kurzu zadejte hodnotu celé číslo.</span><span class="sxs-lookup"><span data-stu-id="3832d-148">In the Course ID column, enter a non-integer value.</span></span>  
  
-   <span data-ttu-id="3832d-149">Ve sloupci koncové datum zadejte datum, která je starší než počáteční datum.</span><span class="sxs-lookup"><span data-stu-id="3832d-149">In the End Date column, enter a date that is earlier than the Start Date.</span></span>  
  
-   <span data-ttu-id="3832d-150">Odstraňte hodnotu v ID kurzu, počáteční datum nebo koncové datum.</span><span class="sxs-lookup"><span data-stu-id="3832d-150">Delete the value in Course ID, Start Date, or End Date.</span></span>  
  
-   <span data-ttu-id="3832d-151">Chcete-li vrátit hodnotu neplatný buňku, umístěn kurzor zpět do buňky a stisknutím klávesy ESC.</span><span class="sxs-lookup"><span data-stu-id="3832d-151">To undo an invalid cell value, put the cursor back in the cell and press the ESC key.</span></span>  
  
-   <span data-ttu-id="3832d-152">Vrátit zpět změny pro celý řádek, když je aktuální buňky v režimu úprav, stisknutím klávesy ESC dvakrát.</span><span class="sxs-lookup"><span data-stu-id="3832d-152">To undo changes for an entire row when the current cell is in edit mode, press the ESC key twice.</span></span>  
  
-   <span data-ttu-id="3832d-153">Když dojde k chybě ověření, přesuňte ukazatel myši nad indikátoru v řádku záhlaví zobrazíte přidružené chybovou zprávu.</span><span class="sxs-lookup"><span data-stu-id="3832d-153">When a validation error occurs, move your mouse pointer over the indicator in the row header to see the associated error message.</span></span>  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a><span data-ttu-id="3832d-154">Viz také</span><span class="sxs-lookup"><span data-stu-id="3832d-154">See Also</span></span>  
 <xref:System.Windows.Controls.DataGrid>  
 [<span data-ttu-id="3832d-155">DataGrid</span><span class="sxs-lookup"><span data-stu-id="3832d-155">DataGrid</span></span>](../../../../docs/framework/wpf/controls/datagrid.md)  
 [<span data-ttu-id="3832d-156">Datová vazba</span><span class="sxs-lookup"><span data-stu-id="3832d-156">Data Binding</span></span>](../../../../docs/framework/wpf/data/data-binding-wpf.md)  
 [<span data-ttu-id="3832d-157">Implementace ověření vazby</span><span class="sxs-lookup"><span data-stu-id="3832d-157">Implement Binding Validation</span></span>](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [<span data-ttu-id="3832d-158">Implementace logiky ověření na vlastních objektech</span><span class="sxs-lookup"><span data-stu-id="3832d-158">Implement Validation Logic on Custom Objects</span></span>](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
