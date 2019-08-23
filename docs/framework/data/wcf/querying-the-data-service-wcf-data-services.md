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
ms.openlocfilehash: 50dc56a3c4c87bf9ac197b127c036c41ac833a88
ms.sourcegitcommit: 68653db98c5ea7744fd438710248935f70020dfb
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 08/22/2019
ms.locfileid: "69931127"
---
# <a name="querying-the-data-service-wcf-data-services"></a>Dotazování na datovou službu (WCF Data Services)

[!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Klientská knihovna umožňuje spouštět dotazy na datovou službu pomocí známých .NET Framework programovacích vzorů, včetně použití jazyka LINQ (Language Integrated Query). Klientská knihovna překládá dotaz, který je definován v klientovi jako instance <xref:System.Data.Services.Client.DataServiceQuery%601> třídy, do zprávy požadavku HTTP GET. Knihovna obdrží zprávu s odpovědí a přeloží ji do instancí tříd služby Klient data Service. Tyto třídy jsou sledovány <xref:System.Data.Services.Client.DataServiceContext> třídou, do <xref:System.Data.Services.Client.DataServiceQuery%601> které patří.

## <a name="data-service-queries"></a>Dotazy na datovou službu

<xref:System.Data.Services.Client.DataServiceQuery%601> Obecná třída reprezentuje dotaz, který vrací kolekci nula nebo více instancí typu entity. Dotaz datové služby vždy patří do stávajícího kontextu datové služby. Tento kontext udržuje informace o identifikátorech URI a metadatech služby, které jsou nutné k vytvoření a spuštění dotazu.

Při použití dialogového okna **Přidat odkaz na službu** k přidání datové služby do klientské aplikace založené na .NET Framework je vytvořena třída kontejneru entity, která dědí z <xref:System.Data.Services.Client.DataServiceContext> třídy. Tato třída obsahuje vlastnosti, které vracejí <xref:System.Data.Services.Client.DataServiceQuery%601> typované instance. Pro každou sadu entit, kterou datová služba zpřístupňuje, existuje jedna vlastnost. Tyto vlastnosti usnadňují vytvoření instance <xref:System.Data.Services.Client.DataServiceQuery%601>typu.

Dotaz se spustí v následujících scénářích:

- Při implicitním vyčíslení výsledků, jako například:

  - Když je vyhodnocena <xref:System.Data.Services.Client.DataServiceContext> vlastnost v, která představuje a sada entit, například `foreach` během smyčky (C#) nebo `For Each` (Visual Basic).

  - Když se dotaz přiřadí do `List` kolekce.

- , Pokud je <xref:System.Data.Services.Client.DataServiceQuery%601.BeginExecute%2A> Metoda neboexplicitněvolána.<xref:System.Data.Services.Client.DataServiceQuery%601.Execute%2A>

- V případě, že je volán operátor spuštění dotazu <xref:System.Linq.Enumerable.First%2A> LINQ <xref:System.Linq.Enumerable.Single%2A> , například nebo.

Následující dotaz, když se spustí, vrátí všechny `Customers` entity ve službě Northwind data Service:

[!code-csharp[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getallcustomersspecific)]
[!code-vb[Astoria Northwind Client#GetAllCustomersSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getallcustomersspecific)]

Další informace najdete v tématu [jak: Spusťte dotazy](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)datové služby.

Klient podporuje dotazy na objekty s pozdní vazbou, například při použití dynamického typu v C# [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] Z důvodu výkonu byste však měli vždy vytvářet dotazy silného typu proti datové službě. <xref:System.Tuple> Typ a dynamické objekty nejsou klientem podporovány.

## <a name="linq-queries"></a>Dotazy LINQ

Vzhledem k <xref:System.Data.Services.Client.DataServiceQuery%601> tomu, že <xref:System.Linq.IQueryable%601> třída implementuje rozhraní definované technologií LINQ [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] , může Klientská knihovna transformovat dotazy LINQ proti sadě entit na identifikátor URI, který představuje výraz dotazu vyhodnocený proti datové službě. partner. V následujícím příkladu je dotaz LINQ, který je ekvivalentní předchozímu <xref:System.Data.Services.Client.DataServiceQuery%601> , který vrací `Orders` náklady na dopravné více než $30 a objedná výsledky podle nákladů na dopravu:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionslinqspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsLinqSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionslinqspecific)]

Tento dotaz LINQ se převede na následující identifikátor URI dotazu, který se spustí pro službu [rychlého](../../../../docs/framework/data/wcf/quickstart-wcf-data-services.md) startu dat založenou na Northwind:

```
http://localhost:12345/Northwind.svc/Orders?Orderby=ShippedDate&?filter=Freight gt 30
```

> [!NOTE]
> Sada dotazů vyhodnotit ve syntaxi LINQ je širší než ty, které jsou povolené v syntaxi URI representationed state transfer (REST), která je používána datovými službami. <xref:System.NotSupportedException> Je vyvolána, když dotaz nelze namapovat na identifikátor URI v cílové datové službě.

Další informace najdete v tématu věnovaném [hlediskům LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).

## <a name="adding-query-options"></a>Přidání možností dotazu

Dotazy na datové služby podporují všechny možnosti dotazů, [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)]které s nabízí. Zavoláte <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu pro připojení možností dotazu <xref:System.Data.Services.Client.DataServiceQuery%601> k instanci. <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A>Vrátí novou <xref:System.Data.Services.Client.DataServiceQuery%601> instanci, která je ekvivalentní původnímu dotazu, ale s nastavenou možností nového dotazu. Následující dotaz, pokud je proveden, vrátí `Orders` `Freight` `OrderID`hodnoty, které jsou filtrovány podle hodnoty a seřazeny sestupně:

[!code-csharp[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#addqueryoptionsspecific)]
[!code-vb[Astoria Northwind Client#AddQueryOptionsSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#addqueryoptionsspecific)]

Možnost `$orderby` dotazu můžete použít pro řazení a filtrování dotazu založeného na jedné vlastnosti, jako v následujícím příkladu, který filtruje a řadí vrácené `Orders` objekty na základě hodnoty `Freight` vlastnosti:

[!code-csharp[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#orderwithfilter)]
[!code-vb[Astoria Northwind Client#OrderWithFilter](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#orderwithfilter)]

Můžete zavolat <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> metodu po sobě a vytvořit složité výrazy dotazu. Další informace najdete v tématu [jak: Přidejte možnosti dotazu do dotazu](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)datové služby.

Možnosti dotazu poskytují další způsob, jak vyjádřit syntaktické komponenty dotazu LINQ. Další informace najdete v tématu věnovaném [hlediskům LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md).

> [!NOTE]
> Možnost dotazu nelze přidat k identifikátoru URI dotazu <xref:System.Data.Services.Client.DataServiceQuery%601.AddQueryOption%2A> pomocí metody. `$select` Doporučujeme použít metodu LINQ <xref:System.Linq.Enumerable.Select%2A> , pokud má klient `$select` generovat možnost dotazu v identifikátoru URI požadavku.

<a name="executingQueries"></a>

## <a name="client-versus-server-execution"></a>Spuštění klienta versus serveru

Klient spustí dotaz ve dvou částech. Kdykoli je to možné, výrazy v dotazu se nejprve vyhodnotí na klientovi a pak se vygeneruje dotaz založený na identifikátorech URI a pošle se do datové služby pro vyhodnocení dat ve službě. Vezměte v úvahu následující dotaz LINQ:

[!code-csharp[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#linqqueryclientevalspecific)]
[!code-vb[Astoria Northwind Client#LinqQueryClientEvalSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#linqqueryclientevalspecific)]

V tomto příkladu je výraz `(basePrice – (basePrice * discount))` vyhodnocen na straně klienta. Z tohoto důvodu skutečný identifikátor URI `http://localhost:12345/northwind.svc/Products()?$filter=(UnitPrice gt 90.00M) and substringof('bike',ProductName)` dotazu, který je odeslán do datové služby, obsahuje již počítanou desítkovou `90` hodnotu v klauzuli Filter. Ostatní části filtrovacího výrazu, včetně výrazu podřetězce, jsou vyhodnocovány datovou službou. Výrazy, které jsou vyhodnocovány v klientovi, následují sémantiku modulu CLR (Common Language Runtime), zatímco výrazy odesílané datové službě spoléhají na implementaci [!INCLUDE[ssODataShort](../../../../includes/ssodatashort-md.md)] protokolu datové služby. Měli byste si také uvědomit scénáře, kdy může toto samostatné vyhodnocení způsobit neočekávané výsledky, například když klient i služba provádějí vyhodnocení na základě času v různých časových pásmech.

## <a name="query-responses"></a>Odpovědi na dotazy

Po spuštění <xref:System.Data.Services.Client.DataServiceQuery%601> <xref:System.Collections.Generic.IEnumerable%601> vrátí funkce požadovaný typ entity. Tento výsledek dotazu lze přetypovat na <xref:System.Data.Services.Client.QueryOperationResponse%601> objekt, jak je uvedeno v následujícím příkladu:

[!code-csharp[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/csharp/VS_Snippets_Misc/astoria_northwind_client/cs/source.cs#getresponsespecific)]
[!code-vb[Astoria Northwind Client#GetResponseSpecific](../../../../samples/snippets/visualbasic/VS_Snippets_Misc/astoria_northwind_client/vb/source.vb#getresponsespecific)]

Instance typu entity, které představují entity v datové službě, jsou vytvořeny v klientovi pomocí procesu nazývaného materializace objektů. Další informace naleznete v tématu [materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md). <xref:System.Data.Services.Client.QueryOperationResponse%601> Objekt implementuje<xref:System.Collections.Generic.IEnumerable%601> k poskytnutí přístupu k výsledkům dotazu.

Má <xref:System.Data.Services.Client.QueryOperationResponse%601> také následující členy, kteří vám umožní získat přístup k dalším informacím o výsledku dotazu:

- <xref:System.Data.Services.Client.OperationResponse.Error%2A>– Načte chybu vyvolanou operací, pokud k nějakému došlo.

- <xref:System.Data.Services.Client.OperationResponse.Headers%2A>-obsahuje kolekci hlaviček HTTP odpovědi přidružených k odpovědi na dotaz.

- <xref:System.Data.Services.Client.QueryOperationResponse.Query%2A>– Získá originál <xref:System.Data.Services.Client.DataServiceQuery%601> , který <xref:System.Data.Services.Client.QueryOperationResponse%601>vygeneroval.

- <xref:System.Data.Services.Client.OperationResponse.StatusCode%2A>– Získá kód odpovědi HTTP pro odpověď na dotaz.

- <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A>– Získá celkový počet entit v sadě entit, když <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> byla metoda volána <xref:System.Data.Services.Client.DataServiceQuery%601>na.

- <xref:System.Data.Services.Client.QueryOperationResponse.GetContinuation%2A>-Vrátí <xref:System.Data.Services.Client.DataServiceQueryContinuation> objekt, který obsahuje identifikátor URI další stránky výsledků.

Ve výchozím nastavení [!INCLUDE[ssAstoria](../../../../includes/ssastoria-md.md)] vrací jenom data, která jsou explicitně vybraná pomocí identifikátoru URI dotazu. Díky tomu máte možnost explicitně načíst další data z datové služby, když je to potřeba. Požadavek se pošle do datové služby pokaždé, když explicitně načtete data z datové služby. Data, která je možné explicitně načíst, zahrnují související entity, data stránkované odpovědi a binární datové proudy.

> [!NOTE]
> Vzhledem k tomu, že datová služba může vracet stránkované odpovědi, doporučujeme, aby vaše aplikace používala programovací model pro zpracování odpovědi stránkované datové služby. Další informace najdete v tématu [načítání odloženého obsahu](../../../../docs/framework/data/wcf/loading-deferred-content-wcf-data-services.md).

Množství dat vrácených dotazem se může také snížit tak, že se v odpovědi vrátí jenom některé vlastnosti entity. Další informace najdete v tématu [projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md).

## <a name="getting-a-count-of-the-total-number-of-entities-in-the-set"></a>Získává se celkový počet entit v sadě.

V některých scénářích je užitečné znát celkový počet entit v sadě entit a nikoli pouze počet vrácený dotazem. <xref:System.Data.Services.Client.DataServiceQuery%601.IncludeTotalCount%2A> Zavolejte metodu<xref:System.Data.Services.Client.DataServiceQuery%601> na pro požadavek, aby tento celkový počet entit v sadě zahrnoval výsledek dotazu. V tomto případě <xref:System.Data.Services.Client.QueryOperationResponse%601.TotalCount%2A> vrátí vlastnost vrácenou <xref:System.Data.Services.Client.QueryOperationResponse%601> celkový počet entit v sadě.

Můžete také získat celkový počet entit v sadě <xref:System.Int32> jako nebo <xref:System.Int64> jako hodnotu voláním <xref:System.Linq.Enumerable.Count%2A> metod nebo <xref:System.Linq.Enumerable.LongCount%2A> v uvedeném pořadí. Při volání těchto metod se nevrátí <xref:System.Data.Services.Client.QueryOperationResponse%601> a vrátí se jenom hodnota Count. Další informace najdete v tématu [jak: Určete počet entit vrácených dotazem](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md).

## <a name="in-this-section"></a>V tomto oddílu

- [Projekce dotazů](../../../../docs/framework/data/wcf/query-projections-wcf-data-services.md)

- [Materializace objektů](../../../../docs/framework/data/wcf/object-materialization-wcf-data-services.md)

- [Aspekty LINQ](../../../../docs/framework/data/wcf/linq-considerations-wcf-data-services.md)

- [Postupy: Spouštění dotazů datové služby](../../../../docs/framework/data/wcf/how-to-execute-data-service-queries-wcf-data-services.md)

- [Postupy: Přidání možností dotazu do dotazu datové služby](../../../../docs/framework/data/wcf/how-to-add-query-options-to-a-data-service-query-wcf-data-services.md)

- [Postupy: Určení počtu entit vrácených dotazem](../../../../docs/framework/data/wcf/number-of-entities-returned-by-a-query-wcf.md)

- [Postupy: Zadání přihlašovacích údajů klienta pro žádost datové služby](../../../../docs/framework/data/wcf/specify-client-creds-for-a-data-service-request-wcf.md)

- [Postupy: Nastavení hlaviček v žádosti klienta](../../../../docs/framework/data/wcf/how-to-set-headers-in-the-client-request-wcf-data-services.md)

- [Postupy: Výsledky dotazu projektu](../../../../docs/framework/data/wcf/how-to-project-query-results-wcf-data-services.md)

## <a name="see-also"></a>Viz také:

- [Klientská knihovna pro WCF Data Services](../../../../docs/framework/data/wcf/wcf-data-services-client-library.md)
