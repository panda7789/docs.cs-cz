---
title: 'Postupy: vytvoření vazby dat pomocí projektu zdroje dat (služby WCF Data Services)'
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- data binding, WCF Data Services
- WCF Data Services, data binding
ms.assetid: 2477af0a-676f-44f7-b73d-e66208785509
ms.openlocfilehash: 0807b8de6bad5e70fbf522cb1cc20872c59fe1b4
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="how-to-bind-data-using-a-project-data-source-wcf-data-services"></a>Postupy: vytvoření vazby dat pomocí projektu zdroje dat (služby WCF Data Services)
Vytvořením zdroje dat, které jsou založeny na generované datové objekty [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské aplikace. Když přidáte odkaz na datové služby pomocí **přidat odkaz na službu** dialogové okno, zdroj dat projektu je vytvořen společně s datové třídy generovaného klienta. Jeden zdroj dat se vytvoří pro každou sadu entit, že data služby vystavuje. Můžete vytvořit formuláře, které zobrazují data ze služby tak, že přetáhnete tyto položky zdroje dat z **zdroje dat** okna do návrháře. Tyto položky stát ovládacích prvků, které jsou vázány na zdroj dat. Během provádění tento zdroj dat je vázána na instanci systému <xref:System.Data.Services.Client.DataServiceCollection%601> třídy, která je vyplněn objekty, které jsou ke službě dat vrácených dotazem. Další informace najdete v tématu [vazby dat k ovládacím prvkům](../../../../docs/framework/data/wcf/binding-data-to-controls-wcf-data-services.md).  
  
 Příklady v tomto tématu službu Northwind ukázková data a data klienta automaticky vygenerovanou služby třídy. Tato služba a datové třídy klienta se vytvoří při dokončení [rychlého startu služby WCF Data Services](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md).  
  
### <a name="to-use-a-project-data-source-in-a-wpf-window"></a>Budou používat zdroj dat projektu v okně WPF  
  
1.  V projektu WPF přidáte odkaz na službu Northwind data. Další informace najdete v tématu [postupy: Přidání odkazu na službu Data](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md).  
  
2.  V **zdroje dat** okno, rozbalte `Customers` uzel v **NorthwindEntities** zdroj dat projektu.  
  
3.  Klikněte na tlačítko **CustomerID** položku, vyberte **ComboBox** ze seznamu a přetáhněte **CustomerID** položky z **zákazníci** uzlu Návrhář.  
  
     Tím se vytvoří následující prvky objektu v souboru XAML pro okno:  
  
    -   A <xref:System.Windows.Data.CollectionViewSource> element s názvem `customersViewSource`. <xref:System.Windows.FrameworkElement.DataContext%2A> Vlastnost nejvyšší úrovně <xref:System.Windows.Controls.Grid> element objektu je nastaven pro tento nový <xref:System.Windows.Data.CollectionViewSource>.  
  
    -   Vázané na data <xref:System.Windows.Controls.ComboBox> s názvem `CustomerID`.  
  
    -   A <xref:System.Windows.Controls.Label>.  
  
4.  Přetáhněte **objednávky** navigační vlastnost pro návrháře.  
  
     Tím se vytvoří následující prvky další objekt v souboru XAML pro okno:  
  
    -   Druhý <xref:System.Windows.Data.CollectionViewSource> element s názvem `customersOrdersViewSource`, zdroj, který je `customerViewSource`.  
  
    -   Vázané na data <xref:System.Windows.Controls.DataGrid> ovládací prvek s názvem `ordersDataGrid`.  
  
5.  (Volitelné) Přetáhněte další položky z **zákazníci** uzlu do návrháře.  
  
6.  Otevřít stránku kód pro formulář a přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersusingwpf)]  
  
7.  V částečné třídy, která definuje formuláře, přidejte následující kód, který vytvoří <xref:System.Data.Objects.ObjectContext> instance a definuje `customerID` konstantní.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdefinitionwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinitionWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdefinitionwpf)]  
  
