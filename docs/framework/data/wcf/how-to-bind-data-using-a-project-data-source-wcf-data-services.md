---
title: 'Postupy: Vázání dat pomocí zdroje dat projektu (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: 85d5974f43349d91d56a1ab41b314521a6ee7348
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780164"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Postupy: Vázání dat pomocí zdroje dat projektu (WCF Data Services)

Můžete vytvořit zdroje dat, které jsou založeny na generovaných datových objektech v klientské aplikaci WCF Data Services. Když přidáte odkaz na datovou službu pomocí dialogového okna **Přidat odkaz na službu** , vytvoří se zdroj dat projektu společně s generovanými datovými třídami klienta. Jeden zdroj dat se vytvoří pro každou sadu entit, kterou datová služba zpřístupňuje. Formuláře, které zobrazují data ze služby, můžete vytvořit přetažením těchto položek zdrojů dat z okna **zdroje dat** do návrháře. Tyto položky se stanou ovládacími prvky, které jsou svázány se zdrojem dat. Během provádění je tento zdroj dat svázán s instancí <xref:System.Data.Services.Client.DataServiceCollection%601> třídy, která je vyplněna objekty, které jsou vráceny dotazem na datovou službu. Další informace najdete v tématu [vázání dat na ovládací prvky](binding-data-to-controls-wcf-data-services.md).

 Příklady v tomto tématu používají ukázkovou datovou službu Northwind a automaticky vygenerované třídy klientské datové služby. Tato služba a klientské datové třídy se vytvoří po dokončení [WCF Data Services rychlý Start](quickstart-wcf-data-services.md).

## <a name="use-a-project-data-source-in-a-wpf-window"></a>Použití zdroje dat projektu v okně WPF

1. V aplikaci Visual Studio, v projektu WPF, přidejte odkaz na datovou službu Northwind. Další informace najdete v tématu [jak: Přidejte odkaz](how-to-add-a-data-service-reference-wcf-data-services.md)na datovou službu.

2. V okně **zdroje dat** rozbalte `Customers` uzel ve zdroji dat projektu **NorthwindEntities** .

3. Klikněte na položku **KódZákazníka** , v seznamu vyberte položku **ComboBox** a přetáhněte položku **KódZákazníka** z uzlu **Customers** do návrháře.

     Tím dojde k vytvoření následujících prvků objektu v souboru XAML pro okno:

    - Element s názvem `customersViewSource`. <xref:System.Windows.Data.CollectionViewSource> Vlastnost prvku objektu nejvyšší úrovně <xref:System.Windows.Controls.Grid> je nastavena na hodnotu New <xref:System.Windows.Data.CollectionViewSource>. <xref:System.Windows.FrameworkElement.DataContext%2A>

    - S názvem <xref:System.Windows.Controls.ComboBox> `CustomerID`vázaným na data.

    - A <xref:System.Windows.Controls.Label>.

4. Přetáhněte navigační vlastnost **Orders (objednávky** ) do návrháře.

     Tím se vytvoří následující prvky objektu v souboru XAML pro okno:

    - Druhý <xref:System.Windows.Data.CollectionViewSource> prvek s názvem `customersOrdersViewSource`, `customerViewSource`zdroj, který je.

    - Ovládací prvek vázaný <xref:System.Windows.Controls.DataGrid> na data s `ordersDataGrid`názvem.

5. Volitelné Přetáhněte další položky z uzlu **Customers** do návrháře.

6. Otevřete znakovou stránku formuláře a přidejte následující `using` příkazy (`Imports` v Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. V dílčí třídě, která definuje formulář, přidejte následující kód, který vytvoří <xref:System.Data.Objects.ObjectContext> instanci a `customerID` definuje konstantu.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. V návrháři vyberte okno.

    > [!NOTE]
    > Ujistěte se, že jste vybrali samotné okno místo výběru obsahu, který se nachází v rámci okna. Pokud je toto okno vybráno, textové pole **název** v horní části okna **vlastností** by mělo obsahovat název okna.

9. V okně **vlastnosti** vyberte tlačítko **události** .

10. Najděte **načtenou** událost a dvakrát klikněte na rozevírací seznam vedle této události.

     Visual Studio otevře soubor kódu na pozadí okna a vygeneruje <xref:System.Windows.FrameworkElement.Loaded> obslužnou rutinu události.

11. V nově vytvořené <xref:System.Windows.FrameworkElement.Loaded> obslužné rutině události zkopírujte a vložte následující kód.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. Tento kód <xref:System.Data.Services.Client.DataServiceCollection%601> vytvoří instanci `Customers` pro typ na základě spuštění dotazu <xref:System.Collections.Generic.IEnumerable%601> LINQ, který vrátí z `Customers` spolu se souvisejícími `Orders` objekty z datové služby Northwind a váže ho k `customersViewSource`.

## <a name="use-a-project-data-source-in-a-windows-form"></a>Použití zdroje dat projektu ve formuláři Windows

1. V okně **zdroje dat** rozbalte uzel **Customers (zákazníci** ) ve zdroji dat projektu **NorthwindEntities** .

2. Klikněte na položku **KódZákazníka** , v seznamu vyberte položku **ComboBox** a přetáhněte položku **KódZákazníka** z uzlu **Customers** do návrháře.

     Tím se ve formuláři vytvoří následující ovládací prvky:

    - Instance <xref:System.Windows.Forms.BindingSource> pojmenovaného `customersBindingSource`.

    - Instance <xref:System.Windows.Forms.BindingNavigator> pojmenovaného `customersBindingNavigator`. Tento ovládací prvek můžete odstranit, protože nebude potřeba.

    - S názvem <xref:System.Windows.Forms.ComboBox> `CustomerID`vázaným na data.

    - A <xref:System.Windows.Forms.Label>.

3. Přetáhněte navigační vlastnost **Orders** do formuláře.

4. Tím `ordersBindingSource` `customersBindingSource` <xref:System.Windows.Forms.BindingSource.DataMember%2A> `Customers`se vytvoří ovládací prvek s vlastnostíovládacíhoprvkunastavenýmnahodnotuavlastnostnastavenouna.<xref:System.Windows.Forms.BindingSource.DataSource%2A> Také vytvoří `ordersDataGridView` ovládací prvek vázaný na data na formuláři, který provází odpovídající ovládací prvek popisek.

5. Volitelné Přetáhněte další položky z uzlu **Customers** do návrháře.

6. Otevřete znakovou stránku formuláře a přidejte následující `using` příkazy (`Imports` v Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersusing)]

7. V dílčí třídě, která definuje formulář, přidejte následující kód, který vytvoří <xref:System.Data.Objects.ObjectContext> instanci a `customerID` definuje konstantu.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdefinition)]

8. V návrháři formuláře poklikejte na formulář.

     Tím se otevře znaková stránka pro formulář a vytvoří se metoda, která zpracovává `Load` událost pro formulář.

9. V obslužné rutině události zkopírujte a vložte následující kód. `Load`

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabinding)]

10. Tento kód <xref:System.Data.Services.Client.DataServiceCollection%601> vytvoří instanci `Customers` pro typ na základě provedení `Customers` a <xref:System.Data.Services.Client.DataServiceQuery%601> , které vrátí <xref:System.Collections.Generic.IEnumerable%601> z datové služby Northwind, a váže ji k `customersBindingSource`.

## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Postupy: Vázání dat na prvky Windows Presentation Foundation](bind-data-to-wpf-elements-wcf-data-services.md)
