---
title: 'Postupy: Vytvoření vazby dat pomocí zdroje dat projektu (WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: e1111077a407dc32475976b15ff71170978e3184
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: HT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61765502"
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Postupy: Vytvoření vazby dat pomocí zdroje dat projektu (WCF Data Services)

Můžete vytvořit zdroje dat, které jsou založené na objektech generovaná data v aplikaci klienta WCF Data Services. Když přidáte odkaz na datovou službu s použitím **přidat odkaz na službu** dialogového okna, zdroje dat projektu se vytvoří společně s datových tříd generovaného klienta. Jeden zdroj dat se vytvoří pro každou sadu entit, které data služba zpřístupňuje. Můžete vytvářet formuláře, které zobrazují data ze služby přetažením položky zdroje těchto dat z **zdroje dat** okna do návrháře. Tyto položky budou ovládací prvky, které jsou vázány na zdroj dat. Během provádění je vázán tento zdroj dat na instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídu, která je vyplněna objekty, které jsou vrácené dotazem do datové služby. Další informace najdete v tématu [vazba dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).

 Příklady v tomto tématu ukázková datová služba Northwind a klientská data automaticky generované služby třídy. Tuto službu a třídy dat klientů jsou vytvořeny po dokončení [rychlý start služeb WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).

## <a name="use-a-project-data-source-in-a-wpf-window"></a>Použijte zdroje dat projektu v okně WPF

1. V rámci projektu WPF v sadě Visual Studio, přidejte odkaz na datová služba Northwind. Další informace najdete v tématu [jak: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).

2. V **zdroje dat** okna, rozbalte `Customers` uzlu **NorthwindEntities** zdroje dat projektu.

3. Klikněte na tlačítko **CustomerID** položky, vyberte **– pole se seznamem** ze seznamu a přetáhněte **CustomerID** položky z **zákazníkům** uzlu Návrhář.

     Tím se vytvoří následující prvky objektu v souboru XAML pro okno:

    - A <xref:System.Windows.Data.CollectionViewSource> element s názvem `customersViewSource`. <xref:System.Windows.FrameworkElement.DataContext%2A> Vlastnost na nejvyšší úrovni <xref:System.Windows.Controls.Grid> prvek objektu je nastavena na tento nový <xref:System.Windows.Data.CollectionViewSource>.

    - Vázaný na data <xref:System.Windows.Controls.ComboBox> s názvem `CustomerID`.

    - A <xref:System.Windows.Controls.Label>.

4. Přetáhněte **objednávky** navigační vlastnost do návrháře.

     Tím se vytvoří následující prvky další objekt v souboru XAML pro okno:

    - Sekundy <xref:System.Windows.Data.CollectionViewSource> element s názvem `customersOrdersViewSource`, zdroj, který je `customerViewSource`.

    - Vázaný na data <xref:System.Windows.Controls.DataGrid> ovládací prvek s názvem `ordersDataGrid`.

5. (Volitelné) Přetáhněte další položky z **zákazníkům** uzlu do návrháře.

6. Otevřete stránku kódu pro formulář a přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]

7. V dílčí třídě, která definuje formuláře, přidejte následující kód, který vytváří <xref:System.Data.Objects.ObjectContext> instance a definuje `customerID` konstantní.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]

8. V Návrháři vyberte v okně.

    > [!NOTE]
    > Ujistěte se, že samotné, namísto výběru obsah, který je v okně vyberte okno. Pokud je vybrán v okně, **název** textového pole v horní části **vlastnosti** okno by mělo obsahovat název okna.

9. V **vlastnosti** okna, vyberte **události** tlačítko.

10. Najít **Loaded** události a poté dvojitým kliknutím rozevírací seznam vedle této události.

     Visual Studio otevře soubor kódu na pozadí okna a generuje <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.

11. V nově vytvořené <xref:System.Windows.FrameworkElement.Loaded> obslužná rutina události, zkopírujte a vložte následující kód.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]

12. Tento kód vytvoří instanci <xref:System.Data.Services.Client.DataServiceCollection%601> pro `Customers` na provádění dotazu LINQ, který vrací na základě typu <xref:System.Collections.Generic.IEnumerable%601> z `Customers` spolu se souvisejícími `Orders` objekty z datová služba Northwind a provádí vazbu `customersViewSource`.

## <a name="use-a-project-data-source-in-a-windows-form"></a>Použijte zdroje dat projektu ve formuláři Windows

1. V **zdroje dat** okna, rozbalte **zákazníkům** uzlu v **NorthwindEntities** zdroje dat projektu.

2. Klikněte na tlačítko **CustomerID** položky, vyberte **– pole se seznamem** ze seznamu a přetáhněte **CustomerID** položky z **zákazníkům** uzlu Návrhář.

     Tím se vytvoří následující ovládací prvky ve formuláři:

    - Instance <xref:System.Windows.Forms.BindingSource> s názvem `customersBindingSource`.

    - Instance <xref:System.Windows.Forms.BindingNavigator> s názvem `customersBindingNavigator`. Tento ovládací prvek můžete odstranit nebude potřeba.

    - Vázaný na data <xref:System.Windows.Forms.ComboBox> s názvem `CustomerID`.

    - A <xref:System.Windows.Forms.Label>.

3. Přetáhněte **objednávky** navigační vlastnost pro formulář.

4. Tím se vytvoří `ordersBindingSource` ovládacím prvkem <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost ovládacího prvku nastavte na `customersBindingSource` a <xref:System.Windows.Forms.BindingSource.DataMember%2A> nastavenou na `Customers`. Také vytvoří `ordersDataGridView` ovládací prvek vázaný na data ve formuláři doplněny ovládací prvek popisek odpovídajícím způsobem s názvem.

5. (Volitelné) Přetáhněte další položky z **zákazníkům** uzlu do návrháře.

6. Otevřete stránku kódu pro formulář a přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):

     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersusing)]

7. V dílčí třídě, která definuje formuláře, přidejte následující kód, který vytváří <xref:System.Data.Objects.ObjectContext> instance a definuje `customerID` konstantní.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdefinition)]

8. V návrháři formuláře dvakrát klikněte na formuláři.

     Tím se otevře na stránce kódu pro formulář a vytvoří metodu, která zpracovává `Load` událost pro daný formulář.

9. V `Load` obslužná rutina události, zkopírujte a vložte následující kód.

     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabinding)]

10. Tento kód vytvoří instanci <xref:System.Data.Services.Client.DataServiceCollection%601> pro `Customers` na provedení na základě typu <xref:System.Data.Services.Client.DataServiceQuery%601> , který vrátí <xref:System.Collections.Generic.IEnumerable%601> z `Customers` z Northwind dat služby a provádí vazbu na `customersBindingSource`.

## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Postupy: Vytvoření vazby dat na elementy Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
