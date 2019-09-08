---
title: Vázání dat na ovládací prvky (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
ms.openlocfilehash: 3607b7e985bfaa081c003c1a7c59a26578156eb7
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70780495"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Vázání dat na ovládací prvky (WCF Data Services)
Pomocí [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]nástroje můžete navazovat ovládací prvky, jako `ComboBox` jsou `ListView` ovládací prvky a, na instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídy. Tato kolekce, která dědí z <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy, obsahuje data [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] z informačního kanálu. Tato třída reprezentuje dynamický sběr dat, který poskytuje oznámení, když se položky přidají nebo odeberou. Použijete-li instanci <xref:System.Data.Services.Client.DataServiceCollection%601> pro datovou vazbu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , klientské knihovny tyto události zpracují, aby bylo zajištěno, že objekty <xref:System.Data.Services.Client.DataServiceContext> , které jsou sledovány, zůstávají synchronizované s daty v vázaném prvku uživatelského rozhraní.  
  
 Třída (nepřímo) <xref:System.Collections.Specialized.INotifyCollectionChanged> implementuje rozhraní pro upozornění kontextu při přidání nebo odebrání objektů z kolekce. <xref:System.Data.Services.Client.DataServiceCollection%601> Objekty typu datové služby použité s a <xref:System.Data.Services.Client.DataServiceCollection%601> musí také <xref:System.ComponentModel.INotifyPropertyChanged> implementovat rozhraní, aby se zobrazila výstraha, <xref:System.Data.Services.Client.DataServiceCollection%601> když se změní vlastnosti objektů v kolekci vazeb.  
  
> [!NOTE]
> Při použití dialogového okna **Přidat odkaz na službu** nebo `/dataservicecollection` nástroje [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) s možností pro vygenerování tříd klientské datové služby, vygenerované datové třídy implementují <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [jak: Ručně vygenerujte třídy](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)datové služby klienta.  
  
## <a name="creating-the-binding-collection"></a>Vytváření kolekce vazeb  
 Vytvořte novou instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídy voláním jedné z metod konstruktoru třídy se zadanou <xref:System.Data.Services.Client.DataServiceContext> instancí a případně <xref:System.Data.Services.Client.DataServiceQuery%601> dotazem LINQ, který při spuštění vrátí <xref:System.Collections.Generic.IEnumerable%601> instanci. To <xref:System.Collections.Generic.IEnumerable%601> poskytuje zdroj objektů pro kolekci vazeb, které jsou materializované [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] z informačního kanálu. Další informace naleznete v tématu [materializace objektů](object-materialization-wcf-data-services.md). Ve výchozím nastavení jsou změny provedené u vázaných objektů a položek vložených do kolekce automaticky sledovány pomocí <xref:System.Data.Services.Client.DataServiceContext>. Pokud potřebujete tyto změny sledovat ručně, zavolejte jednu z metod konstruktoru, která převezme `trackingMode` parametr a zadejte <xref:System.Data.Services.Client.TrackingMode.None>hodnotu.  
  
 Následující příklad ukazuje, jak vytvořit instanci <xref:System.Data.Services.Client.DataServiceCollection%601> založenou na zadané <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601> , která vrací všechny zákazníky se souvisejícími objednávkami:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Vázání dat na prvky Windows Presentation Foundation  
 Vzhledem k tomu, že <xref:System.Collections.ObjectModel.ObservableCollection%601> <xref:System.Collections.ObjectModel.ObservableCollection%601>Třídadědí z třídy, můžete objekty svázat s elementem nebo ovládacím prvkem v aplikaci Windows Presentation Foundation (WPF) jako při použití třídy pro vazbu. <xref:System.Data.Services.Client.DataServiceCollection%601> Další informace najdete v tématu [datová vazba (Windows Presentation Foundation)](../../wpf/data/data-binding-wpf.md). Jedním ze způsobů, jak vytvořit vazby dat datové služby k ovládacím prvkům `DataContext` WPF, je nastavit vlastnost elementu na instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídy, která obsahuje výsledek dotazu. V tomto případě použijete <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost k nastavení zdroje objektu pro ovládací prvek. <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> Vlastnost použijte k určení vlastnosti vázaného objektu, který se má zobrazit. Pokud vytváříte vazbu elementu k souvisejícímu objektu, který je vrácen vlastností navigace, zahrňte cestu do vazby definované pro <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost. Tato cesta je relativní vzhledem ke kořenovému objektu nastavenému <xref:System.Windows.FrameworkElement.DataContext%2A> vlastností nadřazeného ovládacího prvku. Následující příklad nastaví <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> elementu pro svázání nadřazeného ovládacího prvku s <xref:System.Data.Services.Client.DataServiceCollection%601> objekty zákazníka:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Následující příklad ukazuje definici vazby XAML podřízených <xref:System.Windows.Controls.DataGrid> a <xref:System.Windows.Controls.ComboBox> ovládacích prvků:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Další informace najdete v tématu [jak: Navažte data na prvky](bind-data-to-wpf-elements-wcf-data-services.md)Windows Presentation Foundation.  
  
 Když se entita účastní relace 1: n nebo m:n, vlastnost navigace pro relaci vrátí kolekci souvisejících objektů. Při použití dialogového okna **Přidat odkaz na službu** nebo nástroje DataSvcUtil. exe k vygenerování tříd klientských datových služeb vrátí vlastnost navigace instanci <xref:System.Data.Services.Client.DataServiceCollection%601>. To umožňuje svázat související objekty s ovládacím prvkem a podporovat běžné scénáře vazeb WPF, jako je například vzor vazby master-detail pro související entity. V předchozím příkladu XAML vytvoří kód XAML hlavní <xref:System.Data.Services.Client.DataServiceCollection%601> prvek s kořenovým datovým prvkem. Pořadí <xref:System.Windows.Controls.DataGrid> je pak svázáno s objednávkami <xref:System.Data.Services.Client.DataServiceCollection%601> vrácenými vybraným objektem Customers, které jsou následně vázány na <xref:System.Windows.Window>kořenový datový prvek.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Svázání dat s ovládacími prvky model Windows Forms  
 Chcete-li vytvořit vazby objektů k ovládacímu prvku formuláře `DataSource` systému Windows, nastavte vlastnost ovládacího prvku na instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídy, která obsahuje výsledek dotazu.  
  
> [!NOTE]
> Datová vazba je podporována pouze pro ovládací prvky, které naslouchají událostem změny <xref:System.Collections.Specialized.INotifyCollectionChanged> implementací rozhraní a <xref:System.ComponentModel.INotifyPropertyChanged> . Pokud ovládací prvek nepodporuje tento druh oznámení změny, změny provedené v podkladu <xref:System.Data.Services.Client.DataServiceCollection%601> se neprojeví v ovládacím prvku Bound.  
  
 V následujícím příkladu se váže <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Windows.Forms.ComboBox> k ovládacímu prvku:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 Když použijete dialogové okno **Přidat odkaz na službu** k vygenerování tříd klientských datových služeb, vytvoří se také zdroj dat projektu, který je založen na generovaném <xref:System.Data.Services.Client.DataServiceContext>. Pomocí tohoto zdroje dat můžete vytvořit prvky uživatelského rozhraní nebo ovládací prvky, které zobrazují data z datové služby pouhým přetažením položek z okna **zdroje dat** do návrháře. Tyto položky se stanou prvky v uživatelském rozhraní aplikace, které jsou svázány se zdrojem dat. Další informace najdete v tématu [jak: Vázání dat pomocí zdroje](how-to-bind-data-using-a-project-data-source-wcf-data-services.md)dat projektu.  
  
## <a name="binding-paged-data"></a>Vázání stránkovaných dat  
 Datovou službu lze nakonfigurovat tak, aby omezila množství dotazovaného data vráceného v rámci jedné zprávy odpovědi. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md). Pokud datová služba obsahuje data odezvy stránkování, obsahuje každá odpověď odkaz, který se používá k vrácení další stránky výsledků. Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md). V tomto případě je nutné explicitně načíst stránky voláním <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> metody na rozhraní <xref:System.Data.Services.Client.DataServiceCollection%601> předáním identifikátoru URI získaného z <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> vlastnosti, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 Související objekty jsou načteny podobným způsobem. Další informace najdete v tématu [jak: Navažte data na prvky](bind-data-to-wpf-elements-wcf-data-services.md)Windows Presentation Foundation.  
  