8.  V Návrháři vyberte okna.  
  
    > [!NOTE]
    >  Ujistěte se, že vyberete okno samotné nevyberete, ale obsah, který je v okně. Pokud je vybrána okna, **název** textového pole v horní části **vlastnosti** okno by mělo obsahovat název okna.  
  
9. V **vlastnosti** vyberte **události** tlačítko.  
  
10. Najít **Loaded** události a poté dvojitým kliknutím rozevíracího seznamu vedle této události.  
  
     Visual Studio otevře soubor kódu pro okno a generuje <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události.  
  
11. V nově vytvořený <xref:System.Windows.FrameworkElement.Loaded> obslužné rutiny události, zkopírujte a vložte následující kód.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf2.xaml.cs#customersordersdatabindingwpf)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingWpf](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf2.xaml.vb#customersordersdatabindingwpf)]  
  
12. Tento kód vytvoří instanci <xref:System.Data.Services.Client.DataServiceCollection%601> pro `Customers` na spuštění dotazu LINQ, který vrací založený na typu <xref:System.Collections.Generic.IEnumerable%601> z `Customers` společně s související `Orders` objektů ze služby Northwind dat a váže k `customersViewSource`.  
  
### <a name="to-use-a-project-data-source-in-a-windows-form"></a>Budou používat zdroj dat projektu ve formuláři Windows  
  
1.  V **zdroje dat** okno, rozbalte **zákazníci** uzel v **NorthwindEntities** zdroj dat projektu.  
  
2.  Klikněte na tlačítko **CustomerID** položku, vyberte **ComboBox** ze seznamu a přetáhněte **CustomerID** položky z **zákazníci** uzlu Návrhář.  
  
     Tím se vytvoří následující ovládací prvky na formuláři:  
  
    -   Instance <xref:System.Windows.Forms.BindingSource> s názvem `customersBindingSource`.  
  
    -   Instance <xref:System.Windows.Forms.BindingNavigator> s názvem `customersBindingNavigator`. Tento ovládací prvek můžete odstranit, protože nebude potřeba.  
  
    -   Vázané na data <xref:System.Windows.Forms.ComboBox> s názvem `CustomerID`.  
  
    -   A <xref:System.Windows.Forms.Label>.  
  
3.  Přetáhněte **objednávky** navigační vlastnost pro formulář.  
  
4.  Tím se vytvoří `ordersBindingSource` řízení s <xref:System.Windows.Forms.BindingSource.DataSource%2A> vlastnost nastavena na ovládacího prvku `customersBindingSource` a <xref:System.Windows.Forms.BindingSource.DataMember%2A> vlastnost nastavena na hodnotu `Customers`. Vytvoří také `ordersDataGridView` vázané na data ovládacího prvku formuláře, spolu odpovídajícím způsobem názvem Popisek – ovládací prvek.  
  
5.  (Volitelné) Přetáhněte další položky z **zákazníci** uzlu do návrháře.  
  
6.  Otevřít stránku kód pro formulář a přidejte následující `using` příkazy (`Imports` v jazyce Visual Basic):  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersusing)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersUsing](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersusing)]  
  
7.  V částečné třídy, která definuje formuláře, přidejte následující kód, který vytvoří <xref:System.Data.Objects.ObjectContext> instance a definuje `customerID` konstantní.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdefinition)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDefinition](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdefinition)]  
  
8.  V návrháři formuláře klikněte dvakrát na formuláři.  
  
     Tím se otevře znaková stránka pro daný formulář a vytvoří metoda, která zpracovává `Load` událost pro daný formulář.  
  
9. V `Load` obslužné rutiny události, zkopírujte a vložte následující kód.  
  
     [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabinding)]
     [!code-vb[Astoria Northwind Client#CustomersOrdersDataBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabinding)]  
  
10. Tento kód vytvoří instanci <xref:System.Data.Services.Client.DataServiceCollection%601> pro `Customers` na provedení na základě typu <xref:System.Data.Services.Client.DataServiceQuery%601> , který vrací <xref:System.Collections.Generic.IEnumerable%601> z `Customers` z Northwind data služby a váže se k `customersBindingSource`.  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Postupy: Vytvoření vazby dat na elementy Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md)
