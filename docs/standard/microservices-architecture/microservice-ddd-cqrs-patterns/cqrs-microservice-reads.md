---
title: Implementace čtení nebo dotazů v mikroslužbě CQRS
description: Architektura Mikroslužeb .NET pro Kontejnerizované aplikace .NET | Seznamte se s provádění dotazů na straně modelu cqrs v pořadí mikroslužeb v aplikaci eShopOnContainers pomocí Dapperem.
ms.date: 10/08/2018
ms.openlocfilehash: f791546e2fc00e276ab55302802a5534465ace58
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65639727"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="59b01-103">Implementace čtení nebo dotazů v mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="59b01-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="59b01-104">Pro čtení nebo dotazů implementuje pořadí mikroslužeb z aplikace odkaz na aplikaci eShopOnContainers dotazy odděleně od modelu DDD a transakční oblasti.</span><span class="sxs-lookup"><span data-stu-id="59b01-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="59b01-105">To bylo provedeno primárně, protože požadavky pro dotazy a transakce se výrazně liší.</span><span class="sxs-lookup"><span data-stu-id="59b01-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="59b01-106">Zápisy provádět transakce, které musí být v souladu se logiku domény.</span><span class="sxs-lookup"><span data-stu-id="59b01-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="59b01-107">Dotazy, na druhé straně jsou idempotentní a může být odděleni od domény pravidla.</span><span class="sxs-lookup"><span data-stu-id="59b01-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="59b01-108">Tento přístup je jednoduchý, jak je znázorněno v obrázek 7 – 3.</span><span class="sxs-lookup"><span data-stu-id="59b01-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="59b01-109">Kontrolerů rozhraní Web API pomocí jakékoliv infrastruktury, jako je například micro objekt relační Mapovač (ORM) určené jako Dapperem a vrací dynamický modely ViewModels v závislosti na potřebách aplikace uživatelského rozhraní je implementováno rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="59b01-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Nejjednodušším přístupem pro dotazy na straně zjednodušený přístup modelu CQRS může být implementována pouze dotazování na databázi s Micro-ORM jako Dapperem, vrací dynamický modely ViewModel.](./media/image3.png)