## <a name="customizing-data-binding-behaviors"></a>Přizpůsobení chování datových vazeb  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Třída umožňuje zachytit události vyvolané při provedení změn v kolekci, jako je například přidání nebo odebrání objektu, a když jsou provedeny změny vlastností objektu v kolekci. Můžete upravit události datové vazby a přepsat tak výchozí chování, což zahrnuje následující omezení:  
  
- V rámci delegátů se neprovede žádné ověření.  
  
- Přidání entity automaticky přidá související entity.  
  
- Odstraněním entity se neodstraňují související entity.  
  
 Při vytváření nové instance <xref:System.Data.Services.Client.DataServiceCollection%601>nástroje máte možnost zadat následující parametry, které definují delegáty pro metody, které zpracovávají události vyvolané při změně vázaného objektu:  
  
- `entityChanged`-a metoda, která je volána, když dojde ke změně vlastnosti vázaného objektu. Tento <xref:System.Func%602> delegát <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> <xref:System.Data.Services.Client.DataServiceContext>přijme objekt a vrátí logickou hodnotu, která označuje, zda má být k dismomentaci výchozí chování volání metody. <xref:System.Data.Services.Client.EntityChangedParams>  
  
- `entityCollectionChanged`– Metoda, která je volána při přidání nebo odebrání objektu z kolekce vazeb. Tento <xref:System.Func%602> delegát <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> přijme objekt a vrátí logickou hodnotu, která označuje, zda výchozí chování, volání akce nebo akce v <xref:System.Data.Services.Client.EntityCollectionChangedParams> <xref:System.Data.Services.Client.DataServiceContext>by měl stále probíhat.  
  
