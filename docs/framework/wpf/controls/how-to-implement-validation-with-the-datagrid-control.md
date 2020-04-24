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
ms.openlocfilehash: 38b4c9cd7679f0d8da9b18fb5bd6bb729d33ed54
ms.sourcegitcommit: 62285ec11fa8e8424bab00511a90760c60e63c95
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/20/2020
ms.locfileid: "81646090"
---
# <a name="how-to-implement-validation-with-the-datagrid-control"></a>Postupy: Implementace ověření pomocí ovládacího prvku DataGrid
Ovládací <xref:System.Windows.Controls.DataGrid> prvek umožňuje provádět ověření na úrovni buňky i řádku. Při ověřování na úrovni buňky můžete ověřit jednotlivé vlastnosti vázaného datového objektu, když uživatel aktualizuje hodnotu. Při ověřování na úrovni řádku ověřujete celé datové objekty, když uživatel potvrdí změny na řádku. Můžete také poskytnout přizpůsobenou vizuální zpětnou vazbu pro chyby ověření nebo použít výchozí vizuální zpětnou vazbu, kterou <xref:System.Windows.Controls.DataGrid> poskytuje ovládací prvek.  
  
 Následující postupy popisují, jak použít <xref:System.Windows.Controls.DataGrid> ověřovací pravidla pro vazby a přizpůsobit vizuální zpětnou vazbu.  
  
### <a name="to-validate-individual-cell-values"></a>Ověření jednotlivých hodnot buněk  
  
