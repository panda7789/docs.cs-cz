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
ms.openlocfilehash: 7c53ad18e029dbe1f882035c1bffc8f4bfbaa2f9
ms.sourcegitcommit: d2e1dfa7ef2d4e9ffae3d431cf6a4ffd9c8d378f
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/07/2019
ms.locfileid: "70790409"
---
# <a name="loading-deferred-content-wcf-data-services"></a>Načítání odloženého obsahu (WCF Data Services)
Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] omezuje množství dat vrácených dotazem. V případě potřeby však můžete z datové služby explicitně načíst další data, včetně souvisejících entit, stránkovaných odpovědí a binárních datových proudů. Toto téma popisuje, jak načíst takový odložený obsah do aplikace.  
  
## <a name="related-entities"></a>Související entity  
 Při spuštění dotazu budou vráceny pouze entity v sadě entit s adresovánou adresou. Například když dotaz na datovou službu Northwind `Customers` vrátí entity, ve výchozím nastavení se související `Orders` entity nevrátí, i když existuje vztah mezi `Customers` a `Orders`. V případě, že je v datové službě povoleno stránkování, je také nutné explicitně načíst další datové stránky ze služby. Existují dva způsoby, jak načítat související entity:  
  
- **Eager načítání**: Možnost `$expand` dotaz můžete použít k vyžádání, že dotaz vrátí entity, které souvisejí s přidružením na sadu entit, kterou požaduje požadovaný dotaz. Použijte metodu na pro přidání `$expand` možnosti do dotazu, který je odeslán do datové služby. <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Data.Services.Client.DataServiceQuery%601.Expand%2A> Více souvisejících sad entit můžete vyžádat tak, že je oddělíte čárkou, jako v následujícím příkladu. Všechny entity vyžádané dotazem jsou vráceny v rámci jedné odpovědi. Následující příklad vrátí `Order_Details` a `Customers` společně se `Orders` sadou entit:  
  
     [!code-csharp[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#expandorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#ExpandOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#expandorderdetailsspecific)]  
  
     [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]omezí na 12 počet sad entit, které mohou být zahrnuty v jednom dotazu pomocí `$expand` možnosti dotazu.  
  
- **Explicitní načítání**: Můžete zavolat <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> na instanci pro explicitní načtení souvisejících entit. Každé volání <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metody vytvoří samostatnou žádost o datovou službu. Následující příklad explicitně načte `Order_Details` `Orders` pro entitu:  
  
     [!code-csharp[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadrelatedorderdetailsspecific)]
     [!code-vb[Astoria Northwind Client#LoadRelatedOrderDetailsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadrelatedorderdetailsspecific)]  
  
 Pokud se rozhodnete, kterou možnost použijete, vezměte v úvahu, že existuje kompromis mezi počtem požadavků na datovou službu a množstvím dat vrácených v rámci jedné odpovědi. Eager načítání použijte v případě, že vaše aplikace vyžaduje přidružené objekty a chcete se vyhnout přidané latenci dalších požadavků, aby je bylo možné explicitně načíst. Nicméně pokud existují případy, kdy aplikace potřebuje pouze data pro konkrétní související instance entit, měli byste zvážit explicitní načtení těchto entit voláním <xref:System.Data.Services.Client.DataServiceContext.LoadProperty%2A> metody. Další informace najdete v tématu [jak: Načtěte související](how-to-load-related-entities-wcf-data-services.md)entity.  
  
## <a name="paged-content"></a>Obsah stránkovaného obsahu  
 Pokud je v datové službě povolené stránkování, počet položek v informačním kanálu, které vrací datová služba, je omezen konfigurací datové služby. Omezení stránky lze nastavit samostatně pro každou sadu entit. Další informace najdete v tématu [konfigurace datové služby](configuring-the-data-service-wcf-data-services.md). Pokud je povoleno stránkování, obsahuje konečná položka v informačním kanálu odkaz na další stránku dat. Tento odkaz je obsažen v <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> objektu. Identifikátor URI získáte na další stránku dat voláním <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody <xref:System.Data.Services.Client.QueryOperationResponse%601> vrácené při <xref:System.Data.Services.Client.DataServiceQuery%601> spuštění. Vrácený <xref:System.Data.Services.Client.DataServiceQueryContinuation%601> objekt se pak použije k načtení další stránky výsledků. Je nutné vytvořit výčet výsledků dotazu před voláním <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> metody. Zvažte použití `do…while` smyčky k prvnímu zobrazení výčtu výsledku dotazu a pak `non-null` vyhledejte další hodnotu odkazu. Když metoda vrátí `null` (`Nothing` v Visual Basic), pro původní dotaz nejsou k dispozici žádné další stránky výsledků. <xref:System.Data.Services.Client.QueryOperationResponse%601.GetContinuation%2A> Následující příklad ukazuje `do…while` smyčku, která načte stránkovaná zákaznická data z ukázkové datové služby Northwind.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextlink)]
 [!code-vb[Astoria Northwind Client#LoadNextLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextlink)]  
  
 Když dotaz požaduje, aby se související entity vracely v jedné odpovědi společně s požadovanou sadou entit, můžou omezení stránkování ovlivnit vnořené kanály, které jsou zahrnuté do odpovědi. Pokud je například limit stránkování nastaven v ukázkové datové službě Northwind pro `Customers` sadu entit, může být pro související `Orders` sadu entit nastavena také velikost nezávislého stránkování, jak je uvedeno v následujícím příkladu v souboru Northwind.svc.cs, který definuje službu Northwind Sample data Service.  
  
 [!code-csharp[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_service/cs/northwind.svc.cs#dataserviceconfigpaging)]
 [!code-vb[Astoria Northwind Service#DataServiceConfigPaging](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_service/vb/northwind.svc.vb#dataserviceconfigpaging)]  
  
 V takovém případě je nutné implementovat stránkování pro informační kanály nejvyšší úrovně `Customers` i pro vnořené `Orders` entity. Následující příklad ukazuje `while` smyčku používanou k načtení `Orders` stránek entit souvisejících s vybranou `Customers` entitou.  
  
 [!code-csharp[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#loadnextorderslink)]
 [!code-vb[Astoria Northwind Client#LoadNextOrdersLink](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#loadnextorderslink)]  
  
 Další informace najdete v tématu [jak: Načte stránkované výsledky](how-to-load-paged-results-wcf-data-services.md).  
  
## <a name="binary-data-streams"></a>Binární datové proudy  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]umožňuje přístup k datům binárních rozsáhlých objektů (BLOB) jako datový proud. Streamování odloží načítání binárních dat do doby, než je potřeba, a klient může efektivněji zpracovat tato data. Aby bylo možné tuto funkci využít, musí tato datová služba implementovat <xref:System.Data.Services.Providers.IDataServiceStreamProvider> poskytovatele. Další informace najdete v tématu [poskytovatel streamování](streaming-provider-wcf-data-services.md). Pokud je povoleno streamování, vrátí se typy entit bez souvisejících binárních dat. V takovém případě je nutné použít <xref:System.Data.Services.Client.DataServiceContext.GetReadStream%2A> metodu <xref:System.Data.Services.Client.DataServiceContext> třídy pro přístup k datovému proudu pro binární data ze služby. Podobně použijte <xref:System.Data.Services.Client.DataServiceContext.SetSaveStream%2A> metodu pro přidání nebo změnu binárních dat pro entitu jako datový proud. Další informace najdete v tématu [práce s binárními daty](working-with-binary-data-wcf-data-services.md).  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
- [Dotazování v datové službě](querying-the-data-service-wcf-data-services.md)
