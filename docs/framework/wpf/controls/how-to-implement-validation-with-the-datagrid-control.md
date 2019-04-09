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
ms.openlocfilehash: aead8cbd500262a4cba535fd023dd9701d50257a
ms.sourcegitcommit: 5b6d778ebb269ee6684fb57ad69a8c28b06235b9
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/08/2019
ms.locfileid: "59086803"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Postupy: Implementace ověření pomocí ovládacího prvku DataGrid
<xref:System.Windows.Controls.DataGrid> Ovládací prvek umožňuje provádět ověření na úrovni buněk a řádek. S ověřováním na úrovni buněk ověřit jednotlivé vlastnosti vázaný datový objekt když uživatel aktualizuje hodnotu. S ověřováním na úrovni řádků ověřit celé datové objekty Pokud uživatel potvrdí změny do řádku. Můžete také poskytovat přizpůsobená vizuální zpětnou vazbu pro chyby ověření, nebo použít výchozí vizuální zpětnou vazbu, která <xref:System.Windows.Controls.DataGrid> poskytuje ovládací prvek.  
  
 Následující postupy popisují, jak používat pravidla ověřování <xref:System.Windows.Controls.DataGrid> vazby a přizpůsobit vizuální zpětnou vazbu.  
  
### <a name="to-validate-individual-cell-values"></a>Ověření hodnoty jednotlivých buněk  
  
-   Zadejte jeden nebo více ověřovacích pravidel na vazba použitá s sloupec. Je to podobné ověřování dat v jednoduché ovládací prvky, jak je popsáno v [přehled datových vazeb](../data/data-binding-overview.md).  
  
     Následující příklad ukazuje <xref:System.Windows.Controls.DataGrid> ovládací prvek s čtyři sloupce, které jsou vázány na různé vlastnosti objektu firmy. Tři sloupce zadejte <xref:System.Windows.Controls.ExceptionValidationRule> nastavením <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> vlastnost `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Když uživatel zadá neplatnou hodnotu (například jiných než celých čísel ve sloupci ID kurzu), zobrazí se červené ohraničení kolem buňky. Můžete změnit toto výchozí ověření zpětnou vazbu jak je popsáno v následujícím postupu.  
  
### <a name="to-customize-cell-validation-feedback"></a>Chcete-li přizpůsobit zpětnou vazbu ověření buňky  
  
-   Nastavit sloupci <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> vlastnost stylu vhodná pro sloupec v ovládacím prvku pro úpravy. Protože ovládací prvky pro úpravy budou vytvořeny v době běhu, nelze použít <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> přidružená vlastnost stejně jako jednoduché ovládací prvky.  
  
     Následující příklad aktualizuje z předchozího příkladu tak, že přidáte chybového stylu sdílí tři sloupce s ověřovací pravidla. Když uživatel zadá neplatnou hodnotu, styl změní barvu pozadí buněk a přidá popis. Všimněte si použití aktivační procedury k určení, zda dochází k chybě ověřování. Se totiž aktuálně nejsou k dispozici žádná šablona vyhrazené chyba pro buňky.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Můžete implementovat širší přizpůsobení nahrazením <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> používané sloupce.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>K ověření více hodnot v jediném řádku  
  
1.  Implementace <xref:System.Windows.Controls.ValidationRule> podtřídy, která kontroluje více vlastností vázaný datový objekt. V vaše <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementace metody přetypovat `value` pro parametr <xref:System.Windows.Data.BindingGroup> instance. Pak přístup k objektu data prostřednictvím <xref:System.Windows.Data.BindingGroup.Items%2A> vlastnost.  
  
     Následující příklad ukazuje tento proces ověření, zda `StartDate` hodnota vlastnosti pro `Course` objekt je starší než jeho `EndDate` hodnotu vlastnosti.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2.  Přidat ověřovací pravidlo pro <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> kolekce. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> Poskytuje přímý přístup k vlastnosti <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> vlastnost <xref:System.Windows.Data.BindingGroup> instance, které jsou seskupeny všechny vazby použit v ovládacím prvku.  
  
     Následující příklad nastaví <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> vlastnost v XAML. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> Je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> tak, že ověřování dochází pouze po aktualizaci vázaný datový objekt.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Když uživatel určí koncové datum, která je starší než počáteční datum, zobrazí se červený vykřičník (!) v záhlaví řádku. Můžete změnit toto výchozí ověření zpětnou vazbu jak je popsáno v následujícím postupu.  
  
### <a name="to-customize-row-validation-feedback"></a>K přizpůsobení řádků ověření zpětné vazby  
  
-   Nastavte <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost umožňuje přizpůsobit řádek ověření zpětné vazby pro jednotlivé <xref:System.Windows.Controls.DataGrid> ovládacích prvků. Může také ovlivnit více ovládacích prvků pomocí na styl implicitní řádek nastavit <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> vlastnost.  
  
     Následující příklad nahradí zpětnou vazbu výchozí řádek ověření viditelnost indikátoru. Když uživatel zadá neplatnou hodnotu, zobrazí se červené kolečko s bílým vykřičník v záhlaví řádku. K tomu dochází u řádku a buňky chyb ověření. V popisku se zobrazí související chybová zpráva.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad obsahuje kompletní ukázku pro buňky řádků a ověření. `Course` Třída poskytující objekt ukázková data, která implementuje <xref:System.ComponentModel.IEditableObject> pro podporu transakcí. <xref:System.Windows.Controls.DataGrid> Ovládací prvek komunikuje s <xref:System.ComponentModel.IEditableObject> umožňující uživatelům vrátit změny stisknutím klávesy ESC.  
  
> [!NOTE]
>  Pokud používáte Visual Basic v prvním řádku souboru mainwindow.XAML, nahraďte `x:Class="DataGridValidation.MainWindow"` s `x:Class="MainWindow"`.  
  
 Pokud chcete otestovat ověření, zkuste následující:  
  
-   Ve sloupci ID kurzu zadejte hodnotu jiných než celých čísel.  
  
-   Ve sloupci koncové datum zadejte data, která je starší než datum zahájení.  
  
-   Odstraňte hodnotu v kurzu ID, počáteční datum nebo datum ukončení.  
  
-   Pokud chcete vrátit zpět na hodnotu neplatnou buňku, umístěte kurzor zpět do buňky a stiskněte klávesu ESC.  
  
-   Pokud chcete vrátit zpět změny provedené u celý řádek, pokud aktuální buňka v režimu úprav, stiskněte dvakrát klávesu ESC.  
  
-   Pokud dojde k chybě ověření, přesuňte ukazatel myši nad indikátoru v záhlaví řádků k zobrazení související chybové zprávy.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Datová vazba](../data/data-binding-wpf.md)
- [Implementace ověření vazby](../data/how-to-implement-binding-validation.md)
- [Implementace logiky ověření ve vlastních objektech](../data/how-to-implement-validation-logic-on-custom-objects.md)
