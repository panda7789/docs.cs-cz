---
title: Dotazování na datovou službu (WCF Data Services)
ms.date: 03/30/2017
dev_langs:
- csharp
- vb
helpviewer_keywords:
- WCF Data Services, client library
- WCF Data Services, querying
- WCF Data Services, accessing data
ms.assetid: 823e9444-27aa-4f1f-be8e-0486d67f54c0
ms.openlocfilehash: 99fe377e8fff193c4f8bb566946b95c61c1b3693
ms.sourcegitcommit: 79a2d6a07ba4ed08979819666a0ee6927bbf1b01
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/28/2019
ms.locfileid: "74568884"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Dotazování na datovou službu (WCF Data Services)

Klientská knihovna WCF Data Services umožňuje spouštět dotazy na datovou službu pomocí známých .NET Framework programovacích vzorů, včetně použití jazyka LINQ (Language Integrated Query). Klientská knihovna překládá dotaz, který je definován v klientovi jako instance třídy <xref:System.Data.Services.Client.DataServiceQuery%601>, do zprávy požadavku HTTP GET. Knihovna obdrží zprávu s odpovědí a přeloží ji do instancí tříd služby Klient data Service. Tyto třídy jsou sledovány <xref:System.Data.Services.Client.DataServiceContext>, do kterých <xref:System.Data.Services.Client.DataServiceQuery%601> patří.

## <a name="data-service-queries"></a>Dotazy na datovou službu

<xref:System.Data.Services.Client.DataServiceQuery%601> obecná třída reprezentuje dotaz, který vrací kolekci nula nebo více instancí typu entity. Dotaz datové služby vždy patří do stávajícího kontextu datové služby. Tento kontext udržuje informace o identifikátorech URI a metadatech služby, které jsou nutné k vytvoření a spuštění dotazu.

Při použití dialogového okna **Přidat odkaz na službu** k přidání datové služby do klientské aplikace založené na .NET Framework je vytvořena třída kontejneru entity, která dědí z třídy <xref:System.Data.Services.Client.DataServiceContext>. Tato třída obsahuje vlastnosti, které vracejí zadané instance <xref:System.Data.Services.Client.DataServiceQuery%601>. Pro každou sadu entit, kterou datová služba zpřístupňuje, existuje jedna vlastnost. Tyto vlastnosti usnadňují vytvoření instance typového <xref:System.Data.Services.Client.DataServiceQuery%601>.

Dotaz se spustí v následujících scénářích:

