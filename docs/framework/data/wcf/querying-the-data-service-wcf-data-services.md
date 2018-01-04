---
title: "Dotaz na službu Data (služby WCF Data Services)"
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
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
caps.latest.revision: "7"
author: dotnet-bot
ms.author: dotnetcontent
manager: wpickett
ms.workload: dotnet
ms.openlocfilehash: 976f1e4d8a149f8104325fd5d006d245afee04a9
ms.sourcegitcommit: 16186c34a957fdd52e5db7294f291f7530ac9d24
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/22/2017
---
# <a name="querying-the-data-service-wcf-data-services"></a>Dotaz na službu Data (služby WCF Data Services)
[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientské knihovny umožňuje spouštět dotazy na data služby pomocí známých [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)] programování způsoby, včetně použití integrovaného dotazu jazyka (LINQ). Klientská knihovna překládá dotazu, která je definována v klientovi jako jedna instance <xref:System.Data.Services.Client.DataServiceQuery%601> třída do zprávy požadavku HTTP GET. Knihovny obdrží zprávu odpovědi a převede jej do instance třídy služeb dat klienta. Tyto třídy jsou sledovány objektem <xref:System.Data.Services.Client.DataServiceContext> ke kterému <xref:System.Data.Services.Client.DataServiceQuery%601> patří.  
  
## <a name="data-service-queries"></a>Dotazy na data služby  
 <xref:System.Data.Services.Client.DataServiceQuery%601> Obecná třída reprezentuje dotaz, který vrátí kolekce nula nebo více instancí typu entity. Dotaz služby data vždy patří do kontextu služby existující data. Tento kontext udržuje služby URI a metadata informace, které je potřeba vytvořit a provést dotaz.  
  
 Při použití **přidat odkaz na službu** dialogové okno Přidat službu dat do [!INCLUDE[dnprdnshort](../../../../includes/dnprdnshort-md.md)]-je vytvořen na základě klientskou aplikaci, třídu kontejneru entit, který dědí z <xref:System.Data.Services.Client.DataServiceContext> – třída. Tato třída obsahuje vlastnosti, které vracejí typové <xref:System.Data.Services.Client.DataServiceQuery%601> instance. Není k dispozici pro každou sadu entit, že data služby vystavuje jednu vlastnost. Tyto vlastnosti usnadňují vytvoření instance představuje zadaný <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
 Je dotaz proveden v následujících scénářích:  
  
-   Když výsledky jsou uvedené implicitně, jako například:  
  
    -   Pokud vlastnost <xref:System.Data.Services.Client.DataServiceContext> představující a je uvedené sady entit, například během `foreach` (C#) nebo `For Each` ([!INCLUDE[vbprvb](../../../../includes/vbprvb-md.md)]) smyčky.  
  
    -   Když je přiřazen dotaz `List` kolekce.  
  
-   Když <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> explicitně volána metoda.  
  
-   Když LINQ provádění – operátor dotazu, jako například <xref:System.Linq.Enumerable.First%2A> nebo <xref:System.Linq.Enumerable.Single%2A> je volána.  
  
 Následující dotaz, když je proveden, vrátí všechny `Customers` entity ve službě Northwind dat:  
  
 [!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getallcustomersspecific)]  
 [!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getallcustomersspecific)]  
  
 Další informace najdete v tématu [postup: provedení dotazů na Data služby](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md).  
  
 [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klient podporuje dotazy pro pozdní vazbou objekty, například při použití *dynamické* typ v jazyce C#. Z důvodů výkonu by však vždy tvoří silného typu dotazy pro službu data. <xref:System.Tuple> Klienta nepodporuje typ a dynamických objektů.  
  
## <a name="linq-queries"></a>Dotazů LINQ  
 Protože <xref:System.Data.Services.Client.DataServiceQuery%601> třída implementuje <xref:System.Linq.IQueryable%601> rozhraní definované LINQ, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] klientské knihovny je schopen transformace dotazy LINQ pro sadu dat entity do identifikátor URI, který představuje výrazu dotazu porovnán s datové služby prostředek. Následující příklad je dotaz LINQ, který je ekvivalentní pro předchozí <xref:System.Data.Services.Client.DataServiceQuery%601> , který vrací `Orders` mají nákladní náklady na více než 30 $ a objednávky výsledky podle nákladní náklady:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionslinqspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionslinqspecific)]  
  
 Tento dotaz LINQ je přeložit na následující dotaz identifikátor URI, který se spustí na základě Northwind [rychlý Start](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) služba dat:  
  
