---
title: Načítání odloženého obsahu (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, deferred content
- WCF Data Services, loading data
ms.assetid: 32f9b588-c832-44c4-a7e0-fcce635df59a
ms.openlocfilehash: 811118755c4688bd0ea8cb9ba37b2101ab6c52cf
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568943"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Načítání odloženého obsahu (WCF Data Services)
Ve výchozím nastavení WCF Data Services omezuje množství dat vrácených dotazem. V případě potřeby však můžete z datové služby explicitně načíst další data, včetně souvisejících entit, stránkovaných odpovědí a binárních datových proudů. Toto téma popisuje, jak načíst takový odložený obsah do aplikace.  
  
## <a name="related-entities"></a>Související entity  
 Při spuštění dotazu budou vráceny pouze entity v sadě entit s adresovánou adresou. Například když dotaz na datovou službu Northwind vrátí `Customers` entit, ve výchozím nastavení se související `Orders` entity nevrátí, i když existuje vztah mezi `Customers` a `Orders`. V případě, že je v datové službě povoleno stránkování, je také nutné explicitně načíst další datové stránky ze služby. Existují dva způsoby, jak načítat související entity:  
  
- **Eager načítání**: pomocí možnosti dotazu `$expand` můžete požádat, aby dotaz vrátil entity, které souvisí s přidružením k sadě entit, kterou požaduje požadovaný dotaz. Pomocí metody <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> v <xref:System.Data.Services.Client.DataServiceQuery%601> přidejte `$expand` možnost pro dotaz, který je odeslán do datové služby. Více souvisejících sad entit můžete vyžádat tak, že je oddělíte čárkou, jako v následujícím příkladu. Všechny entity vyžádané dotazem jsou vráceny v rámci jedné odpovědi. Následující příklad vrací `Order_Details` a `Customers` společně se sadou entit `Orders`:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     WCF Data Services omezení na 12 počet sad entit, které mohou být zahrnuty v jednom dotazu pomocí možnosti dotaz `$expand`.  
  
- **Explicitní načítání**: k explicitnímu načtení souvisejících entit můžete volat metodu <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> v instanci <xref:System.Data.Services.Client.DataServiceContext>. Každé volání metody <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> vytvoří samostatnou žádost o datovou službu. Následující příklad explicitně načte `Order_Details` pro entitu `Orders`:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Pokud se rozhodnete, kterou možnost použijete, vezměte v úvahu, že existuje kompromis mezi počtem požadavků na datovou službu a množstvím dat vrácených v rámci jedné odpovědi. Eager načítání použijte v případě, že vaše aplikace vyžaduje přidružené objekty a chcete se vyhnout přidané latenci dalších požadavků, aby je bylo možné explicitně načíst. Nicméně pokud existují případy, kdy aplikace potřebuje pouze data pro konkrétní související instance entit, měli byste zvážit explicitní načtení těchto entit voláním metody <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A>. Další informace najdete v tématu [Postup: načtení souvisejících entit](how-to-load-related-entities-wcf-data-services.md).  
  
## <a name="paged-content"></a>Obsah stránkovaného obsahu  
 Pokud je v datové službě povolené stránkování, počet položek v informačním kanálu, které vrací datová služba, je omezen konfigurací datové služby. Omezení stránky lze nastavit samostatně pro každou sadu entit. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md). Pokud je povoleno stránkování, obsahuje konečná položka v informačním kanálu odkaz na další stránku dat. Tento odkaz je obsažený v objektu <xref:System.Data.Services.Client.DataServiceQueryContinuation%601>. Identifikátor URI získáte na další stránku dat voláním metody <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> u <xref:System.Data.Services.Client.QueryOperationResponse%601> vráceného při spuštění <xref:System.Data.Services.Client.DataServiceQuery%601>. Vrácený objekt <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> se pak použije k načtení další stránky výsledků. Před voláním metody <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> je třeba vytvořit výčet výsledků dotazu. Zvažte použití smyčky `do…while` k prvnímu zobrazení výčtu výsledku dotazu a potom zkontrolujte hodnotu `non-null` další odkaz. Pokud metoda <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> vrátí `null` (`Nothing` v Visual Basic), pro původní dotaz nejsou k dispozici žádné další stránky výsledků. Následující příklad ukazuje smyčku `do…while`, která načte stránkovaná zákaznická data z ukázkové datové služby Northwind.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Když dotaz požaduje, aby se související entity vracely v jedné odpovědi společně s požadovanou sadou entit, můžou omezení stránkování ovlivnit vnořené kanály, které jsou zahrnuté do odpovědi. Pokud je například limit stránkování nastaven v ukázkové datové službě Northwind pro sadu `Customers` entit, může být pro související sadu entit `Orders` nastavena také velikost nezávislého stránkování, jak je uvedeno v následujícím příkladu v souboru Northwind.svc.cs, který definuje ukázkovou datovou službu Northwind.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 V takovém případě je nutné implementovat stránkování pro `Customers` nejvyšší úrovně i pro vnořené kanály `Orders` entit. Následující příklad ukazuje `while` cyklus, který se používá k načtení stránek `Orders` entit souvisejících s vybranou entitou `Customers`.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Další informace najdete v tématu [Postup: načtení stránkovaných výsledků](how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Binární datové proudy  
 WCF Data Services umožňuje přístup k binárním datům rozsáhlých objektů (BLOB) jako datový proud. Streamování odloží načítání binárních dat do doby, než je potřeba, a klient může efektivněji zpracovat tato data. Aby bylo možné tuto funkci využít, datová služba musí implementovat poskytovatele <xref:System.Data.Services.Providers.IDataServiceStreamProvider>. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md). Pokud je povoleno streamování, vrátí se typy entit bez souvisejících binárních dat. V takovém případě je nutné použít metodu <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> třídy <xref:System.Data.Services.Client.DataServiceContext> pro přístup k datovému proudu pro binární data ze služby. Podobně použijte metodu <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> k přidání nebo změně binárních dat pro entitu jako datový proud. Další informace najdete v tématu [práce s binárními daty](working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