- Zadejte jedno nebo více ověřovacích pravidel pro vazbu použitou se sloupcem. To je podobné ověřování dat v jednoduchých ovládacích prvků, jak je popsáno v [přehledu datové vazby](../../../desktop-wpf/data/data-binding-overview.md).  
  
     Následující příklad ukazuje <xref:System.Windows.Controls.DataGrid> ovládací prvek se čtyřmi sloupci vázanými na různé vlastnosti obchodního objektu. Tři sloupce určují <xref:System.Windows.Controls.ExceptionValidationRule> nastavenívlastnosti <xref:System.Windows.Data.Binding.ValidatesOnExceptions%2A> na `true`.  
  
     [!code-xaml[DataGrid_Validation#BasicXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/window1.xaml#basicxaml)]  
  
     Když uživatel zadá neplatnou hodnotu (například necelé číslo ve sloupci ID kurzu), zobrazí se kolem buňky červené ohraničení. Tuto výchozí zpětnou vazbu ověření můžete změnit, jak je popsáno v následujícím postupu.  
  
### <a name="to-customize-cell-validation-feedback"></a>Přizpůsobení zpětné vazby ověření buněk  
  
- Nastavte <xref:System.Windows.Controls.DataGridBoundColumn.EditingElementStyle%2A> vlastnost sloupce na styl odpovídající ovládacímu prvku pro úpravy sloupce. Vzhledem k tomu, že ovládací prvky <xref:System.Windows.Controls.Validation.ErrorTemplate%2A?displayProperty=nameWithType> pro úpravy jsou vytvářeny za běhu, nelze použít připojenou vlastnost jako u jednoduchých ovládacích prvků.  
  
     Následující příklad aktualizuje předchozí příklad přidáním chybového stylu sdíleného třemi sloupci s ověřovacími pravidly. Když uživatel zadá neplatnou hodnotu, styl změní barvu pozadí buňky a přidá popisek. Všimněte si použití aktivační události k určení, zda došlo k chybě ověření. To je nutné, protože v současné době neexistuje žádná vyhrazená šablona chyb pro buňky.  
  
     [!code-xaml[DataGrid_Validation#CellValidationXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#cellvalidationxaml)]  
  
     Můžete implementovat rozsáhlejší přizpůsobení <xref:System.Windows.Controls.DataGridColumn.CellStyle%2A> nahrazením použité sloupec.  
  
### <a name="to-validate-multiple-values-in-a-single-row"></a>Ověření více hodnot v jednom řádku  
  
1. Implementujte <xref:System.Windows.Controls.ValidationRule> podtřídu, která kontroluje více vlastností vázaného datového objektu. V <xref:System.Windows.Controls.ValidationRule.Validate%2A> implementaci metody přetypujte hodnotu parametru `value` na instanci. <xref:System.Windows.Data.BindingGroup> Potom můžete přistupovat k <xref:System.Windows.Data.BindingGroup.Items%2A> datovému objektu prostřednictvím vlastnosti.  
  
     Následující příklad ukazuje tento proces k `StartDate` ověření, `Course` zda hodnota vlastnosti pro objekt je starší než jeho `EndDate` hodnota vlastnosti.  
  
     [!code-csharp[DataGrid_Validation#CourseValidationRule](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#coursevalidationrule)]
     [!code-vb[DataGrid_Validation#CourseValidationRule](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#coursevalidationrule)]  
  
2. Přidejte ověřovací pravidlo <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A?displayProperty=nameWithType> do kolekce. Vlastnost <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> poskytuje přímý přístup <xref:System.Windows.Data.BindingGroup.ValidationRules%2A> k <xref:System.Windows.Data.BindingGroup> vlastnosti instance, která seskupuje všechny vazby používané ovládacím prvkem.  
  
     Následující příklad nastaví <xref:System.Windows.Controls.DataGrid.RowValidationRules%2A> vlastnost v XAML. Vlastnost <xref:System.Windows.Controls.ValidationRule.ValidationStep%2A> je nastavena tak, aby <xref:System.Windows.Controls.ValidationStep.UpdatedValue> k ověření došlo až po aktualizaci vázaného datového objektu.  
  
     [!code-xaml[DataGrid_Validation#RowValidationRulesXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationrulesxaml)]  
  
     Když uživatel určí koncové datum, které je dřívější než počáteční datum, zobrazí se v záhlaví řádku červený vykřičník (!). Tuto výchozí zpětnou vazbu ověření můžete změnit, jak je popsáno v následujícím postupu.  
  
### <a name="to-customize-row-validation-feedback"></a>Přizpůsobení zpětné vazby ověření řádku  
  
- Nastavte <xref:System.Windows.Controls.DataGrid.RowValidationErrorTemplate%2A?displayProperty=nameWithType> vlastnost. Tato vlastnost umožňuje přizpůsobit zpětnou <xref:System.Windows.Controls.DataGrid> vazbu ověření řádku pro jednotlivé ovládací prvky. Můžete také ovlivnit více ovládacích prvků pomocí <xref:System.Windows.Controls.DataGridRow.ValidationErrorTemplate%2A?displayProperty=nameWithType> implicitní styl řádku nastavit vlastnost.  
  
     Následující příklad nahradí výchozí zpětnou vazbu ověření řádku viditelnějším indikátorem. Když uživatel zadá neplatnou hodnotu, v záhlaví řádku se zobrazí červený kruh s bílým vykřičníkem. K tomu dochází pro chyby ověření řádku a buňky. Přidružená chybová zpráva se zobrazí v popisu.  
  
     [!code-xaml[DataGrid_Validation#RowValidationFeedbackXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#rowvalidationfeedbackxaml)]  
  
## <a name="example"></a>Příklad  
 Následující příklad poskytuje úplnou ukázku pro ověření buněk a řádků. Třída `Course` poskytuje ukázkový datový objekt, který implementuje <xref:System.ComponentModel.IEditableObject> pro podporu transakcí. Ovládací <xref:System.Windows.Controls.DataGrid> prvek spolupracuje <xref:System.ComponentModel.IEditableObject> s umožnit uživatelům vrátit změny stisknutím klávesy ESC.  
  
> [!NOTE]
> Pokud používáte visual basic, v prvním řádku MainWindow.xaml, nahradit `x:Class="DataGridValidation.MainWindow"` . `x:Class="MainWindow"`  
  
 Chcete-li ověření otestovat, vyzkoušejte následující postup:  
  
- Ve sloupci ID kurzu zadejte hodnotu bez celého čísla.  
  
- Do sloupce Koncové datum zadejte datum, které je dřívější než Počáteční datum.  
  
- Odstraňte hodnotu v ID kurzu, počátečním datu nebo koncovém datu.  
  
- Chcete-li vrátit zpět neplatnou hodnotu buňky, vložte kurzor zpět do buňky a stiskněte klávesu ESC.  
  
- Chcete-li vrátit změny pro celý řádek, když je aktuální buňka v režimu úprav, stiskněte dvakrát klávesu ESC.  
  
- Dojde-li k ověřovací chybě, přesuňte ukazatel myši nad indikátor v záhlaví řádku a zotřite přidruženou chybovou zprávu.  
  
 [!code-csharp[DataGrid_Validation#FullCode](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml.cs#fullcode)]
 [!code-vb[DataGrid_Validation#FullCode](~/samples/snippets/visualbasic/VS_Snippets_Wpf/datagrid_validation/vb/mainwindow.xaml.vb#fullcode)]  
  
 [!code-xaml[DataGrid_Validation#FullXaml](~/samples/snippets/csharp/VS_Snippets_Wpf/datagrid_validation/cs/mainwindow.xaml#fullxaml)]  
  
## <a name="see-also"></a>Viz také

- <xref:System.Windows.Controls.DataGrid>
- [DataGrid](datagrid.md)
- [Datová vazba](../../../desktop-wpf/data/data-binding-overview.md)
- [Implementovat ověření vazby](../data/how-to-implement-binding-validation.md)
- [Implementace logiky ověření u vlastních objektů](../data/how-to-implement-validation-logic-on-custom-objects.md)