```  
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30  
```  
  
> [!NOTE]
>  Sada vyjádřit kombinací v syntaxi LINQ dotazů je širší než ty, které povolené v representational stavu transfer (REST) – na základě syntaxe identifikátoru URI, který je používán datové služby. A <xref:System.NotSupportedException> se vyvolá, když dotaz nelze mapovat na ve službě data cílový identifikátor URI.  
  
 Další informace najdete v tématu [LINQ aspekty](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
## <a name="adding-query-options"></a>Přidání možnosti dotazu  
 Data služby dotazy podporu všech dotaz možnostech, které [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]s poskytuje. Volání <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda připojit možností dotazu <xref:System.Data.Services.Client.DataServiceQuery%601> instance. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>vrátí novou <xref:System.Data.Services.Client.DataServiceQuery%601> instanci, která je ekvivalentní původní dotaz ale s nový dotaz možnost set. Následující dotaz, při spuštění, vrátí `Orders` , jsou filtrovány podle `Freight` hodnotu a seřazené podle `OrderID`, sestupně:  
  
 [!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#addqueryoptionsspecific)]  
 [!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#addqueryoptionsspecific)]  
  
 Můžete použít `$orderby` dotazování možnost pořadí a filtrovat dotaz založený na jedinou vlastností, jako v následujícím příkladu, který filtruje a řadí vrácený `Orders` objekty podle hodnotu `Freight` vlastnost:  
  
 [!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#orderwithfilter)]
 [!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#orderwithfilter)]  
  
 Můžete volat <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda postupně k vytvoření složitých dotazů výrazy. Další informace najdete v tématu [postupy: Přidání možnosti dotazu na Data služby dotaz](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).  
  
 Možnosti dotazu poskytnout další způsoby, jak vyjádřit syntaktické součásti dotaz LINQ. Další informace najdete v tématu [LINQ aspekty](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).  
  
> [!NOTE]
>  `$select` Možnost dotazu nelze přidat do dotazu identifikátoru URI pomocí <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metoda. Doporučujeme použít LINQ <xref:System.Linq.Enumerable.Select%2A> metoda váš klient bude generovat `$select` dotaz v identifikátoru URI požadavku možnost.  
  
<a name="executingQueries"></a>   
## <a name="client-versus-server-execution"></a>Klient a Server spuštění  
 Klient provede dotaz ve dvou částech. Kdykoli je to možné, na straně klienta jsou nejprve vyhodnotí výrazy v dotazu, a potom dotaz na základě identifikátoru URI je generována a odešle do služby data pro vyhodnocení proti data ve službě. Vezměte v úvahu následující dotaz LINQ:  
  
 [!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#linqqueryclientevalspecific)]  
 [!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#linqqueryclientevalspecific)]  
  
 V tomto příkladu výraz `(basePrice – (basePrice * discount))` je vyhodnocován v klientovi. Z toho důvodu skutečného identifikátoru URI dotazu `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` odeslaného na data služby obsahuje již vypočtenou hodnotu decimal `90` v klauzuli filtru. Ostatní části výrazu filtrování, včetně Výraz substring vyhodnocují se službou data. Výrazy, které se vyhodnocují na klienta postupujte podle běžné sémantiku language runtime (CLR), zatímco výrazy zaslané službě dat závisí na implementaci služby data [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu. Taky by měl být vědomi scénáře, kde toto samostatné testování může způsobit neočekávané výsledky, například když klient a služba provést v různých časových pásmech založené na čase hodnocení.  
  
## <a name="query-responses"></a>Odpovědi na dotazy  
 Po provedení <xref:System.Data.Services.Client.DataServiceQuery%601> vrátí <xref:System.Collections.Generic.IEnumerable%601> požadovaná entita typu. Tento výsledek dotazu může být převeden <xref:System.Data.Services.Client.QueryOperationResponse%601> objekt, jako v následujícím příkladu:  
  
 [!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria northwind client/cs/source.cs#getresponsespecific)]
 [!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria northwind client/vb/source.vb#getresponsespecific)]  
  
 Instancí typu entity, které představují entity ve službě data jsou vytvořené na straně klienta pomocí procesu nazývaného materialization objektu. Další informace najdete v tématu [Materialization objekt](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> Objektu implementuje <xref:System.Collections.Generic.IEnumerable%601> zajistit přístup do výsledků dotazu.  
  
 <xref:System.Data.Services.Client.QueryOperationResponse%601> Má také následující členy, které vám umožní přístup k dalším informacím o výsledku dotazu:  
  
-   <xref:System.Data.Services.Client.OperationResponse.Error%2A>-Získá chybu vyvolané operace, pokud žádné došlo k chybě.  
  
-   <xref:System.Data.Services.Client.OperationResponse.Headers%2A>-obsahuje kolekci hlaviček odpovědí HTTP přidružený k odpovědi na dotaz.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A>-Získá původní <xref:System.Data.Services.Client.DataServiceQuery%601> generovaný <xref:System.Data.Services.Client.QueryOperationResponse%601>.  
  
-   <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A>-Získá kód odpovědi HTTP pro odpověď v dotazu.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>-získá celkový počet entit v entitě nastavit, kdy <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> byla volána metoda <xref:System.Data.Services.Client.DataServiceQuery%601>.  
  
-   <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A>-Vrátí <xref:System.Data.Services.Client.DataServiceQueryContinuation> objekt, který obsahuje identifikátor URI další stránky výsledků.  
  
 Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] pouze vrátí data, která je explicitně vybrána v dotazu identifikátoru URI. To vám dává možnost explicitně načíst další data ze služby data, když je to potřeba. Žádost o posílá službu data pokaždé, když explicitně načíst data ze služby data. Data, která je možné explicitně načíst zahrnuje entit v relaci, data stránkové odpovědi a binární datové proudy.  
  
> [!NOTE]
>  Protože datové služby může vrátit stránkové odpověď, doporučujeme, aby vaše aplikace používat programovací vzor zpracovat odpověď stránkové dat služby. Další informace najdete v tématu [načítání odložení obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).  
  
 Zadáním, že jsou v odpovědi vrátí jenom některé vlastnosti entity lze také snížit množství dat vrácených dotazem. Další informace najdete v tématu [projekce dotazu](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).  
  
## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Získávání počet celkový počet entit v sadě  
 V některých případech je užitečné vědět, celkový počet entit v sadu entit a nikoli pouze počet vrácených dotazem. Volání <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> metodu <xref:System.Data.Services.Client.DataServiceQuery%601> k vyžádání, že tento celkový počet entit v sadě být součástí výsledku dotazu. V takovém případě <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> vlastnost vrácený <xref:System.Data.Services.Client.QueryOperationResponse%601> vrátí celkový počet entit v sadě.  
  
 Můžete také získat jenom celkový počet entit v sadě buď jako <xref:System.Int32> nebo jako <xref:System.Int64> hodnotu voláním <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.LongCount%2A> metody v uvedeném pořadí. Pokud tyto metody jsou volány, <xref:System.Data.Services.Client.QueryOperationResponse%601> nevrátí; je vrácena pouze hodnota počtu. Další informace najdete v tématu [postupy: určení číslo z entity vrácených dotazem](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).  
  
## <a name="in-this-section"></a>V tomto oddílu  
 [Projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)  
  
 [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)  
  
 [Aspekty LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)  
  
 [Postupy: Provádění dotazů v datové službě](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)  
  
 [Postupy: Přidání možností do dotazu v datové službě](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)  
  
 [Postupy: Určení počtu entit vrácených dotazem](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)  
  
 [Postupy: Zadání přihlašovacích údajů klienta v žádosti do datové služby](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)  
  
 [Postupy: Nastavení hlaviček v klientské žádosti](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)  
  
 [Postupy: Výsledky dotazů na projekt](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)  
  
## <a name="see-also"></a>Viz také  
 [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
