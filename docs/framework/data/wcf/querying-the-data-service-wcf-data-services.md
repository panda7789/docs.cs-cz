---
title: Dotazování v datové službě (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: abae49e709fa2e77d641d991dd6e09cf82216732
ms.sourcegitcommit: 680a741667cf6859de71586a0caf6be14f4f7793
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/12/2019
ms.locfileid: "59517288"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Dotazování v datové službě (WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna umožňuje spouštění dotazů na datovou službu pomocí známých [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] programovací modely, včetně použití jazyka integrované dotazu (LINQ). Knihovna klienta přeloží dotaz, který je definován v klientovi jako jedna instance <xref:System.Data.Services.Client.DataServiceQuery%601> třídy do zprávy požadavku HTTP GET. Knihovny přijímá zprávy s odpovědí a přeloží ho do instancí tříd klientské datové služby. Tyto třídy jsou sledovány objektem <xref:System.Data.Services.Client.DataServiceContext> ke kterému <xref:System.Data.Services.Client.DataServiceQuery%601> patří.  
  
## <a name="data-service-queries"></a>Dotazů v datové službě  
 <xref:System.Data.Services.Client.DataServiceQuery%601> Generické třídě představuje dotaz, který vrátí kolekci nula nebo více instancí typu entity. Dotaz datové služby vždy patří do existujícího kontextu datové služby. Tento kontext udržuje identifikátor URI a metadata informace o služby, které je nutné k vytvoření a provedení dotazu.  
  
 Při použití **přidat odkaz na službu** dialogové okno Přidat službu data [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]– aplikace založené na klienta, třídu kontejneru entity se vytvoří, která dědí z <xref:System.Data.Services.Client.DataServiceContext> třídy. Tato třída obsahuje vlastnosti, které vrací zadaný <xref:System.Data.Services.Client.DataServiceQuery%601> instancí. Existuje jedna vlastnost pro každou sadu entit, které data služba zpřístupňuje. Tyto vlastnosti usnadňují vytvoření instance typovaného <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
 Dotaz je proveden v následujících scénářích:  
  
-   Když výsledky jsou uvedené implicitně, jako například:  
  
    -   Pokud vlastnost <xref:System.Data.Services.Client.DataServiceContext> , který představuje a je vypočten sadu entit, jako například během `foreach` (C#) nebo `For Each` smyčky (Visual Basic).  
  
    -   Když je přiřazen dotaz `List` kolekce.  
  
-   Když <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> metoda je explicitně zavolán.  
  
-   Když LINQ provádění – operátor dotazu, jako například <xref:System.Linq.Enumerable.First%2A> nebo <xref:System.Linq.Enumerable.Single%2A> je volána.  
  
 Následující dotaz, pokud je spuštěn, vrátí všechny `Customers` entity v datová služba Northwind:  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]  
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]  
  
 Další informace najdete v tématu [jak: Spuštění dotazů v datové službě](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klient podporuje dotazy pro objekty s pozdní vazbou, například při použití *dynamické* zadejte C#. Z důvodů výkonu by ale vždy compose silného typu dotazů vůči datové služby. <xref:System.Tuple> Klient nepodporuje typ a dynamické objekty.  
  
## <a name="linq-queries"></a>Dotazy LINQ  
 Protože <xref:System.Data.Services.Client.DataServiceQuery%601> implementuje třída <xref:System.Linq.IQueryable%601> rozhraní určené LINQ, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny je možné transformovat LINQ dotazů na data sady entit na identifikátor URI, který představuje výraz dotazu, který je porovnán s datové služby prostředek. V následujícím příkladu je dotaz LINQ, který je ekvivalentem předchozího <xref:System.Data.Services.Client.DataServiceQuery%601> , která vrací `Orders` , která mají svou cenu freight více než 30 USD a objednávek výsledky podle freight náklady:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 Tento dotaz LINQ, je přeložen do následujícího dotazu identifikátoru URI, který se provede na základě Northwind [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) datové služby:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  Sadu dotazů v syntaxi LINQ anyAttribute je rozsáhlejší než ty, které povolené v (REST) representational state transfer-podle syntaxe identifikátoru URI, který používá datové služby. A <xref:System.NotSupportedException> se vyvolá, když dotaz nelze namapovat na identifikátor URI v cílové datové služby.  
  
 Další informace najdete v tématu [aspekty LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
## <a name="adding-query-options"></a>Přidání možnosti dotazu  
 Data služby dotazy dotazu se na možnosti podpory, který [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]s poskytuje. Volání <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda pro přidání možností dotazu <xref:System.Data.Services.Client.DataServiceQuery%601> instance. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> vrátí nový <xref:System.Data.Services.Client.DataServiceQuery%601> instanci, která je ekvivalentní k původní dotaz ale s nový dotaz sada možností. Následující dotaz, při spuštění vrátí `Orders` , které jsou filtrovány podle `Freight` hodnotu a seřazené podle `OrderID`sestupně:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]  
  
 Můžete použít `$orderby` možnost pořadí dotazování a filtrování dotazu podle jedné vlastnosti, jako v následujícím příkladu, který filtruje a řadí vráceného `Orders` objekty podle hodnoty `Freight` vlastnost:  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]  
  
 Můžete volat <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda postupně k vytvoření složitých dotazů výrazy. Další informace najdete v tématu [jak: Přidání možností do dotazu v datové službě](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).  
  
 Možnosti dotazu zadejte jiný způsob, jak vyjádřit syntaktické součásti dotazu LINQ. Další informace najdete v tématu [aspekty LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
> [!NOTE]
>  `$select` Povolena možnost dotazu nelze přidat do dotazu identifikátoru URI pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metody. Doporučujeme použít LINQ <xref:System.Linq.Enumerable.Select%2A> metoda může mít klienta generovat `$select` možnosti v identifikátoru URI požadavku dotazu.  
  
<a name="executingQueries"></a>   
## <a name="client-versus-server-execution"></a>Klient a spuštění serveru  
 Klient provede dotaz ve dvou částech. Kdykoli je to možné, výrazy v dotazu se nejdřív vyhodnotit na straně klienta, a pak vygeneruje a odešle do služby data pro vyhodnocení s daty ve službě dotazů založených na identifikátor URI. Vezměte v úvahu následující dotaz LINQ:  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]  
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]  
  
 V tomto příkladu výraz `(basePrice – (basePrice * discount))` vyhodnotit na straně klienta. Z toho důvodu samotný dotaz URI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` , který se odešle k datům služby obsahuje již vypočtenou hodnotu decimal `90` v klauzuli filtru. Ostatní části výrazu filtrování, včetně podřetězec výraz jsou vyhodnoceny datovou službou. Výrazy, které se vyhodnocují na straně klienta podle běžné language runtime (CLR) sémantiku, zatímco odeslána do služby data výrazy se spoléhají na implementaci služby data [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu. Jste měli také něco vědět o scénářích, kde může toto samostatné vyhodnocení vést k neočekávaným výsledkům, například když klient a služba provádět v různých časových pásmech podle času hodnocení.  
  
## <a name="query-responses"></a>Odpovědi na dotazy  
 Při spuštění <xref:System.Data.Services.Client.DataServiceQuery%601> vrátí <xref:System.Collections.Generic.IEnumerable%601> typu požadovaná entita. Tento výsledek dotazu může být převeden <xref:System.Data.Services.Client.QueryOperationResponse%601> objektů, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]  
  
 Instance typu entity, které představují entit ve službě data jsou vytvořeny na straně klienta pomocí procesu nazývaného materializace objektů. Další informace najdete v tématu [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> Objekt implementuje <xref:System.Collections.Generic.IEnumerable%601> a zajistit tak přístup k výsledkům dotazu.  
  
 <xref:System.Data.Services.Client.QueryOperationResponse%601> Také má následující členy, které vám umožní získat další informace o výsledku dotazu:  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A> -Získá chybu vyvolané operace, pokud některý došlo k chybě.  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A> -obsahuje kolekci hlaviček odpovědí HTTP přidružený k odpovědi na dotaz.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A> -Získá původní <xref:System.Data.Services.Client.DataServiceQuery%601> vygenerovanou <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> -Získá kód odpovědi HTTP pro odpověď na dotaz.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> -získá celkový počet entit v entitě nastavena, když <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> byla volána metoda <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> -Vrátí <xref:System.Data.Services.Client.DataServiceQueryContinuation> objekt, který obsahuje identifikátor URI další stránky výsledků.  
  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vrátí jenom data, která je explicitně vybrána v dotazu identifikátoru URI. To vám umožňuje explicitně načíst další data z datové služby, když ho nepotřebují. Žádost se odesílají službě dat pokaždé, když explicitně načíst data z datové služby. Data, která je explicitně načíst zahrnuje související entity, data stránkované odpovědi a binární datové proudy.  
  
> [!NOTE]
>  Vzhledem k tomu, že datové služby může vrátit stránkovaná odpověď, doporučujeme, aby vaše aplikace používat programovací model pro zpracování odpovědi služby stránkovaná data. Další informace najdete v tématu [načítání odložené obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Množství dat vrácených dotazem může také snížit tak, že určíte, že se v odpovědi vrátí pouze určité vlastnosti entity. Další informace najdete v tématu [projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Získávání počet celkový počet entit v sadě  
 V některých případech je užitečné vědět, celkový počet entit v sadu entit a nikoli pouze počet vrácených dotazem. Volání <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metodu <xref:System.Data.Services.Client.DataServiceQuery%601> požádat o zahrnou celkový počet entit v sadě s výsledkem dotazu. V takovém případě <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> vlastnost vráceného <xref:System.Data.Services.Client.QueryOperationResponse%601> vrátí celkový počet entit v sadě.  
  
 Můžete také získat jenom celkový počet entit v sadě buď jako <xref:System.Int32> nebo jako <xref:System.Int64> pomocí volání <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.LongCount%2A> metody v uvedeném pořadí. Při volání těchto metod <xref:System.Data.Services.Client.QueryOperationResponse%601> nevrátí; vrátil hodnotu count. Další informace najdete v tématu [jak: Určení počtu entit vrácených dotazem](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [Aspekty LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [Postupy: Spuštění dotazů v datové službě](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [Postupy: Přidání možností do dotazu v datové službě](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [Postupy: Určení počtu entit vrácených dotazem](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [Postupy: Zadejte požádat o přihlašovací údaje klienta datové služby](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [Postupy: Nastavit hlavičky v požadavku klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [Postupy: Výsledky dotazu projektu](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
