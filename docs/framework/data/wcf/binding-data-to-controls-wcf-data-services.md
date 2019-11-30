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
ms.openlocfilehash: ab75380738064a001b12e79d1481d053622077ef
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74569327"
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Vázání dat na ovládací prvky (WCF Data Services)
Pomocí WCF Data Services můžete navazovat ovládací prvky, jako jsou ovládací prvky `ComboBox` a `ListView`, na instanci třídy <xref:System.Data.Services.Client.DataServiceCollection%601>. Tato kolekce, která dědí z třídy <xref:System.Collections.ObjectModel.ObservableCollection%601>, obsahuje data z informačního kanálu typu Open Data Protocol (OData). Tato třída reprezentuje dynamický sběr dat, který poskytuje oznámení, když se položky přidají nebo odeberou. Použijete-li instanci <xref:System.Data.Services.Client.DataServiceCollection%601> pro datovou vazbu, aplikace WCF Data Services klientské knihovny tyto události zpracuje, aby bylo zajištěno, že objekty sledované <xref:System.Data.Services.Client.DataServiceContext> zůstávají synchronizovány s daty v vázaném prvku uživatelského rozhraní.  
  
 Třída <xref:System.Data.Services.Client.DataServiceCollection%601> (nepřímo) implementuje rozhraní <xref:System.Collections.Specialized.INotifyCollectionChanged> a upozorní kontext, když jsou objekty přidány nebo odebrány z kolekce. Objekty typu datové služby použité s <xref:System.Data.Services.Client.DataServiceCollection%601> musí implementovat rozhraní <xref:System.ComponentModel.INotifyPropertyChanged>, aby se zobrazila výstraha <xref:System.Data.Services.Client.DataServiceCollection%601> v případě, že se změnily vlastnosti objektů v kolekci vazeb.  
  