- Při implicitním vyčíslení výsledků, jako například:

  - Když je vyhodnocena vlastnost na <xref:System.Data.Services.Client.DataServiceContext>, která představuje a sadu entit, například během smyčka `foreach` (C#) nebo `For Each` (Visual Basic).

  - Když se dotaz přiřadí kolekci `List`.

- Když je explicitně volána metoda <xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A> nebo <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A>.

- Při volání operátoru spuštění dotazu LINQ, jako je například <xref:System.Linq.Enumerable.First%2A> nebo <xref:System.Linq.Enumerable.Single%2A>.

Následující dotaz, když se spustí, vrátí všechny `Customers` entit ve službě Northwind data Service:

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

Další informace najdete v tématu [Postupy: spouštění dotazů datové služby](how-to-execute-data-service-queries-wcf-data-services.md).

Klient WCF Data Services podporuje dotazy na objekty s pozdní vazbou, například při použití *dynamického* typu v C#. Z důvodu výkonu byste však měli vždy vytvářet dotazy silného typu proti datové službě. Klient nepodporuje typ <xref:System.Tuple> a dynamické objekty.

## <a name="linq-queries"></a>Dotazy LINQ

Vzhledem k tomu, že třída <xref:System.Data.Services.Client.DataServiceQuery%601> implementuje rozhraní <xref:System.Linq.IQueryable%601> definované technologií LINQ, knihovna klienta WCF Data Services je schopna transformovat dotazy LINQ proti sadě entit na identifikátor URI, který představuje výraz dotazu vyhodnocený proti prostředku datové služby. Následující příklad je dotaz LINQ, který je ekvivalentní předchozímu <xref:System.Data.Services.Client.DataServiceQuery%601>, který vrací `Orders`, které mají náklady na dopravné více než $30 a jsou výsledkem ceny za přepravné:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

Tento dotaz LINQ se převede na následující identifikátor URI dotazu, který se spustí pro službu [rychlého](quickstart-wcf-data-services.md) startu dat založenou na Northwind:

```http
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> Sada dotazů vyhodnotit ve syntaxi LINQ je širší než ty, které jsou povolené v syntaxi URI representationed state transfer (REST), která je používána datovými službami. <xref:System.NotSupportedException> je vyvolána, když dotaz nelze namapovat na identifikátor URI v cílové datové službě.

Další informace najdete v tématu věnovaném [hlediskům LINQ](linq-considerations-wcf-data-services.md).

## <a name="adding-query-options"></a>Přidání možností dotazu

Dotazy na datové služby podporují všechny možnosti dotazů, které poskytuje služba WCF Data Service. Zavoláte metodu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pro připojení možností dotazu k instanci <xref:System.Data.Services.Client.DataServiceQuery%601>. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> vrátí novou instanci <xref:System.Data.Services.Client.DataServiceQuery%601>, která je ekvivalentní původnímu dotazu, ale s nastavenou možností nového dotazu. Následující dotaz po provedení vrátí `Orders`, které jsou filtrovány hodnotou `Freight` a seřazeny podle `OrderID`, sestupně:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

Pomocí možnosti dotaz `$orderby` můžete seřadit a filtrovat dotaz na základě jedné vlastnosti, jako v následujícím příkladu, který filtruje a řadí vrácené objekty `Orders` na základě hodnoty vlastnosti `Freight`:

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

Můžete zavolat metodu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> po sobě a vytvořit složité výrazy dotazu. Další informace najdete v tématu [Postup: Přidání možností dotazu do dotazu datové služby](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md).

Možnosti dotazu poskytují další způsob, jak vyjádřit syntaktické komponenty dotazu LINQ. Další informace najdete v tématu věnovaném [hlediskům LINQ](linq-considerations-wcf-data-services.md).

> [!NOTE]
> Možnost dotazu `$select` nelze přidat k identifikátoru URI dotazu pomocí metody <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>. Doporučujeme, abyste pomocí metody <xref:System.Linq.Enumerable.Select%2A> LINQ vygenerovali v identifikátoru URI požadavku možnost dotazu `$select`.

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a>Spuštění klienta versus serveru

Klient spustí dotaz ve dvou částech. Kdykoli je to možné, výrazy v dotazu se nejprve vyhodnotí na klientovi a pak se vygeneruje dotaz založený na identifikátorech URI a pošle se do datové služby pro vyhodnocení dat ve službě. Vezměte v úvahu následující dotaz LINQ:

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

V tomto příkladu je výraz `(basePrice – (basePrice * discount))` vyhodnocen v klientovi. Z tohoto důvodu vlastní identifikátor URI dotazu `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)`, který je odeslán do datové služby, obsahuje již počítanou desítkovou hodnotu `90` v klauzuli Filter. Ostatní části filtrovacího výrazu, včetně výrazu podřetězce, jsou vyhodnocovány datovou službou. Výrazy, které jsou vyhodnocovány na straně klienta, následují sémantiku modulu CLR (Common Language Runtime), zatímco výrazy odesílané do datové služby spoléhají na implementaci datové služby protokolu OData. Měli byste si také uvědomit scénáře, kdy může toto samostatné vyhodnocení způsobit neočekávané výsledky, například když klient i služba provádějí vyhodnocení na základě času v různých časových pásmech.

## <a name="query-responses"></a>Odpovědi na dotazy

Po spuštění <xref:System.Data.Services.Client.DataServiceQuery%601> vrátí <xref:System.Collections.Generic.IEnumerable%601> požadovaného typu entity. Tento výsledek dotazu lze přetypovat na objekt <xref:System.Data.Services.Client.QueryOperationResponse%601>, jak je uvedeno v následujícím příkladu:

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

Instance typu entity, které představují entity v datové službě, jsou vytvořeny v klientovi pomocí procesu nazývaného materializace objektů. Další informace naleznete v tématu [materializace objektů](object-materialization-wcf-data-services.md). Objekt <xref:System.Data.Services.Client.QueryOperationResponse%601> implementuje <xref:System.Collections.Generic.IEnumerable%601> k poskytnutí přístupu k výsledkům dotazu.

<xref:System.Data.Services.Client.QueryOperationResponse%601> má také následující členy, které vám umožní získat přístup k dalším informacím o výsledku dotazu:

- <xref:System.Data.Services.Client.OperationResponse.Error%2A> – vrátí chybu vyvolanou operací, pokud k nějakému došlo.

- <xref:System.Data.Services.Client.OperationResponse.Headers%2A> – obsahuje kolekci hlaviček HTTP odpovědi přidružených k odpovědi na dotaz.

- <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A>-získá původní <xref:System.Data.Services.Client.DataServiceQuery%601>, který vygeneroval <xref:System.Data.Services.Client.QueryOperationResponse%601>.

- <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A> – získá kód odpovědi HTTP pro odpověď na dotaz.

- <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> – Získá celkový počet entit v sadě entit při volání metody <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> na <xref:System.Data.Services.Client.DataServiceQuery%601>.

- <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A> – vrátí objekt <xref:System.Data.Services.Client.DataServiceQueryContinuation>, který obsahuje identifikátor URI další stránky výsledků.

Ve výchozím nastavení WCF Data Services vrátí pouze data, která jsou explicitně vybrána identifikátorem URI dotazu. Díky tomu máte možnost explicitně načíst další data z datové služby, když je to potřeba. Požadavek se pošle do datové služby pokaždé, když explicitně načtete data z datové služby. Data, která je možné explicitně načíst, zahrnují související entity, data stránkované odpovědi a binární datové proudy.

> [!NOTE]
> Vzhledem k tomu, že datová služba může vracet stránkované odpovědi, doporučujeme, aby vaše aplikace používala programovací model pro zpracování odpovědi stránkované datové služby. Další informace najdete v tématu [načítání odloženého obsahu](loading-deferred-content-wcf-data-services.md).

Množství dat vrácených dotazem se může také snížit tak, že se v odpovědi vrátí jenom některé vlastnosti entity. Další informace najdete v tématu [projekce dotazů](query-projections-wcf-data-services.md).

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Získává se celkový počet entit v sadě.

V některých scénářích je užitečné znát celkový počet entit v sadě entit a nikoli pouze počet vrácený dotazem. Voláním metody <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> v <xref:System.Data.Services.Client.DataServiceQuery%601> vyžádáte, aby byl tento celkový počet entit v sadě zahrnutý společně s výsledkem dotazu. V tomto případě vlastnost <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> vráceného <xref:System.Data.Services.Client.QueryOperationResponse%601> vrátí celkový počet entit v sadě.

Můžete také získat celkový počet entit v množině buď jako <xref:System.Int32>, nebo jako <xref:System.Int64> hodnotu voláním <xref:System.Linq.Enumerable.Count%2A> nebo <xref:System.Linq.Enumerable.LongCount%2A>ch metod. Při volání těchto metod se nevrátí <xref:System.Data.Services.Client.QueryOperationResponse%601>. Vrátí se jenom hodnota Count. Další informace najdete v tématu [Postupy: určení počtu entit vrácených dotazem](number-of-entities-returned-by-a-query-wcf.md).

## <a name="in-this-section"></a>V tomto oddílu

- [Projekce dotazů](query-projections-wcf-data-services.md)

- [Materializace objektů](object-materialization-wcf-data-services.md)

- [Aspekty LINQ](linq-considerations-wcf-data-services.md)

- [Postupy: Provádění dotazů v datové službě](how-to-execute-data-service-queries-wcf-data-services.md)

- [Postupy: Přidání možností do dotazu v datové službě](how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)

- [Postupy: Určení počtu entit vrácených dotazem](number-of-entities-returned-by-a-query-wcf.md)

- [Postupy: Zadání přihlašovacích údajů klienta v žádosti do datové služby](specify-client-creds-for-a-data-service-request-wcf.md)

- [Postupy: Nastavení hlaviček v klientské žádosti](how-to-set-headers-in-the-client-request-wcf-data-services.md)

- [Postupy: Výsledky dotazů na projekt](how-to-project-query-results-wcf-data-services.md)

## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](wcf-data-services-client-library.md)