> [!NOTE]
> [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]neprovede žádné ověření vlastního chování, které implementujete v těchto delegátech.  
  
 <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> V následujícím příkladu je akce přizpůsobena <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> voláním metody a k odebrání `Orders_Details` entit, které patří k odstraněné `Orders` entitě. Tato vlastní akce se provede, protože závislé entity se při odstranění nadřazené entity neodstraní automaticky.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Další informace najdete v tématu [jak: Přizpůsobení chování](how-to-customize-data-binding-behaviors-wcf-data-services.md)datových vazeb.  
  
 Výchozí chování při odebrání objektu z <xref:System.Data.Services.Client.DataServiceCollection%601> <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> pomocí metody je, že objekt je také <xref:System.Data.Services.Client.DataServiceContext>označen jako odstraněný v. Chcete-li toto chování změnit, můžete zadat delegáta metody v `entityCollectionChanged` parametru, který je volán <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> při výskytu události.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Datová vazba s vlastními třídami dat klienta  
 Aby bylo možné načíst objekty do <xref:System.Data.Services.Client.DataServiceCollection%601>, samotné objekty musí <xref:System.ComponentModel.INotifyPropertyChanged> implementovat rozhraní. Třídy klienta datové služby, které jsou generovány při použití dialogového okna **Přidat odkaz na službu** nebo pomocí nástroje [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) implementují toto rozhraní. Pokud zadáte vlastní klientské třídy dat, je nutné použít jiný typ kolekce pro datovou vazbu. Když se objekty změní, je nutné zpracovat události v ovládacích prvcích vázaných na data pro volání následujících metod <xref:System.Data.Services.Client.DataServiceContext> třídy:  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>– Když se do kolekce přidá nový objekt.  
  
- <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A>– Při odebrání objektu z kolekce.  
  
- <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>– Když se u objektu v kolekci změní vlastnost.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>– Když je objekt přidán do kolekce souvisejících objektů.  
  
- <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>– Když je objekt přidán do kolekce souvisejících objektů.  
  
 Další informace najdete v tématu [aktualizace datové služby](updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Ruční generování tříd klientských datových služeb](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [Postupy: Přidat odkaz na datovou službu](how-to-add-a-data-service-reference-wcf-data-services.md)
