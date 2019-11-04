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
ms.openlocfilehash: 401949aa4bea924b458a91dc00c454c97aff4895
ms.sourcegitcommit: 944ddc52b7f2632f30c668815f92b378efd38eea
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/03/2019
ms.locfileid: "73458464"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Postupy: Implementace ověření pomocí ovládacího prvku DataGrid
Ovládací prvek <xref:System.Windows.Controls.DataGrid> umožňuje provádět ověřování na úrovni buňky i řádku. Při ověřování na úrovni buňky ověříte jednotlivé vlastnosti vázaného datového objektu, když uživatel aktualizuje hodnotu. Při ověřování na úrovni řádků ověříte celé datové objekty, když uživatel potvrdí změny řádku. Můžete také poskytnout přizpůsobenou vizuální zpětnou vazbu k chybám ověřování nebo použít výchozí vizuální zpětnou vazbu, kterou poskytuje ovládací prvek <xref:System.Windows.Controls.DataGrid>.  
  
 Následující postupy popisují, jak použít pravidla ověřování pro <xref:System.Windows.Controls.DataGrid> vazby a přizpůsobení vizuální zpětné vazby.  
  
### <a name="to-validate-individual-cell-values"></a>Ověření jednotlivých hodnot buňky  
  
- Zadejte jedno nebo více ověřovacích pravidel pro vazbu použitou se sloupcem. To je podobné ověřování dat v jednoduchých ovládacích prvcích, jak je popsáno v tématu [Přehled vytváření datových vazeb](../data/data-binding-overview.md).  
  
     Následující příklad ukazuje ovládací prvek <xref:System.Windows.Controls.DataGrid> se čtyřmi sloupci svázanými s různými vlastnostmi obchodního objektu. Tři sloupce určují <xref:System.Windows.Controls.ExceptionValidationRule> nastavením vlastnosti <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> na `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Když uživatel zadá do sloupce ID kurzu neplatnou hodnotu (například jiné než celé číslo), zobrazí se kolem buňky červené ohraničení. Můžete změnit tuto výchozí zpětnou vazbu k ověření, jak je popsáno v následujícím postupu.  
  
### <a name="to-customize-cell-validation-feedback"></a>Přizpůsobení zpětné vazby k ověření buňky  
  
- Vlastnost <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> sloupce nastavte na styl vhodný pro ovládací prvek pro úpravy sloupce. Vzhledem k tomu, že ovládací prvky pro úpravy jsou vytvořeny za běhu, nemůžete použít <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> připojenou vlastnost, jako byste používali jednoduché ovládací prvky.  
  
     Následující příklad aktualizuje předchozí příklad přidáním stylu chyby, který sdílí tři sloupce s ověřovacími pravidly. Když uživatel zadá neplatnou hodnotu, styl změní barvu pozadí buňky a přidá popis. Všimněte si použití triggeru k určení, zda došlo k chybě ověřování. To je nutné, protože pro buňky aktuálně není k dispozici žádná vyhrazená šablona chyby.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Můžete implementovat rozsáhlejší přizpůsobení nahrazením <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> používaného sloupcem.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Ověření více hodnot v jednom řádku  
  
1. Implementujte podtřídu <xref:System.Windows.Controls.ValidationRule>, která kontroluje více vlastností vázaného datového objektu. V implementaci metody <xref:System.Windows.Controls.ValidationRule.Validate%2A> přetypujte hodnotu parametru `value` na instanci <xref:System.Windows.Data.BindingGroup>. Přístup k datovému objektu pak můžete získat pomocí vlastnosti <xref:System.Windows.Data.BindingGroup.Items%2A>.  
  
     Následující příklad demonstruje tento proces ověření, zda hodnota vlastnosti `StartDate` pro `Course` objekt je dřívější než hodnota vlastnosti `EndDate`.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Přidejte ověřovací pravidlo do kolekce <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType>. Vlastnost <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> poskytuje přímý přístup k vlastnosti <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> instance <xref:System.Windows.Data.BindingGroup>, která seskupuje všechny vazby používané ovládacím prvkem.  
  
     Následující příklad nastaví vlastnost <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> v jazyce XAML. Vlastnost <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena na hodnotu <xref:System.Windows.Controls.ValidationStep.UpdatedValue>, takže ověření probíhá pouze po aktualizaci vázaného datového objektu.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Pokud uživatel zadá koncové datum, které je dřívější než počáteční datum, zobrazí se v záhlaví řádku červený vykřičník (!). Můžete změnit tuto výchozí zpětnou vazbu k ověření, jak je popsáno v následujícím postupu.  
  
### <a name="to-customize-row-validation-feedback"></a>Přizpůsobení zpětné vazby k ověření řádku  
  
- Nastavte vlastnost <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType>. Tato vlastnost umožňuje přizpůsobit zpětnou vazbu k ověření řádku pro jednotlivé ovládací prvky <xref:System.Windows.Controls.DataGrid>. Můžete také ovlivnit více ovládacích prvků pomocí implicitního stylu řádku pro nastavení vlastnosti <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType>.  
  
     Následující příklad nahradí výchozí názor na ověření řádku pomocí viditelného indikátoru. Když uživatel zadá neplatnou hodnotu, zobrazí se v záhlaví řádku červený kroužek s bílým vykřičníkem. K tomu dochází pro chyby ověřování řádku a buňky. Přidružená chybová zpráva se zobrazí v popisu tlačítka.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí kompletní ukázku ověřování buněk a řádků. Třída `Course` poskytuje ukázkový datový objekt, který implementuje <xref:System.ComponentModel.IEditableObject> pro podporu transakcí. Ovládací prvek <xref:System.Windows.Controls.DataGrid> komunikuje s <xref:System.ComponentModel.IEditableObject>, aby uživatelé mohli vrátit změny stisknutím klávesy ESC.  
  
> [!NOTE]
> Pokud používáte Visual Basic, v prvním řádku MainWindow. xaml nahraďte `x:Class="DataGridValidation.MainWindow"` `x:Class="MainWindow"`.  
  
 Chcete-li ověřit ověření, postupujte následovně:  
  
- Do sloupce ID kurzu zadejte hodnotu, která není celočíselná.  
  
- Do sloupce koncové datum zadejte datum starší než datum zahájení.  
  
- Odstraňte hodnotu v ID kurzu, počáteční datum nebo datum ukončení.  
  
- Chcete-li vrátit neplatnou hodnotu buňky, umístěte kurzor zpátky do buňky a stiskněte klávesu ESC.  
  
- Chcete-li vrátit změny celého řádku, pokud je aktuální buňka v režimu úprav, stiskněte dvakrát klávesu ESC.  
  
- Pokud dojde k chybě ověřování, přesuňte ukazatel myši nad indikátor v záhlaví řádku, aby se zobrazila přidružená chybová zpráva.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Viz také:

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Datová vazba](../../../desktop-wpf/data/data-binding-overview.md)
- [Implementace ověření vazby](../data/how-to-implement-binding-validation.md)
- [Implementace logiky ověření na vlastních objektech](../data/how-to-implement-validation-logic-on-custom-objects.md)
