---
title: Načtení odloženého obsahu (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: ee7b0b40d74d908dc4f25372273f852662370df0
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59518003"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Načtení odloženého obsahu (WCF Data Services)
Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] omezuje množství dat, které dotaz vrátí. Můžete však explicitně načíst další data, včetně souvisejících entit, data stránkované odpovědi a binární datové proudy z datové služby, když ho nepotřebují. Toto téma popisuje, jak načíst takového odloženého obsahu do vaší aplikace.  
  
## <a name="related-entities"></a>Související entity  
 Při spouštění dotazu budou vráceny pouze entity v sadě entit adresovaný. Když dotaz proti datová služba Northwind například vrátí `Customers` entity, ve výchozím nastavení související `Orders` nejsou vráceny entity, i když existuje vztah mezi `Customers` a `Orders`. Také když je stránkování povoleno v datové službě, je nutné explicitně načíst stránky následná data ze služby. Existují dva způsoby, jak načíst související entity:  
  
-   **Předběžné načítání**: Můžete použít `$expand` možností dotazu žádosti, že dotaz vrátí entity, které se týkají přidružení k entitě nastavte požadovaný dotaz. Použití <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> metodu na <xref:System.Data.Services.Client.DataServiceQuery%601> přidáte `$expand` možnost Dotaz odeslaný do služby data. Můžete požádat o více související entity sady oddělených čárkou, jako v následujícím příkladu. Všechny entity požadoval dotaz se vrátí v jedné odezvě. Následující příklad vrátí `Order_Details` a `Customers` spolu s `Orders` sady entit:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] omezuje počet sad entit, které mohou být zahrnuty v jediném dotazu pomocí 12 `$expand` možnosti dotazu.  
  
-   **Explicitní načtení**: Můžete volat <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> instance pro explicitní načtení souvisejících entit. Každé volání <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metoda vytvoří samostatnou žádost o datové služby. Následující příklad načte explicitně `Order_Details` pro `Orders` entity:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Při zvažování možnost dobré si uvědomíte, že je kompromis mezi počet požadavků ve službě data a množství dat, která je vrácena v jedné odezvě. Použijte nemůžou dočkat, až načítání, pokud vaše aplikace vyžaduje přidružených objektů a chcete se vyhnout přidání latence dalších požadavků je explicitně načítat. Nicméně pokud existují případy, když aplikace potřebuje pouze data pro instance konkrétní související entity, měli byste zvážit explicitně voláním načítání entit <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metody. Další informace najdete v tématu [jak: Načtení souvisejících entit](../../../../docs/framework/data/wcf/how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Stránkovaná obsahu  
 Pokud je stránkování povoleno v datové službě, je omezen počet položek v informačním kanálu, které služba data vrátí konfigurace datové služby. Stránka omezení můžete nastavit zvlášť pro každou sadu entit. Další informace najdete v tématu [konfigurace datové služby](../../../../docs/framework/data/wcf/configuring-the-data-service-wcf-data-services.md). Když je povoleno stránkování, poslední položku v informačním kanálu obsahuje odkaz na další stránku data. Tento odkaz je součástí <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> objektu. Získat identifikátor URI další stránky dat voláním <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metodu na <xref:System.Data.Services.Client.QueryOperationResponse%601> vrácena, když <xref:System.Data.Services.Client.DataServiceQuery%601> provádí. Vrácený <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> objekt se pak použije k načtení další stránky výsledků. Před voláním musí vytvořit výčet výsledků dotazu <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody. Zvažte použití `do…while` cyklu nejprve vytvořit výčet výsledku dotazu a pak vyhledejte `non-null` hodnotu odkazu na další stránku. Když <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> vrátí metoda `null` (`Nothing` v jazyce Visual Basic), nejsou žádné další výsledek stránky pro původní dotaz. Následující příklad ukazuje `do…while` smyčku, která načte stránkovaného zákaznická data z ukázkové datová služba Northwind.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Když požadavků na dotazy související entity jsou vráceny v odpověď o jedné spolu s sady požadovaná entita, omezení stránkování může mít vliv na vnořené informační kanály, které jsou zahrnuty vložené s odpovědí. Například pokud stránkování omezení nastaveno ve vzorku datová služba Northwind pro `Customers` sadu entit, nezávislé omezení stránkování lze také nastavit pro související `Orders` entity nastavení, jako v následujícím příkladu od Northwind.svc.cs souboru, který Definuje ukázková datová služba Northwind.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 V takovém případě je nutné implementovat stránkování pro obě na nejvyšší úrovni `Customers` a vnořeného `Orders` informační kanály entity. Následující příklad ukazuje `while` smyčky použitá k načtení stránky `Orders` související entity vybranému `Customers` entity.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Další informace najdete v tématu [jak: Načtení stránkovaných výsledků](../../../../docs/framework/data/wcf/how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Binární datové proudy  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] umožňuje přístup k datům binárních rozsáhlých objektů (BLOB) jako datový proud. Streamování odloží načítání binárních dat, dokud je to potřeba, a klient může zpracovávat efektivněji tato data. Aby bylo možné tuto funkci využít, musí implementovat datové služby <xref:System.Data.Services.Providers.IDataServiceStreamProvider> zprostředkovatele. Další informace najdete v tématu [streamování poskytovatele](../../../../docs/framework/data/wcf/streaming-provider-wcf-data-services.md). Pokud je povoleno vysílání datového proudu, typy entit jsou vráceny bez související binární data. V takovém případě musíte použít <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> pro přístup k datový proud pro binární data ze služby. Podobně lze použít <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metoda pro přidání nebo změnu binární data konkrétní entity jako datový proud. Další informace najdete v tématu [práce s binárními daty](../../../../docs/framework/data/wcf/working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
- [Dotazování v datové službě](../../../../docs/framework/data/wcf/querying-the-data-service-wcf-data-services.md)