> [!NOTE]
> Při použití dialogového okna **Přidat odkaz na službu** nebo nástroje [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) s možností `/dataservicecollection` pro vygenerování tříd klientské datové služby, vygenerované datové třídy implementují rozhraní <xref:System.ComponentModel.INotifyPropertyChanged>. Další informace najdete v tématu [Postup: ruční generování tříd klientských datových služeb](how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Vytváření kolekce vazeb  
 Vytvořte novou instanci třídy <xref:System.Data.Services.Client.DataServiceCollection%601> voláním jedné z metod konstruktoru třídy s dodanou instancí <xref:System.Data.Services.Client.DataServiceContext> a volitelně také dotaz <xref:System.Data.Services.Client.DataServiceQuery%601> nebo LINQ, který při spuštění vrátí instanci <xref:System.Collections.Generic.IEnumerable%601>. Tento <xref:System.Collections.Generic.IEnumerable%601> poskytuje zdroj objektů pro kolekci vazeb, které jsou materializované z datového kanálu OData. Další informace naleznete v tématu [materializace objektů](object-materialization-wcf-data-services.md). Ve výchozím nastavení jsou změny provedené u vázaných objektů a položek vložených do kolekce automaticky sledovány <xref:System.Data.Services.Client.DataServiceContext>. Pokud potřebujete tyto změny sledovat ručně, zavolejte jednu z metod konstruktoru, která přebírá parametr `trackingMode` a zadejte hodnotu <xref:System.Data.Services.Client.TrackingMode.None>.  
  
 Následující příklad ukazuje, jak vytvořit instanci <xref:System.Data.Services.Client.DataServiceCollection%601> založenou na poskytnuté <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601>, která vrací všechny zákazníky se souvisejícími objednávkami:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Vázání dat na prvky Windows Presentation Foundation  
 Vzhledem k tomu, že třída <xref:System.Data.Services.Client.DataServiceCollection%601> dědí z třídy <xref:System.Collections.ObjectModel.ObservableCollection%601>, lze objekty svázat s elementem nebo ovládacím prvkem v aplikaci Windows Presentation Foundation (WPF) jako při použití třídy <xref:System.Collections.ObjectModel.ObservableCollection%601> pro vytváření vazby. Další informace najdete v tématu [datová vazba (Windows Presentation Foundation)](../../../desktop-wpf/data/data-binding-overview.md). Jedním ze způsobů, jak vytvořit vazby dat datové služby k ovládacím prvkům WPF, je nastavit vlastnost `DataContext` elementu na instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídy, která obsahuje výsledek dotazu. V tomto případě použijete vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> k nastavení zdroje objektu pro ovládací prvek. Vlastnost <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> slouží k určení vlastnosti vázaného objektu, který se má zobrazit. Pokud vytváříte vazbu elementu k souvisejícímu objektu, který je vrácen vlastností navigace, zahrňte cestu do vazby definované pro vlastnost <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A>. Tato cesta je relativní vzhledem ke kořenovému objektu nastavenému vlastností <xref:System.Windows.FrameworkElement.DataContext%2A> nadřazeného ovládacího prvku. Následující příklad nastaví vlastnost <xref:System.Windows.FrameworkElement.DataContext%2A> <xref:System.Windows.Controls.StackPanel> elementu pro svázání nadřazeného ovládacího prvku s <xref:System.Data.Services.Client.DataServiceCollection%601> zákaznických objektů:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Následující příklad ukazuje definici vazby XAML podřízených <xref:System.Windows.Controls.DataGrid> a <xref:System.Windows.Controls.ComboBox> ovládací prvky:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Další informace naleznete v tématu [How to: bind data to Windows Presentation Foundation Elements](bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Když se entita účastní relace 1: n nebo m:n, vlastnost navigace pro relaci vrátí kolekci souvisejících objektů. Když použijete dialogové okno **Přidat odkaz na službu** nebo nástroj DataSvcUtil. exe ke generování tříd klientských dat, vlastnost navigace vrátí instanci <xref:System.Data.Services.Client.DataServiceCollection%601>. To umožňuje svázat související objekty s ovládacím prvkem a podporovat běžné scénáře vazeb WPF, jako je například vzor vazby master-detail pro související entity. V předchozím příkladu XAML vytvoří kód XAML hlavní <xref:System.Data.Services.Client.DataServiceCollection%601> k kořenovému datovému elementu. Pořadí <xref:System.Windows.Controls.DataGrid> se pak sváže s objednávkami <xref:System.Data.Services.Client.DataServiceCollection%601> vrácenými z vybraných objektů Customers, které jsou následně vázány na kořenový datový prvek <xref:System.Windows.Window>.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Svázání dat s ovládacími prvky model Windows Forms  
 Chcete-li vytvořit vazby objektů k ovládacímu prvku formuláře systému Windows, nastavte vlastnost `DataSource` ovládacího prvku na instanci <xref:System.Data.Services.Client.DataServiceCollection%601> třídy, která obsahuje výsledek dotazu.  
  
> [!NOTE]
> Datová vazba je podporována pouze pro ovládací prvky, které naslouchají událostem změny implementací rozhraní <xref:System.Collections.Specialized.INotifyCollectionChanged> a <xref:System.ComponentModel.INotifyPropertyChanged>. Pokud ovládací prvek nepodporuje tento druh oznámení změny, změny provedené v podkladovém <xref:System.Data.Services.Client.DataServiceCollection%601> se neprojeví v ovládacím prvku Bound.  
  
 Následující příklad váže <xref:System.Data.Services.Client.DataServiceCollection%601> k ovládacímu prvku <xref:System.Windows.Forms.ComboBox>:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 Když použijete dialogové okno **Přidat odkaz na službu** k vygenerování tříd klientských datových služeb, vytvoří se také zdroj dat projektu, který je založen na vygenerované <xref:System.Data.Services.Client.DataServiceContext>. Pomocí tohoto zdroje dat můžete vytvořit prvky uživatelského rozhraní nebo ovládací prvky, které zobrazují data z datové služby pouhým přetažením položek z okna **zdroje dat** do návrháře. Tyto položky se stanou prvky v uživatelském rozhraní aplikace, které jsou svázány se zdrojem dat. Další informace naleznete v tématu [How to: bind data using a Project Data Source](how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Vázání stránkovaných dat  
 Datovou službu lze nakonfigurovat tak, aby omezila množství dotazovaného data vráceného v rámci jedné zprávy odpovědi. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md). Pokud datová služba obsahuje data odezvy stránkování, obsahuje každá odpověď odkaz, který se používá k vrácení další stránky výsledků. Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md). V tomto případě je nutné explicitně načíst stránky voláním metody <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> na <xref:System.Data.Services.Client.DataServiceCollection%601> předáním identifikátoru URI získaného z vlastnosti <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A>, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 Související objekty jsou načteny podobným způsobem. Další informace naleznete v tématu [How to: bind data to Windows Presentation Foundation Elements](bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Přizpůsobení chování datových vazeb  
 Třída <xref:System.Data.Services.Client.DataServiceCollection%601> umožňuje zachytit události vyvolané při provedení změn v kolekci, jako je například přidání nebo odebrání objektu, a když jsou provedeny změny vlastností objektu v kolekci. Můžete upravit události datové vazby a přepsat tak výchozí chování, což zahrnuje následující omezení:  
  
- V rámci delegátů se neprovede žádné ověření.  
  
- Přidání entity automaticky přidá související entity.  
  
- Odstraněním entity se neodstraňují související entity.  
  
 Při vytváření nové instance <xref:System.Data.Services.Client.DataServiceCollection%601>máte možnost zadat následující parametry, které definují delegáty pro metody, které zpracovávají události vyvolané při změně vázaného objektu:  
  
- `entityChanged` – metoda, která se volá, když se změní vlastnost vázaného objektu. Tento <xref:System.Func%602> delegát přijímá objekt <xref:System.Data.Services.Client.EntityChangedParams> a vrátí logickou hodnotu, která označuje, zda má být ve <xref:System.Data.Services.Client.DataServiceContext>stále k dis výchozí chování volání <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>.  
  
- `entityCollectionChanged` – metoda, která se volá při přidání nebo odebrání objektu z kolekce vazeb. Tento <xref:System.Func%602> delegát přijímá objekt <xref:System.Data.Services.Client.EntityCollectionChangedParams> a vrátí logickou hodnotu, která označuje, zda výchozí chování volání <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> pro <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> akci nebo <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> pro akci <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> na <xref:System.Data.Services.Client.DataServiceContext>by mělo stále probíhat.  
  
> [!NOTE]
> WCF Data Services neprovede žádné ověření vlastního chování, které implementujete v těchto delegátech.  
  
 V následujícím příkladu je akce <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> přizpůsobena pro volání metody <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> a <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> k odebrání `Orders_Details` entit, které patří k odstraněné `Orders` entitě. Tato vlastní akce se provede, protože závislé entity se při odstranění nadřazené entity neodstraní automaticky.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Další informace naleznete v tématu [How to: Customize a Behavior Binding](how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Výchozí chování při odebrání objektu z <xref:System.Data.Services.Client.DataServiceCollection%601> pomocí metody <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> je, že objekt je také označen jako odstraněný v <xref:System.Data.Services.Client.DataServiceContext>. Chcete-li toto chování změnit, můžete zadat delegáta metody v parametru `entityCollectionChanged`, který je volán při výskytu události <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged>.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Datová vazba s vlastními třídami dat klienta  
 Aby bylo možné načíst objekty do <xref:System.Data.Services.Client.DataServiceCollection%601>, samotné objekty musí implementovat rozhraní <xref:System.ComponentModel.INotifyPropertyChanged>. Třídy klienta datové služby, které jsou generovány při použití dialogového okna **Přidat odkaz na službu** nebo pomocí nástroje [DataSvcUtil. exe](wcf-data-service-client-utility-datasvcutil-exe.md) implementují toto rozhraní. Pokud zadáte vlastní klientské třídy dat, je nutné použít jiný typ kolekce pro datovou vazbu. Když se objekty změní, je nutné zpracovat události v ovládacích prvcích vázaných na data pro volání následujících metod <xref:System.Data.Services.Client.DataServiceContext> třídy:  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> – při přidání nového objektu do kolekce.  
  
- <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> – při odebrání objektu z kolekce.  
  
- <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> – když se u objektu v kolekci změní vlastnost.  
  
- <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A> – když se objekt přidá do kolekce souvisejících objektů.  
  
- <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A> – když se objekt přidá do kolekce souvisejících objektů.  
  
 Další informace najdete v tématu [aktualizace datové služby](updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Postupy: Ruční generování tříd klientské datové služby](how-to-manually-generate-client-data-service-classes-wcf-data-services.md)
- [Postupy: Přidání odkazu na datovou službu](how-to-add-a-data-service-reference-wcf-data-services.md)
