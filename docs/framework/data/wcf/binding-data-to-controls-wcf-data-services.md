---
title: "Vazba dat s ovládacími prvky (služby WCF Data Services)"
ms.custom: 
ms.date: 03/30/2017
ms.prod: .net-framework-oob
ms.reviewer: 
ms.suite: 
ms.technology: dotnet-clr
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- csharp
- vb
helpviewer_keywords:
- client applications, WCF Data Services
- WCF Data Services, client library
- data binding, WCF Data Services
ms.assetid: b32e1d49-c214-4cb1-867e-88fbb3d08c8d
caps.latest.revision: "3"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.openlocfilehash: ca580801e6bb8786071ec705d4a86d367b02f622
ms.sourcegitcommit: ce279f2d7fe2220e6ea0a25a8a7a5370ddf8d9f0
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/02/2017
---
# <a name="binding-data-to-controls-wcf-data-services"></a>Vazba dat s ovládacími prvky (služby WCF Data Services)
S [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)], lze vázat ovládací prvky, jako `ComboBox` a `ListView` ovládacích prvků do instance systému <xref:System.Data.Services.Client.DataServiceCollection%601> třídy. Tuto kolekci, která dědí z <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy, obsahuje data z [!INCLUDE[ssODataFull](../../../../includes/ssodatafull-md.md)] informačního kanálu. Tato třída reprezentuje kolekci dynamická data, která poskytuje oznámení, pokud získat položky přidány nebo odebrány. Při použití instance <xref:System.Data.Services.Client.DataServiceCollection%601> pro datovou vazbu [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny zpracování těchto událostí k zajištění, že objekty sledovanými <xref:System.Data.Services.Client.DataServiceContext> zůstaly synchronizované s daty v elementu vázané uživatelského rozhraní.  
  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Třídy (nepřímo) implementuje <xref:System.Collections.Specialized.INotifyCollectionChanged> rozhraní pro upozornění kontextu, když jsou objekty přidat nebo odebrat z kolekce. Použít s objekty pro typ dat služby <xref:System.Data.Services.Client.DataServiceCollection%601> musí také implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní výstrahy <xref:System.Data.Services.Client.DataServiceCollection%601> při vlastnosti objektů v kolekci vazby změnily.  
  
> [!NOTE]
>  Při použití **přidat odkaz na službu** dialogové okno nebo[DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroj s `/dataservicecollection` možnost vygenerovat třídy klienta data service, generované datové třídy implementovat <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Další informace najdete v tématu [postupy: ruční generování dat služby třídy klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md).  
  
## <a name="creating-the-binding-collection"></a>Vytváření kolekce vazby  
 Vytvořit novou instanci třídy <xref:System.Data.Services.Client.DataServiceCollection%601> třída při volání jedné z metod třídy konstruktor s zadaný <xref:System.Data.Services.Client.DataServiceContext> instance a volitelně <xref:System.Data.Services.Client.DataServiceQuery%601> nebo LINQ dotazu, který vrátí po spuštění, <xref:System.Collections.Generic.IEnumerable%601> instance. To <xref:System.Collections.Generic.IEnumerable%601> poskytuje zdroj objektů pro kolekci vazby, která jsou nastala z [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] informačního kanálu. Další informace najdete v tématu [Materialization objekt](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). Ve výchozím nastavení, změny provedené v vázaný objekty a položek vložených do kolekce jsou automaticky sledovány objektem <xref:System.Data.Services.Client.DataServiceContext>. Pokud potřebujete ručně sledovat tyto změny, zavolejte jednu z metod konstruktoru, která přebírá `trackingMode` parametr a zadejte hodnotu <xref:System.Data.Services.Client.TrackingMode.None>.  
  
 Následující příklad ukazuje, jak vytvořit instanci <xref:System.Data.Services.Client.DataServiceCollection%601> podle zadaný <xref:System.Data.Services.Client.DataServiceContext> a <xref:System.Data.Services.Client.DataServiceQuery%601> která vrací všechny zákazníky s související objednávky:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders2.cs#customersorders2binding)]
 [!code-vb[Astoria Northwind Client#CustomersOrders2Binding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders2.vb#customersorders2binding)]  
  
## <a name="binding-data-to-windows-presentation-foundation-elements"></a>Vazba dat s Windows Presentation Foundation elementy  
 Protože <xref:System.Data.Services.Client.DataServiceCollection%601> třída dědí z <xref:System.Collections.ObjectModel.ObservableCollection%601> třídu, objekty lze vázat na element nebo ovládací prvek v aplikaci Windows Presentation Foundation (WPF), stejně jako při použití <xref:System.Collections.ObjectModel.ObservableCollection%601> třídy pro vazbu. Další informace najdete v tématu [datové vazby (Windows Presentation Foundation)](../../../../docs/framework/wpf/data/data-binding-wpf.md). Jedním ze způsobů k vytvoření vazby ovládacích prvků WPF dat služby data je nastaven `DataContext` vlastnost elementu k instanci systému <xref:System.Data.Services.Client.DataServiceCollection%601> třídu, která obsahuje výsledek dotazu. V takovém případě použijete <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost nastavující zdrojového objektu ovládacího prvku. Použití <xref:System.Windows.Controls.ItemsControl.DisplayMemberPath%2A> vlastnosti k určení, jehož vlastnost Vázaný objekt k zobrazení. Pokud element vytváříte vazbu na související objekt, který je vrácen navigační vlastnost, zahrnout cestu definované pro vazbu <xref:System.Windows.Controls.ItemsControl.ItemsSource%2A> vlastnost. Tato cesta je relativní vzhledem ke kořenový objekt, který je nastaven <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost nadřazeného ovládacího prvku. Následující příklad nastavuje <xref:System.Windows.FrameworkElement.DataContext%2A> vlastnost <xref:System.Windows.Controls.StackPanel> elementu, který chcete vytvořit vazbu nadřazeného ovládacího prvku do <xref:System.Data.Services.Client.DataServiceCollection%601> objektů zákazníka:  
  
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#masterdetailbinding)]
 [!code-csharp[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf.xaml.cs#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml.vb#masterdetailbinding)]
 [!code-vb[Astoria Northwind Client#MasterDetailBinding](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#masterdetailbinding)]  
  
 Následující příklad ukazuje definici XAML vazby podřízeného <xref:System.Windows.Controls.DataGrid> a <xref:System.Windows.Controls.ComboBox> ovládacích prvků:  
  
 [!code-xaml[Astoria Northwind Client#MasterDetailXaml](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf.xaml#masterdetailxaml)]  
  
 Další informace najdete v tématu [postupy: vytvoření vazby dat Windows Presentation Foundation elementy](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
 Když entity účastní jeden mnoho nebo relace m: n, navigační vlastnost pro relaci vrátí kolekci související objekty. Při použití **přidat odkaz na službu** dialogové okno nebo nástroj DataSvcUtil.exe vygenerovat třídy klienta dat služby navigační vlastnost vrací instanci třídy <xref:System.Data.Services.Client.DataServiceCollection%601>. Můžete vytvořit vazbu související objekty do ovládacího prvku a podpoře běžné WPF vazby scénáře, jako je hlavní podrobné vazby vzor pro související entity. V předchozím příkladu XAML kód XAML váže hlavní <xref:System.Data.Services.Client.DataServiceCollection%601> pro kořenový element data. Pořadí <xref:System.Windows.Controls.DataGrid> je pak vázána objednávky <xref:System.Data.Services.Client.DataServiceCollection%601> vrácená z vybraného objektu zákazníků, který je pak svázaný s kořenový prvek data <xref:System.Windows.Window>.  
  
## <a name="binding-data-to-windows-forms-controls"></a>Vazba dat s Windows Forms – ovládací prvky  
 Chcete-li vytvořit vazbu objekty do ovládacího prvku formuláře Windows, nastavte `DataSource` vlastnost ovládacího prvku na instanci systému <xref:System.Data.Services.Client.DataServiceCollection%601> třídu, která obsahuje výsledek dotazu.  
  
> [!NOTE]
>  Datová vazba je podporována pouze pro ovládací prvky, které čekají na události změn implementací <xref:System.Collections.Specialized.INotifyCollectionChanged> a <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Když ovládacího prvku nepodporuje tento typ oznámení o změně, změny provedené základní <xref:System.Data.Services.Client.DataServiceCollection%601> se neprojeví v připojeného ovládacího prvku.  
  
 Následující příklad vytvoří vazbu <xref:System.Data.Services.Client.DataServiceCollection%601> k <xref:System.Windows.Forms.ComboBox> ovládacího prvku:  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorders.cs#customersordersdatabindingspecific)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDataBindingSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorders.vb#customersordersdatabindingspecific)]  
  
 Při použití **přidat odkaz na službu** dialogovém okně můžete vygenerovat služby třídy dat klienta, projektu zdroj dat je vytvořen také to znamená podle vytvořené <xref:System.Data.Services.Client.DataServiceContext>. S tímto zdrojem dat, můžete vytvořit prvky uživatelského rozhraní nebo ovládací prvky, které zobrazují data ze služby data jednoduše tak, že přetáhnete položky z **zdroje dat** okna do návrháře. Tyto položky stát prvky v uživatelském rozhraní aplikace, které jsou vázány na zdroj dat. Další informace najdete v tématu [postupy: vytvoření vazby dat pomocí zdroj dat projektu](../../../../docs/framework/data/wcf/how-to-bind-data-using-a-project-data-source-wcf-data-services.md).  
  
## <a name="binding-paged-data"></a>Vazba dat stránkovaného fondu  
 Chcete-li omezit množství dotazované dat, která se vrátí ve zprávě odpověď jedné lze nakonfigurovat datové služby. Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Když služba dat je stránkování data odpovědi, každá odpověď obsahuje odkaz, který se používá k vrácení další stránky výsledků. Další informace najdete v tématu [načítání odložení obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md). V takovém případě musí explicitně načtení stránek voláním <xref:System.Data.Services.Client.DataServiceCollection%601.Load%2A> metodu <xref:System.Data.Services.Client.DataServiceCollection%601> předáním identifikátor URI získané z <xref:System.Data.Services.Client.DataServiceQueryContinuation.NextLinkUri%2A> vlastnosti, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderswpf3.xaml.cs#bindpageddataspecific)]
 [!code-vb[Astoria Northwind Client#BindPagedDataSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderswpf3.xaml.vb#bindpageddataspecific)]  
  
 Souvisejících objektů, které jsou načteny podobným způsobem. Další informace najdete v tématu [postupy: vytvoření vazby dat Windows Presentation Foundation elementy](../../../../docs/framework/data/wcf/bind-data-to-wpf-elements-wcf-data-services.md).  
  
## <a name="customizing-data-binding-behaviors"></a>Datové vazby chování přizpůsobení  
 <xref:System.Data.Services.Client.DataServiceCollection%601> Třída umožňuje zachytit události vyvolané při provedení změn do kolekce, jako například přidávání nebo odebírání objekt a provedení změn vlastnosti objektu v kolekci. Můžete upravit události vazby dat, které chcete přepsat výchozí chování, která zahrnuje následující omezení:  
  
-   Žádné ověření se provádí v rámci delegáty.  
  
-   Přidání entity automaticky přidá entit v relaci.  
  
-   Odstranění entity nedojde k odstranění entit v relaci.  
  
 Když vytvoříte novou instanci třídy <xref:System.Data.Services.Client.DataServiceCollection%601>, máte možnost zadat následující parametry, které definuje Delegáti a metody, které zpracování událostí vyvolá, když se změní vázaným objektům:  
  
-   `entityChanged`-metodu, která je volána, když vlastnost vázané objektu se změní. To <xref:System.Func%602> delegát přijme <xref:System.Data.Services.Client.EntityChangedParams> objektu a vrací logickou hodnotu, která určuje, zda výchozí chování volání <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A> na <xref:System.Data.Services.Client.DataServiceContext>, má stále probíhat.  
  
-   `entityCollectionChanged`-metodu, která je volána, když je objekt přidat nebo odebrat z kolekce vazby. To <xref:System.Func%602> delegát přijme <xref:System.Data.Services.Client.EntityCollectionChangedParams> objektu a vrací logickou hodnotu, která určuje, zda výchozí chování volání <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A> pro <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Add> akce nebo <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> pro <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> akce <xref:System.Data.Services.Client.DataServiceContext>, má stále probíhat.  
  
> [!NOTE]
>  [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]provede žádné ověření vlastní chování, které implementují v těchto delegáti.  
  
 V následujícím příkladu <xref:System.Collections.Specialized.NotifyCollectionChangedAction.Remove> akce upravit tak, aby volání <xref:System.Data.Services.Client.DataServiceContext.DeleteLink%2A> a <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A> metoda odebrat `Orders_Details` entit, které patří odstraněné `Orders` entity. Tato vlastní akce se provádí, protože závislé entity nejsou automaticky odstraněny při odstranění nadřazená entita.  
  
 [!code-csharp[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/customerorderscustom.xaml.cs#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom.xaml.vb#customersordersdeleterelated)]
 [!code-vb[Astoria Northwind Client#CustomersOrdersDeleteRelated](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/customerorderscustom2.xaml.vb#customersordersdeleterelated)]  
  
 Další informace najdete v tématu [postupy: přizpůsobení chování vazby dat](../../../../docs/framework/data/wcf/how-to-customize-data-binding-behaviors-wcf-data-services.md).  
  
 Výchozí chování, pokud objekt je odebrán z <xref:System.Data.Services.Client.DataServiceCollection%601> pomocí <xref:System.Collections.ObjectModel.Collection%601.Remove%2A> metoda je, že objekt je také označena k odstranění v <xref:System.Data.Services.Client.DataServiceContext>. Chcete-li toto chování změnit, můžete zadat delegátovi, aby se metoda v `entityCollectionChanged` parametr, který je volána, když <xref:System.Collections.Specialized.INotifyCollectionChanged.CollectionChanged> dojde k události.  
  
## <a name="data-binding-with-custom-client-data-classes"></a>Datové vazby pomocí klienta vlastních datových tříd  
 Abyste mohli načíst objekty do <xref:System.Data.Services.Client.DataServiceCollection%601>, musí implementovat samotných objektech <xref:System.ComponentModel.INotifyPropertyChanged> rozhraní. Data služby třídy klienta, které jsou generovány, pokud použijete **přidat odkaz na službu** dialogové okno nebo [DataSvcUtil.exe](../../../../docs/framework/data/wcf/wcf-data-service-client-utility-datasvcutil-exe.md) nástroj pro toto rozhraní implementovat. Pokud jste zadali vlastní klienta datových tříd, musíte použít jiný typ kolekce pro datovou vazbu. Při změně objektů, je nutné zpracovat události v ovládacích prvcích data vázaná volat tyto metody <xref:System.Data.Services.Client.DataServiceContext> třídy:  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AddObject%2A>– Když nový objekt, který se přidá do kolekce.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.DeleteObject%2A>-Pokud je objekt z kolekce odebrán.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.UpdateObject%2A>-Při změně vlastnosti na objekt v kolekci.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.AddLink%2A>-Pokud je objekt přidat do kolekce související objekt.  
  
-   <xref:System.Data.Services.Client.DataServiceContext.SetLink%2A>-Pokud je objekt přidat do kolekce související objekty.  
  
 Další informace najdete v tématu [aktualizaci dat služby](../../../../docs/framework/data/wcf/updating-the-data-service-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Postupy: ručně generovat třídy služeb dat klienta](../../../../docs/framework/data/wcf/how-to-manually-generate-client-data-service-classes-wcf-data-services.md)  
 [Postupy: Přidání odkazu na službu Data](../../../../docs/framework/data/wcf/how-to-add-a-data-service-reference-wcf-data-services.md)