<span data-ttu-id="59b01-111">**Obrázek 7 – 3**.</span><span class="sxs-lookup"><span data-stu-id="59b01-111">**Figure 7-3**.</span></span> <span data-ttu-id="59b01-112">Nejjednodušším přístupem dotazů v mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="59b01-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="59b01-113">Toto je nejjednodušší možný přístup pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="59b01-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="59b01-114">Definice dotazů dotaz na databázi a vracet dynamické ViewModel vytvořené v reálném čase pro každý dotaz.</span><span class="sxs-lookup"><span data-stu-id="59b01-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="59b01-115">Vzhledem k tomu, že dotazy jsou idempotentní, že nedojde ke změně dat bez ohledu na to, kolikrát můžete spustit dotaz.</span><span class="sxs-lookup"><span data-stu-id="59b01-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="59b01-116">Proto není nutné být omezeni prostředím DDD používaným v transakcí na straně, jako je agregace a další způsoby, a proto dotazy, jsou odděleni od oblasti transakční.</span><span class="sxs-lookup"><span data-stu-id="59b01-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="59b01-117">Jednoduše dotaz na databázi pro data, která potřebuje uživatelského rozhraní a vracet dynamické ViewModel, který nemusí být staticky kdekoli (žádné třídy pro modely ViewModel) definované s výjimkou v příkazech SQL sami.</span><span class="sxs-lookup"><span data-stu-id="59b01-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="59b01-118">Protože se jedná o jednoduchý přístup, vyžaduje kód pro dotazy na straně (například kód pomocí micro ORM, jako jsou [Dapperem](https://github.com/StackExchange/Dapper)) je možné implementovat [v rámci stejného projektu webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="59b01-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="59b01-119">Obrázek 7 – 4 ukazuje to.</span><span class="sxs-lookup"><span data-stu-id="59b01-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="59b01-120">Dotazy jsou definovány v **Ordering.API** mikroslužeb projektu v aplikaci eShopOnContainers řešení.</span><span class="sxs-lookup"><span data-stu-id="59b01-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Zobrazení Průzkumníka řešení projektu Ordering.API zobrazující aplikaci > složky dotazů.](./media/image4.png)

<span data-ttu-id="59b01-122">**Obrázek 7 – 4**.</span><span class="sxs-lookup"><span data-stu-id="59b01-122">**Figure 7-4**.</span></span> <span data-ttu-id="59b01-123">Dotazy v mikroslužbě řazení v aplikaci eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="59b01-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="59b01-124">Používat modely ViewModels specificky vytvořené pro klientské aplikace, nezávisle na omezení modelu domény</span><span class="sxs-lookup"><span data-stu-id="59b01-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="59b01-125">Protože dotazy probíhají na získat data, která klientské aplikace potřebují, vrácený typ konkrétně lze pro klienty, na základě dat vrácených dotazy.</span><span class="sxs-lookup"><span data-stu-id="59b01-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="59b01-126">Tyto modely nebo objekty přenosu dat (DTO), se nazývají modely ViewModel.</span><span class="sxs-lookup"><span data-stu-id="59b01-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="59b01-127">Vrácená data (ViewModel) může být výsledkem spojování dat z několika entit nebo tabulek v databázi, nebo dokonce napříč více agregace definované v modelu domény pro transakční oblast.</span><span class="sxs-lookup"><span data-stu-id="59b01-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="59b01-128">Protože vytváříte dotazy nezávisle na doménový model, v tomto případě agregace hranice a omezení jsou zcela ignorovány a můžete zadávat dotazy na všechny tabulky a sloupce, který může být nutné.</span><span class="sxs-lookup"><span data-stu-id="59b01-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="59b01-129">Tento přístup poskytuje flexibilitu a zvýšení produktivity pro vývojáře se vytváří nebo aktualizuje dotazy.</span><span class="sxs-lookup"><span data-stu-id="59b01-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="59b01-130">Modely ViewModels může být statické typy definované v třídách.</span><span class="sxs-lookup"><span data-stu-id="59b01-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="59b01-131">Nebo je lze vytvořit dynamicky na základě dotazů provést (jak je implementován v pořadí mikroslužeb), což je velmi agile pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="59b01-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="59b01-132">Použít Dapperem jako micro ORM pro provádění dotazů</span><span class="sxs-lookup"><span data-stu-id="59b01-132">Use Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="59b01-133">Pro dotazování můžete použít libovolný micro ORM, Entity Framework Core nebo dokonce prostý ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="59b01-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="59b01-134">V ukázkové aplikaci pro objednávání mikroslužeb v aplikaci eShopOnContainers jako dobrý příklad oblíbených micro ORM nebyla vybrána Dapperem.</span><span class="sxs-lookup"><span data-stu-id="59b01-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="59b01-135">Může probíhat prostý dotazy SQL s vynikajícím výkonem, protože je velmi malé framework.</span><span class="sxs-lookup"><span data-stu-id="59b01-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="59b01-136">Dapperem můžete napsat dotaz SQL, který může přistupovat k a připojte se k několika tabulkám.</span><span class="sxs-lookup"><span data-stu-id="59b01-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="59b01-137">Dapperem je projekt open source (původně vytvořil Sam šafrán) a je součástí stavební bloky v [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="59b01-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="59b01-138">Použití Dapperem, stačí nainstalovat prostřednictvím [balíček Dapper NuGet](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="59b01-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Dapper balíčku jako zobrazené v zobrazení Správa balíčků NuGet v sadě Visual Studio.](./media/image4.1.png)

<span data-ttu-id="59b01-140">Musíte také přidat, a s použitím příkazu tak, že váš kód má přístup k metodám Dapper rozšíření.</span><span class="sxs-lookup"><span data-stu-id="59b01-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="59b01-141">Při použití Dapperem ve vašem kódu, můžete přímo použít <xref:System.Data.SqlClient.SqlConnection> třídy, které jsou k dispozici v <xref:System.Data.SqlClient> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="59b01-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="59b01-142">Metoda QueryAsync a další rozšiřující metody, které rozšiřují <xref:System.Data.SqlClient.SqlConnection> třídy, můžete jednoduše spustit dotazy jednoduché a výkonné způsobem.</span><span class="sxs-lookup"><span data-stu-id="59b01-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="59b01-143">Dynamická zobrazení vs. statické modely ViewModels</span><span class="sxs-lookup"><span data-stu-id="59b01-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="59b01-144">Při návratu modely ViewModels do klientské aplikace na straně serveru, se dá chápat tyto modely ViewModels jako DTO (objekty přenosu dat), které mohou být různé entity interní doméně modelu entity, protože modely ViewModels uchovávání dat tak, jak klientská aplikace potřebuje.</span><span class="sxs-lookup"><span data-stu-id="59b01-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="59b01-145">Proto v mnoha případech můžete agregovat data přicházející z několika entit domény a compose modely ViewModels přesně podle jak klientská aplikace musí tato data.</span><span class="sxs-lookup"><span data-stu-id="59b01-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="59b01-146">Tyto modely ViewModels nebo DTO může být definované explicitně (jako vlastník datové třídy) stejně jako `OrderSummary` uvedená v pozdější fragment kódu, nebo třída může vrátit pouze dynamické modely ViewModels nebo dynamické DTO, jednoduše na základě atributů vráceny vaše dotazy jako dynamické Zadejte.</span><span class="sxs-lookup"><span data-stu-id="59b01-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="59b01-147">ViewModel jako dynamický typ.</span><span class="sxs-lookup"><span data-stu-id="59b01-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="59b01-148">Jak je znázorněno v následujícím kódu `ViewModel` může být přímo vrácená metodou dotazy jenom vrácením *dynamické* typ, který interně je na základě atributů vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="59b01-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="59b01-149">To znamená, že dílčí sadu atributů, které mají být vráceny je založen na samotný dotaz.</span><span class="sxs-lookup"><span data-stu-id="59b01-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="59b01-150">Proto pokud přidáte nový sloupec do dotazu nebo join, tato data se dynamicky přidat na vrácenou `ViewModel`.</span><span class="sxs-lookup"><span data-stu-id="59b01-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
    public async Task<IEnumerable<dynamic>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            return await connection.QueryAsync<dynamic>(
                @"SELECT o.[Id] as ordernumber,
                o.[OrderDate] as [date],os.[Name] as [status],
                SUM(oi.units*oi.unitprice) as total
                FROM [ordering].[Orders] o
                LEFT JOIN[ordering].[orderitems] oi ON o.Id = oi.orderid
                LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                GROUP BY o.[Id], o.[OrderDate], os.[Name]");
        }
    }
}
```

<span data-ttu-id="59b01-151">Důležité je, že pomocí dynamický typ vrácené kolekce dat je dynamicky sestavena jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="59b01-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="59b01-152">**V oblasti IT:** Tento přístup snižuje nutnost upravit statických tříd ViewModel pokaždé, když aktualizujete věty SQL dotazu, což tento postup návrhu poměrně agile při psaní kódu, jednoduchý a rychlý rozvoj ve vztahu budoucí změny.</span><span class="sxs-lookup"><span data-stu-id="59b01-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="59b01-153">**Nevýhody:** V dlouhodobém horizontu dynamické typy může mít negativní dopad jasné a kompatibility služby pomocí klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="59b01-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="59b01-154">Kromě toho middleware softwarem, jako je Swashbuckle nemůže poskytovat stejnou úroveň dokumentace u typů vrácených při použití dynamické typy.</span><span class="sxs-lookup"><span data-stu-id="59b01-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="59b01-155">Jako předdefinovaných DTO tříd ViewModel</span><span class="sxs-lookup"><span data-stu-id="59b01-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="59b01-156">**Profesionálové**: Statické předdefinovaných tříd ViewModel, jako je "smluv" podle třídy explicitní objekt DTO, je určitě lepší pro veřejné rozhraní API, ale i na dlouhodobém horizontu mikroslužeb, i v případě, že se používají pouze ve stejné aplikaci.</span><span class="sxs-lookup"><span data-stu-id="59b01-156">**Pros**: Having static predefined ViewModel classes, like “contracts” based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="59b01-157">Pokud chcete určit typy odpověď pro Swagger, budete muset použít explicitní DTO třídy jako návratový typ.</span><span class="sxs-lookup"><span data-stu-id="59b01-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="59b01-158">Předdefinované třídy DTO proto umožňují nabízí bohatší informace ze Swaggeru.</span><span class="sxs-lookup"><span data-stu-id="59b01-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="59b01-159">Který zlepšuje dokumentaci k rozhraní API a kompatibility při využívání rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="59b01-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="59b01-160">**Nevýhody**: Jak bylo zmíněno výše, při aktualizaci kódu, má některé další kroky a aktualizujete DTO třídy.</span><span class="sxs-lookup"><span data-stu-id="59b01-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="59b01-161">*Tip založené na našich zkušenostech*: V dotazech implementovat mikroslužby řazení v aplikaci eShopOnContainers můžeme začít vyvíjet pomocí dynamické modely ViewModels jako byl v raných fázích vývoje velmi jednoduché a flexibilní.</span><span class="sxs-lookup"><span data-stu-id="59b01-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="59b01-162">Ale po vývoj byla stabilizovaná, Rozhodli jsme se refaktorovat rozhraní API a použití statické nebo předem definované DTO pro modely ViewModels, protože je jasnější mikroslužbách uživatelům vědět, explicitních typů objekt DTO, použít jako "kontrakty".</span><span class="sxs-lookup"><span data-stu-id="59b01-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="59b01-163">V následujícím příkladu vidíte, jak dotaz vrací data pomocí explicitní tříd ViewModel DTO: OrderSummary třídy.</span><span class="sxs-lookup"><span data-stu-id="59b01-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

```csharp
using Dapper;
using Microsoft.Extensions.Configuration;
using System.Data.SqlClient;
using System.Threading.Tasks;
using System.Dynamic;
using System.Collections.Generic;

public class OrderQueries : IOrderQueries
{
  public async Task<IEnumerable<OrderSummary>> GetOrdersAsync()
    {
        using (var connection = new SqlConnection(_connectionString))
        {
            connection.Open();
            var result = await connection.QueryAsync<OrderSummary>(
                  @"SELECT o.[Id] as ordernumber, 
                  o.[OrderDate] as [date],os.[Name] as [status], 
                  SUM(oi.units*oi.unitprice) as total
                  FROM [ordering].[Orders] o
                  LEFT JOIN[ordering].[orderitems] oi ON  o.Id = oi.orderid 
                  LEFT JOIN[ordering].[orderstatus] os on o.OrderStatusId = os.Id
                  GROUP BY o.[Id], o.[OrderDate], os.[Name]
                  ORDER BY o.[Id]");
        }
    } 
}
```

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="59b01-164">Popisují typy odezvy webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="59b01-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="59b01-165">Vývojáři využívající webové rozhraní API a mikroslužeb jsou nejvíce zajímají co bude vráceno – konkrétně typů odpovědi a chybové kódy (Pokud není standard).</span><span class="sxs-lookup"><span data-stu-id="59b01-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="59b01-166">Tyto jsou zpracovány v poznámkách komentáře a data XML.</span><span class="sxs-lookup"><span data-stu-id="59b01-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="59b01-167">Bez správnou dokumentaci v Uživatelském rozhraní Swagger, nemá příjemce znalostní báze se vrací typy nebo které HTTP může být vrácen kódy.</span><span class="sxs-lookup"><span data-stu-id="59b01-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="59b01-168">Tento problém vyřešen tak, že přidáte <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, takže Swashbuckle může generovat rozsáhlejší informace o vrácené modelu rozhraní API a hodnoty, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="59b01-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

```csharp
namespace Microsoft.eShopOnContainers.Services.Ordering.API.Controllers
{
    [Route("api/v1/[controller]")]
    [Authorize]
    public class OrdersController : Controller
    {
        //Additional code...
        [Route("")]
        [HttpGet]
        [ProducesResponseType(typeof(IEnumerable<OrderSummary>),
            (int)HttpStatusCode.OK)]
        public async Task<IActionResult> GetOrders()
        {
            var userid = _identityService.GetUserIdentity();
            var orders = await _orderQueries
                .GetOrdersFromUserAsync(Guid.Parse(userid));
            return Ok(orders);
        }
    }
}
```

<span data-ttu-id="59b01-169">Ale `ProducesResponseType` atribut nelze použít jako typ, ale vyžaduje použití explicitních typů, jako je dynamické `OrderSummary` ViewModel DTO, je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="59b01-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="59b01-170">To je další důvod, proč explicitní vrácené typy jsou lepší než dynamické typy v dlouhodobém horizontu.</span><span class="sxs-lookup"><span data-stu-id="59b01-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="59b01-171">Při použití `ProducesResponseType` atribut, můžete také určit, co je očekávaný výsledek v kódy nebo pokud jde o možné HTTP chyby, jako je třeba 200, 400, atd.</span><span class="sxs-lookup"><span data-stu-id="59b01-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="59b01-172">Na následujícím obrázku vidíte způsob, jakým zobrazuje uživatelské rozhraní Swagger informace hodnotu ResponseType.</span><span class="sxs-lookup"><span data-stu-id="59b01-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Zobrazení prohlížeče s stránka uživatelského rozhraní Swagger pro rozhraní API pro řazení.](./media/image5.png)

<span data-ttu-id="59b01-174">**Obrázek 7 – 5**.</span><span class="sxs-lookup"><span data-stu-id="59b01-174">**Figure 7-5**.</span></span> <span data-ttu-id="59b01-175">Zobrazení typů odpovědi a je to možné stavové kódy HTTP z webového rozhraní API uživatelské rozhraní swagger</span><span class="sxs-lookup"><span data-stu-id="59b01-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="59b01-176">Vidíte na obrázku výše jsou některé příklady hodnot na základě typů ViewModel a je to možné stavové kódy HTTP, které mohou být vráceny.</span><span class="sxs-lookup"><span data-stu-id="59b01-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="59b01-177">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="59b01-177">Additional resources</span></span>

- <span data-ttu-id="59b01-178">**Dapper** \\</span><span class="sxs-lookup"><span data-stu-id="59b01-178">**Dapper** \\</span></span>
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="59b01-179">**Julie Lerman. Datové body – Dapper, Entity Framework a hybridních aplikací (článek znalostní báze MSDN Mag.)** \\</span><span class="sxs-lookup"><span data-stu-id="59b01-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)** \\</span></span>
  <https://msdn.microsoft.com/magazine/mt703432.aspx>

- <span data-ttu-id="59b01-180">**ASP.NET Core webové rozhraní API stránky nápovědy k využívající Swagger** \\</span><span class="sxs-lookup"><span data-stu-id="59b01-180">**ASP.NET Core Web API Help Pages using Swagger** \\</span></span>
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="59b01-181">[Předchozí](eshoponcontainers-cqrs-ddd-microservice.md)
>[další](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="59b01-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
