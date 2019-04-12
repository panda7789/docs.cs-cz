---
title: Vazba dat k ovládacím prvkům (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
ms.openlocfilehash: fb2a7c8e1cf3fbae4c6417dab492343ead991204
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517873"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Vazba dat k ovládacím prvkům (WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], můžete svázat ovládací prvky, jako `ComboBox` a `ListView` ovládacích prvků do instance <xref:System.Data.Services.Client.DataServiceCollection%601> třídy. Tuto kolekci, která dědí z <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy, obsahuje data z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu. Tato třída reprezentuje kolekci dynamická data, která poskytuje oznámení, pokud získat přidávat nebo odebírat položky. Při použití instance <xref:System.Data.Services.Client.DataServiceCollection%601> pro datovou vazbu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny pro zpracování těchto událostí k zajištění, že objekty sledován pomocí funkce <xref:System.Data.Services.Client.DataServiceContext> zůstane synchronizovaná s daty v elementu vazby uživatelského rozhraní.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Implementuje třída (nepřímo) <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní kontextu o upozornění, když je přidán či odebrán z kolekce objektů. Použít s objekty typu služby data <xref:System.Data.Services.Client.DataServiceCollection%601> musí také implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní upozornění <xref:System.Data.Services.Client.DataServiceCollection%601> při změnily se vlastnosti objektů v kolekci vazby.  
  
> [!NOTE]
>  Při použití **přidat odkaz na službu** dialogové okno nebo [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroj s `/dataservicecollection` možnost pro generování tříd klientské datové služby, generované datové třídy implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [jak: Ruční generování tříd klientské datové služby](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Vytváření kolekce vazby  
 Vytvořit novou instanci třídy <xref:System.Data.Services.Client.DataServiceCollection%601> třídy voláním jedné z metod konstruktoru třídy pomocí zadaného <xref:System.Data.Services.Client.DataServiceContext> instance a volitelně <xref:System.Data.Services.Client.DataServiceQuery%601> nebo dotaz LINQ, který, pokud je spuštěn, vrátí <xref:System.Collections.Generic.IEnumerable%601> instance. To <xref:System.Collections.Generic.IEnumerable%601> poskytuje zdroj objekty pro vazbu kolekce, která jsou z materializovaného [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu. Další informace najdete v tématu [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). Ve výchozím nastavení, změny provedené v vázaný objekty a vložení do kolekce položek automaticky sleduje provedené <xref:System.Data.Services.Client.DataServiceContext>. Pokud chcete manuálně sledovat tyto změny, volání jedné z metod konstruktoru, které provede `trackingMode` parametr a zadat hodnotu <xref:System.Data.Services.Client.TrackingMode.None>.  
  
 Následující příklad ukazuje, jak vytvořit instanci <xref:System.Data.Services.Client.DataServiceCollection%601> podle zadaného <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601> , který vrátí všechny zákazníky s související objednávky:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Vytvoření vazby dat na elementy Windows Presentation Foundation  
 Protože <xref:System.Data.Services.Client.DataServiceCollection%601> třída dědí z <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy, lze svázat objekty elementu, nebo ovládací prvek v aplikaci Windows Presentation Foundation (WPF) stejně jako při použití <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy pro vazbu. Další informace najdete v tématu [datové vazby (Windows Presentation Foundation)](../../../../docs/framework/wpf/data/data-binding-wpf.md). Data služby data svázat ovládací prvky WPF jedním ze způsobů je nastavit `DataContext` vlastnost elementu, který chcete instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídu, která obsahuje výsledek dotazu. V tomto případě použijete <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost pro nastavení zdrojového objektu ovládacího prvku. Použití <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> vlastnosti a určit, které vlastnosti objektu vázaného k zobrazení. Pokud na související objekt, který je vrácen navigační vlastnost vazby prvku zahrnout vazby definované pro cestu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost. Tato cesta je relativní vzhledem k nastavením kořenového objektu <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnosti nadřazeného ovládacího prvku. Následující příklad nastaví <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> prvek, který chcete vytvořit vazbu na nadřazený ovládací prvek <xref:System.Data.Services.Client.DataServiceCollection%601> objektů zákazníka:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Následující příklad ukazuje definici XAML vazby podřízené <xref:System.Windows.Controls.DataGrid> a <xref:System.Windows.Controls.ComboBox> ovládací prvky:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Další informace najdete v tématu [jak: Vytvoření vazby dat na elementy Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Když entity se účastní jeden mnoho nebo many-to-many vztah, navigační vlastnost pro daný vztah vrátí kolekci souvisejících objektů. Při použití **přidat odkaz na službu** dialogové okno nebo DataSvcUtil.exe nástroj pro generování tříd klientské datové služby, navigační vlastnost vrací instanci <xref:System.Data.Services.Client.DataServiceCollection%601>. To umožňuje svázat objekty v relaci s ovládacím prvkem a podporují běžné WPF vazby scénáře, jako je například vzoru vazby seznam podrobnosti pro související entity. V předchozím příkladu XAML, kód XAML naváže hlavní <xref:System.Data.Services.Client.DataServiceCollection%601> do kořenového elementu data. Pořadí <xref:System.Windows.Controls.DataGrid> pak je vázán na objednávky <xref:System.Data.Services.Client.DataServiceCollection%601> vrácená z vybraného objektu zákazníků, který je zase svázán s kořenovým elementem data <xref:System.Windows.Window>.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Vytvoření vazby dat na Windows Forms ovládací prvky  
 Vytvoření vazby objektů k ovládacímu prvku formuláře Windows, nastavte `DataSource` vlastnost ovládacího prvku na instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídu, která obsahuje výsledek dotazu.  
  
> [!NOTE]
>  Datová vazba je podporována pouze pro ovládací prvky, které naslouchají události změn implementací <xref:System.Collections.Specialized.INotifyCollectionChanged> a <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Když ovládací prvek nepodporuje tento typ upozornění na změnu, změny provedené na základní <xref:System.Data.Services.Client.DataServiceCollection%601> se neprojeví v vázaného ovládacího prvku.  
  
 Následující příklad vytvoří vazbu <xref:System.Data.Services.Client.DataServiceCollection%601> k <xref:System.Windows.Forms.ComboBox> ovládacího prvku:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 Při použití **přidat odkaz na službu** dialogovém okně můžete generovat tříd klientské datové služby, projekt je vytvořen zdroj dat také to znamená podle generované <xref:System.Data.Services.Client.DataServiceContext>. S tímto zdrojem dat, můžete vytvořit prvky uživatelského rozhraní nebo ovládací prvky, které zobrazují data z datové služby jednoduše přetažením položek z **zdroje dat** okna do návrháře. Prvky uživatelského rozhraní aplikace, které jsou vázány na zdroj dat se stanou tyto položky. Další informace najdete v tématu [jak: Vytvoření vazby dat pomocí zdroje dat projektu](../../../../docs/framework/data/wcf/how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Vazba stránkovány dat  
 Datovou službu lze nastavit a omezit tak množství načtená data, která je vrácena ve zprávě jednu odpověď. Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Když datové služby je stránkování dat odpovědi, každou odpověď obsahuje odkaz, který se používá k vrácení další stránky výsledků. Další informace najdete v tématu [načítání odložené obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md). V takovém případě musí explicitně načíst stránky voláním <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> metodu na <xref:System.Data.Services.Client.DataServiceCollection%601> předáním získané z identifikátoru URI <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> vlastnosti, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 Podobným způsobem jsou načteny související objekty. Další informace najdete v tématu [jak: Vytvoření vazby dat na elementy Windows Presentation Foundation](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Přizpůsobení chování datových vazeb  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Třída umožňuje zachytit události vyvolané při změně do kolekce, jako například přidávání nebo odebírání objektu a při změně vlastnosti objektu v kolekci. Můžete upravit vazby události dat přepsat výchozí chování, která zahrnuje následující omezení:  
  
-   Žádné ověření se provádí v rámci delegáty.  
  
-   Přidání entity automaticky přidá související entity.  
  
-   Odstraňuje se entita nedojde k odstranění souvisejících entit.  
  
 Když vytvoříte novou instanci třídy <xref:System.Data.Services.Client.DataServiceCollection%601>, máte možnost zadat následující parametry, které definují delegáty pro metody, které zpracovávají události vyvolané při změně vázaným objektům:  
  
-   `entityChanged` -metodu, která je volána, když je změněna vlastnost Vázaný objekt. To <xref:System.Func%602> přijímá delegát <xref:System.Data.Services.Client.EntityChangedParams> objekt a vrátí logickou hodnotu, která určuje, zda výchozí chování volání <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, stále se budou objevovat.  
  
-   `entityCollectionChanged` -metodu, která je volána, když se přidá nebo odebere z kolekce vazbu objektu. To <xref:System.Func%602> přijímá delegát <xref:System.Data.Services.Client.EntityCollectionChangedParams> objekt a vrátí logickou hodnotu, která určuje, zda výchozí chování volání <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> pro <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> akce nebo <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> pro <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> akce <xref:System.Data.Services.Client.DataServiceContext>, stále se budou objevovat.  
  
> [!NOTE]
>  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] ověří žádné vlastní chování, které implementují v tyto delegáty.  
  
 V následujícím příkladu <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> akce upravit tak, aby volání <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> a <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metoda odebrání `Orders_Details` entity, které patří odstraněné `Orders` entity. Tato vlastní akce je provést, protože závislé entit nejsou automaticky odstraněny při nadřazená entita se odstraní.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Další informace najdete v tématu [jak: Přizpůsobení chování datových vazeb](../../../../docs/framework/data/wcf/how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Výchozí chování, pokud je objekt odebrat z <xref:System.Data.Services.Client.DataServiceCollection%601> pomocí <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> metody je, že objekt je také v označen jako odstraněný <xref:System.Data.Services.Client.DataServiceContext>. Chcete-li toto chování změnit, můžete zadat delegáta metodě v `entityCollectionChanged` parametr, který je volána, když <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> dojde k události.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Datové vazby pomocí klienta vlastních datových tříd  
 Bude moct načíst objekty do <xref:System.Data.Services.Client.DataServiceCollection%601>, musí implementovat samotných objektech <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Datová služba třídy klienta, které jsou generovány, pokud použijete **přidat odkaz na službu** dialogové okno nebo [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) toto rozhraní implementují nástroje. Pokud zadáte vlastní datové třídy, musíte použít jiný typ kolekce pro datovou vazbu. Pokud změníte objekty, musí zpracovávat události v ovládacích prvcích data vázaná na tyto metody volat <xref:System.Data.Services.Client.DataServiceContext> třídy:  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> – Při přidání nového objektu do kolekce.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> – Když je objekt odebrat z kolekce.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> – Když se změní vlastnost na objekt v kolekci.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> – Při přidání objektu do kolekce související objekt.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> – Když je objekt přidán ke kolekci souvisejících objektů.  
  
 Další informace najdete v tématu [aktualizace datové služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Ruční generování tříd klientské datové služby](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [Postupy: Přidání odkazu na datovou službu](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
