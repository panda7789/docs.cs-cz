---
title: Odložené načtení obsahu (služby WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: 8ab4dea9e4f687f9548bb2b46a8f6baf428e29af
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
---
# <a name="loading-deferred-content-wcf-data-services"></a>Odložené načtení obsahu (služby WCF Data Services)
Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] omezení množství dat, který vrací dotaz. Je však explicitně načíst další data, včetně entit v relaci, data stránkové odpovědi a binární datové proudy z službu data, když je to potřeba. Toto téma popisuje, jak načíst takový odložené obsah do vaší aplikace.  
  
## <a name="related-entities"></a>Související entity  
 Při spuštění dotazu se vrátí jenom entity v sadě adresovaný entit. Například, když vrací dotazy na službu data Northwind `Customers` entity ve výchozím nastavení související `Orders` entity nebudou zobrazeny, i když je vztah mezi `Customers` a `Orders`. Navíc pokud je stránkování povoleno ve službě data, je nutné explicitně načíst stránky následná data ze služby. Existují dva způsoby, jak načíst entit v relaci:  
  
-   **Přes načítání**: můžete použít `$expand` možnost dotazu do požadavku, že dotaz vrátí entity, které jsou spojené přidružení k entitě nastavit požadovaný dotaz. Použití <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metodu <xref:System.Data.Services.Client.DataServiceQuery%601> přidat `$expand` možnost dotazu, který je odešle do služby data. Může požádat o sady více související entity oddělte je čárkou, jako v následujícím příkladu. V jedné odpovědi budou vráceny všechny entity požadoval dotazu. Následující příklad vrací `Order_Details` a `Customers` společně s `Orders` sady entit:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] omezuje na 12 počet sad entit, které můžou být součástí jediný dotaz pomocí `$expand` možnost dotazu.  
  
-   **Explicitní načítání**: můžete volat <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> instance explicitně načíst entit v relaci. Každé volání <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metoda vytvoří samostatné žádosti o službu data. Následující příklad načte explicitně `Order_Details` pro `Orders` entity:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Při zvažování možnost provedení Uvědomte si, že je kompromis mezi počet požadavků na službu data a množství dat, která je vrácena v odpověď o jedné. Použijte přes načítání, když vaše aplikace vyžaduje přidružených objektů a budete chtít vyhnout přidané latence dalších žádostí je explicitně načíst. Ale pokud existují případy, pokud aplikace potřebuje pouze data pro konkrétní související entity instance, měli byste zvážit explicitně načítání tyto entity voláním <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metoda. Další informace najdete v tématu [postupy: načtení entit v relaci](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Stránkové obsahu  
 Pokud je stránkování povoleno ve službě data, je omezen počet položek v informačním kanálu, že data služby vrátí konfigurace datové služby. Omezení stránce můžete nastavit samostatně pro každou sadu entit. Další informace najdete v tématu [konfigurace službu Data](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Pokud je povoleno stránkování, poslední položku v informačním kanálu obsahuje odkaz na další stránku data. Tento odkaz je součástí <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> objektu. Získat identifikátor URI na další stránku dat voláním <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metodu <xref:System.Data.Services.Client.QueryOperationResponse%601> vrácená při <xref:System.Data.Services.Client.DataServiceQuery%601> se spustí. Vrácený <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> objekt se pak použije k načtení další stránky výsledků. Před voláním musíte vytvořit výčet výsledek dotazu <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metoda. Zvažte použití `do…while` opakování ve smyčce bude nejprve vytvořit výčet výsledek dotazu a poté vyhledejte `non-null` hodnotu odkazu na další stránku. Když <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metoda vrátí `null` (`Nothing` v jazyce Visual Basic), nejsou žádné další výsledek stránky pro původní dotaz. Následující příklad ukazuje `do…while` smyčky, který načítá stránkovaného zákaznická data ze služby Northwind ukázková data.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadnextlink)]  
  
 Pokud jsou požadavky na dotaz, které související entity vrácené v odpověď o jedné společně s sadu požadovaná entita, stránkování omezení může mít vliv na vnořené informační kanály, které jsou zahrnuty vložené s odpovědí. Například pokud je stránkování limit nastavena ve službě Northwind ukázkových dat pro `Customers` sady entit, nezávislé stránkování limit můžete také nastavit pro související `Orders` entit nastaven, jako v následujícím příkladu z Northwind.svc.cs souboru, který Definuje službu Northwind ukázková data.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 V takovém případě je nutné implementovat stránkování pro obě nejvyšší úrovně `Customers` a vnořeného `Orders` entity informačních kanálů. Následující příklad ukazuje `while` smyčky používá k načtení stránek z `Orders` entity související s vybrané `Customers` entity.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#loadnextorderslink)]  
  
 Další informace najdete v tématu [postup: výsledky stránkovaného fondu zatížení](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Binární datové proudy  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje přístup k datům binární rozsáhlý objekt (binární rozsáhlý OBJEKT) jako datový proud. Streamování odkládat údaje načítání binárních dat, dokud je to potřeba, a klient efektivněji zpracovávat tato data. Chcete-li tuto funkci využít, musí implementovat službu data <xref:System.Data.Services.Providers.IDataServiceStreamProvider> zprostředkovatele. Další informace najdete v tématu [streamování zprostředkovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md). Pokud je povoleno vysílání datového proudu, typy entit jsou vráceny bez související binární data. V takovém případě musíte použít <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> třídy pro přístup k datový proud pro binární data ze služby. Podobně lze použít <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodu pro přidání nebo změna binární data pro entitu jako datový proud. Další informace najdete v tématu [práce s binární Data](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)  
 [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
