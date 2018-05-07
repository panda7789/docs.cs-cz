---
title: 'Postupy: Implementace ověření pomocí ovládacího prvku DataGrid'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- DataGrid [WPF], validation
- validation [WPF], DataGrid
ms.assetid: ec6078a8-1e42-4648-b414-f4348e81bda1
ms.openlocfilehash: 20fcc8ebafb25e4e4f176447972e7637aaa5cd7d
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Postupy: Implementace ověření pomocí ovládacího prvku DataGrid
<xref:System.Windows.Controls.DataGrid> Řízení umožňuje provést ověření na úrovni buněk i řádek. S ověřováním na úrovni buněk ověřit jednotlivé vlastnosti vázaný datový objekt když uživatel aktualizuje hodnotu. S ověřováním na úrovni řádků ověřit celé datové objekty když uživatel provede změny na řádek. Můžete také poskytnout vlastní visual zpětnou vazbu pro chyby ověření, nebo použít výchozí vizuální zpětnou vazbu, <xref:System.Windows.Controls.DataGrid> řízení.  
  
 Následující postupy popisují, jak se má použít pravidla ověřování <xref:System.Windows.Controls.DataGrid> vazby a přizpůsobení vizuální zpětnou vazbu.  
  
### <a name="to-validate-individual-cell-values"></a>Ověření hodnoty jednotlivých buněk  
  
-   Zadejte jeden nebo více pravidel ověřování na vazba použitá s sloupec. Toto je podobná ověřování dat v jednoduchých ovládacích prvků, jak je popsáno v [přehled vazby dat](../../../../docs/framework/wpf/data/data-binding-overview.md).  
  
     Následující příklad ukazuje <xref:System.Windows.Controls.DataGrid> ovládacího prvku pomocí čtyři sloupce, které jsou vázány na jiné vlastnosti objektu firmy. Tři sloupce zadejte <xref:System.Windows.Controls.ExceptionValidationRule> nastavením <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> vlastnost `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Když uživatel zadá neplatnou hodnotu (například jiný-celé číslo ve sloupci ID kurzu), zobrazí se kolem buňky červené ohraničení. Tato výchozí ověření zpětná vazba jak je popsáno v následujícím postupu můžete změnit.  
  
### <a name="to-customize-cell-validation-feedback"></a>Chcete-li přizpůsobit buňky ověření zpětné vazby  
  
-   Nastavit sloupce <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> vlastnost styl vhodné pro sloupec je úpravy ovládacího prvku. Protože ovládací prvky pro úpravy budou vytvořeny v době běhu, nemůžete použít <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> přidružená vlastnost jako v jednoduchých ovládacích prvků.  
  
     Následující příklad aktualizuje předchozí příklad přidáním stylu chyby sdíleny tři sloupce s ověřovacích pravidel. Když uživatel zadá neplatnou hodnotu, styl změní barvu pozadí buněk a přidá popisek. Všimněte si použití aktivační událost k určení, zda dochází k chybě ověření. To je potřeba, protože nyní neexistuje žádná šablona vyhrazené chyby pro buněk.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Můžete implementovat širší přizpůsobení nahrazením <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> používá podle sloupce.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>K ověření na jednom řádku více hodnot  
  
1.  Implementace <xref:System.Windows.Controls.ValidationRule> podtřídami, která kontroluje více vlastností vázaný datový objekt. V vaše <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementace metod přetypovat `value` hodnotu parametru <xref:System.Windows.Data.BindingGroup> instance. Máte přístup prostřednictvím datový objekt <xref:System.Windows.Data.BindingGroup.Items%2A> vlastnost.  
  
     Následující příklad ukazuje, tento proces ověření zda `StartDate` hodnota vlastnosti pro `Course` objekt je starší než jeho `EndDate` hodnotu vlastnosti.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  Přidat pravidlo ověření, které <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> kolekce. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> Vlastnost poskytuje přímý přístup k <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> vlastnost <xref:System.Windows.Data.BindingGroup> instance, které jsou seskupeny všechny vazby používané ovládací prvek.  
  
     Následující příklad nastavuje <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> vlastnost v jazyce XAML. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tak, aby ověření dojde až po aktualizaci vázaný datový objekt.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Když uživatel určuje koncové datum, která je starší než počáteční datum, zobrazí se v řádku záhlaví červený vykřičník (!). Tato výchozí ověření zpětná vazba jak je popsáno v následujícím postupu můžete změnit.  
  
### <a name="to-customize-row-validation-feedback"></a>Chcete-li přizpůsobit řádek ověření zpětné vazby  
  
-   Nastavte <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost umožňuje přizpůsobit řádek ověření zpětné vazby pro jednotlivé <xref:System.Windows.Controls.DataGrid> ovládací prvky. Můžete také ovlivnit více ovládacích prvků pomocí styl implicitní řádek nastavit <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> vlastnost.  
  
     Následující příklad nahradí zpětnou vazbu výchozí řádek ověření více viditelných indikátoru. Když uživatel zadá neplatnou hodnotu, zobrazí se v řádku záhlaví červené kolečko obsahující bílý vykřičník. K tomu dochází na řádku a buňky chyby ověření. Související chybové zprávě se zobrazí ve formě popisu tlačítka.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje kompletní ukázka pro buňku a řádek ověření. `Course` Třída poskytuje ukázkový datový objekt, který implementuje <xref:System.ComponentModel.IEditableObject> pro podporu transakcí. <xref:System.Windows.Controls.DataGrid> Řízení komunikuje s <xref:System.ComponentModel.IEditableObject> umožňuje uživatelům vrátit změny stisknutím klávesy ESC.  
  
> [!NOTE]
>  Pokud používáte Visual Basic, v prvním řádku MainWindow.xaml, nahraďte `x:Class="DataGridValidation.MainWindow"` s `x:Class="MainWindow"`.  
  
 Chcete-li otestovat ověření, vyzkoušejte následující:  
  
-   Ve sloupci ID kurzu zadejte hodnotu celé číslo.  
  
-   Ve sloupci koncové datum zadejte datum, která je starší než počáteční datum.  
  
-   Odstraňte hodnotu v ID kurzu, počáteční datum nebo koncové datum.  
  
-   Chcete-li vrátit hodnotu neplatný buňku, umístěn kurzor zpět do buňky a stisknutím klávesy ESC.  
  
-   Vrátit zpět změny pro celý řádek, když je aktuální buňky v režimu úprav, stisknutím klávesy ESC dvakrát.  
  
-   Když dojde k chybě ověření, přesuňte ukazatel myši nad indikátoru v řádku záhlaví zobrazíte přidružené chybovou zprávu.  
  
 [!code-csharp[DataGrid_Validation#FullCode](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](../../../../samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](../../../../samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Viz také  
 <xref:System.Windows.Controls.DataGrid>  
 [DataGrid](../../../../docs/framework/wpf/controls/datagrid.md)  
 [Datová vazba](../../../../docs/framework/wpf/data/data-binding-wpf.md)  
 [Implementace ověření vazby](../../../../docs/framework/wpf/data/how-to-implement-binding-validation.md)  
 [Implementace logiky ověření na vlastních objektech](../../../../docs/framework/wpf/data/how-to-implement-validation-logic-on-custom-objects.md)
