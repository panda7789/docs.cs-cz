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
ms.openlocfilehash: 8ae651b3085b39673a51cf8d5f65e9bfb9da87d7
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69962042"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Postupy: Implementace ověření pomocí ovládacího prvku DataGrid
<xref:System.Windows.Controls.DataGrid> Ovládací prvek umožňuje provádět ověřování na úrovni buňky i řádku. Při ověřování na úrovni buňky ověříte jednotlivé vlastnosti vázaného datového objektu, když uživatel aktualizuje hodnotu. Při ověřování na úrovni řádků ověříte celé datové objekty, když uživatel potvrdí změny řádku. Můžete také poskytnout přizpůsobenou vizuální zpětnou vazbu k chybám ověřování nebo použít výchozí vizuální zpětnou vazbu, kterou <xref:System.Windows.Controls.DataGrid> ovládací prvek poskytuje.  
  
 Následující postupy popisují, jak použít pravidla ověřování pro <xref:System.Windows.Controls.DataGrid> vazby a přizpůsobit vizuální zpětnou vazbu.  
  
### <a name="to-validate-individual-cell-values"></a>Ověření jednotlivých hodnot buňky  
  
- Zadejte jedno nebo více ověřovacích pravidel pro vazbu použitou se sloupcem. To je podobné ověřování dat v jednoduchých ovládacích prvcích, jak je popsáno v tématu [Přehled vytváření datových vazeb](../data/data-binding-overview.md).  
  
     Následující příklad ukazuje <xref:System.Windows.Controls.DataGrid> ovládací prvek se čtyřmi sloupci, které jsou vázány na různé vlastnosti obchodního objektu. Tři sloupce určují <xref:System.Windows.Controls.ExceptionValidationRule> <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> nastavením vlastnosti na `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Když uživatel zadá do sloupce ID kurzu neplatnou hodnotu (například jiné než celé číslo), zobrazí se kolem buňky červené ohraničení. Můžete změnit tuto výchozí zpětnou vazbu k ověření, jak je popsáno v následujícím postupu.  
  
### <a name="to-customize-cell-validation-feedback"></a>Přizpůsobení zpětné vazby k ověření buňky  
  
- Nastavte <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> vlastnost sloupce na styl odpovídající ovládacímu prvku pro úpravy sloupce. Vzhledem k tomu, že jsou ovládací prvky pro úpravy vytvářeny za běhu <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> , nelze použít připojenou vlastnost, například byste měli jednoduché ovládací prvky.  
  
     Následující příklad aktualizuje předchozí příklad přidáním stylu chyby, který sdílí tři sloupce s ověřovacími pravidly. Když uživatel zadá neplatnou hodnotu, styl změní barvu pozadí buňky a přidá popis. Všimněte si použití triggeru k určení, zda došlo k chybě ověřování. To je nutné, protože pro buňky aktuálně není k dispozici žádná vyhrazená šablona chyby.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Můžete implementovat rozsáhlejší přizpůsobení nahrazením <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> používaného sloupce.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Ověření více hodnot v jednom řádku  
  
1. <xref:System.Windows.Controls.ValidationRule> Implementujte podtřídu, která kontroluje více vlastností vázaného datového objektu. V implementaci `value` <xref:System.Windows.Data.BindingGroup> metody přetypujte hodnotu parametru na instanci. <xref:System.Windows.Controls.ValidationRule.Validate%2A> Přístup k datovému objektu pak můžete získat pomocí <xref:System.Windows.Data.BindingGroup.Items%2A> vlastnosti.  
  
     Následující příklad demonstruje tento proces pro ověření, `StartDate` zda hodnota vlastnosti `Course` pro objekt je dřívější než hodnota `EndDate` jeho vlastnosti.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Přidejte ověřovací pravidlo do <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> kolekce. Vlastnost poskytuje přímý přístup <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> k vlastnosti <xref:System.Windows.Data.BindingGroup> instance, která seskupuje všechny vazby používané ovládacím prvkem. <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A>  
  
     Následující příklad nastaví <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> vlastnost v jazyce XAML. Vlastnost je nastavena na <xref:System.Windows.Controls.ValidationStep.UpdatedValue> hodnotu tak, aby k ověření došlo až po aktualizaci vázaného datového objektu. <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A>  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Pokud uživatel zadá koncové datum, které je dřívější než počáteční datum, zobrazí se v záhlaví řádku červený vykřičník (!). Můžete změnit tuto výchozí zpětnou vazbu k ověření, jak je popsáno v následujícím postupu.  
  
### <a name="to-customize-row-validation-feedback"></a>Přizpůsobení zpětné vazby k ověření řádku  
  
- <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> Nastavte vlastnost. Tato vlastnost umožňuje přizpůsobit zpětnou vazbu k ověření řádku pro <xref:System.Windows.Controls.DataGrid> jednotlivé ovládací prvky. Můžete také ovlivnit více ovládacích prvků pomocí implicitního stylu řádku pro nastavení <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> vlastnosti.  
  
     Následující příklad nahradí výchozí názor na ověření řádku pomocí viditelného indikátoru. Když uživatel zadá neplatnou hodnotu, zobrazí se v záhlaví řádku červený kroužek s bílým vykřičníkem. K tomu dochází pro chyby ověřování řádku a buňky. Přidružená chybová zpráva se zobrazí v popisu tlačítka.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad uvádí kompletní ukázku ověřování buněk a řádků. Třída poskytuje ukázkový datový objekt, který implementuje <xref:System.ComponentModel.IEditableObject> pro podporu transakcí. `Course` Ovládací prvek komunikuje s <xref:System.ComponentModel.IEditableObject> tím, aby uživatelům umožnil vrátit změny stisknutím klávesy ESC. <xref:System.Windows.Controls.DataGrid>  
  
> [!NOTE]
> Pokud používáte Visual Basic, nahraďte v prvním řádku souboru MainWindow. XAML parametrem `x:Class="DataGridValidation.MainWindow"`. `x:Class="MainWindow"`  
  
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
- [Datová vazba](../data/data-binding-wpf.md)
- [Implementace ověření vazby](../data/how-to-implement-binding-validation.md)
- [Implementace logiky ověření na vlastních objektech](../data/how-to-implement-validation-logic-on-custom-objects.md)
