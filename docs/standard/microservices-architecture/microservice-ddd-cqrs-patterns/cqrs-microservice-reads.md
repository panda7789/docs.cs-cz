---
title: Implementace čtení či dotazy v CQRS mikroslužbu
description: Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace čtení či dotazy v CQRS mikroslužbu
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.openlocfilehash: 8eca01acc2308097d1684be8bdb0f07edd86832f
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33579103"
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="0f447-103">Implementace čtení či dotazy v CQRS mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="0f447-103">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="0f447-104">Řazení mikroslužbu z aplikace eShopOnContainers odkaz pro čtení nebo dotazy, implementuje dotazy nezávisle DDD modelu a transakční oblasti.</span><span class="sxs-lookup"><span data-stu-id="0f447-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="0f447-105">K tomu bylo potřeba především, protože požadavky pro dotazy a transakce se výrazně liší.</span><span class="sxs-lookup"><span data-stu-id="0f447-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="0f447-106">Zápisy provedení transakcí, které musí být v souladu s logiku domény.</span><span class="sxs-lookup"><span data-stu-id="0f447-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="0f447-107">Dotazy, na druhé straně jsou idempotent a může být oddělené od domény pravidel.</span><span class="sxs-lookup"><span data-stu-id="0f447-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="0f447-108">Přístup je jednoduchý, jak je znázorněno v obrázek 9-3.</span><span class="sxs-lookup"><span data-stu-id="0f447-108">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="0f447-109">Rozhraní API je implementováno modulem řadiče webového rozhraní API pomocí jakékoliv infrastruktury, jako je například micro relační Mapper ORM (Object) jako Dapper a vrátí dynamické ViewModels podle potřeb uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f447-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="0f447-110">**Obrázek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="0f447-110">**Figure 9-3**.</span></span> <span data-ttu-id="0f447-111">Nejjednodušším přístupem pro dotazy v CQRS mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="0f447-111">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="0f447-112">Toto je nejjednodušší možný přístup pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="0f447-112">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="0f447-113">Definice dotazu dotaz na databázi a vrátit dynamické ViewModel vytvořené za chodu při každém dotazu.</span><span class="sxs-lookup"><span data-stu-id="0f447-113">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="0f447-114">Vzhledem k tomu, že dotazy jsou idempotent, že nedojde ke změně dat bez ohledu na to, kolikrát spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="0f447-114">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="0f447-115">Proto nemusíte být omezena žádnému DDD vzoru používá na straně transakcí, jako agregace a dalšími vzory, a proto dotazy, jsou odděleni od oblasti transakcí.</span><span class="sxs-lookup"><span data-stu-id="0f447-115">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="0f447-116">Jednoduše dotaz na databázi pro data, která je uživatelské rozhraní a vrátit dynamické ViewModel, který nemusí být staticky definovanými v odkudkoli (žádné třídy pro ViewModels) s výjimkou v příkazech SQL, sami.</span><span class="sxs-lookup"><span data-stu-id="0f447-116">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="0f447-117">Vzhledem k tomu, že toto je jednoduchá přístup, vyžaduje se kód pro dotazy na straně (například kódu pomocí micro, jako jsou ORM [Dapper](https://github.com/StackExchange/Dapper)) může být implementováno [v rámci stejné projekt webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="0f447-117">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="0f447-118">Na obrázku 9 – 4 je to.</span><span class="sxs-lookup"><span data-stu-id="0f447-118">Figure 9-4 shows this.</span></span> <span data-ttu-id="0f447-119">Dotazy jsou definovány v **Ordering.API** mikroslužbu projektu v eShopOnContainers řešení.</span><span class="sxs-lookup"><span data-stu-id="0f447-119">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="0f447-120">**Obrázek 9 – 4**.</span><span class="sxs-lookup"><span data-stu-id="0f447-120">**Figure 9-4**.</span></span> <span data-ttu-id="0f447-121">Dotazy v mikroslužbu řazení v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0f447-121">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="0f447-122">Pomocí ViewModels konkrétně vytvořené pro klientské aplikace, nezávislé na omezení domény modelu.</span><span class="sxs-lookup"><span data-stu-id="0f447-122">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="0f447-123">Vzhledem k tomu, že dotazy jsou provedena za účelem získání dat potřebných v klientských aplikacích, typ vrácený konkrétně lze pro klienty, na základě dat vrácených dotazy.</span><span class="sxs-lookup"><span data-stu-id="0f447-123">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="0f447-124">Tyto modely nebo objekty přenos dat (DTOs), se nazývají ViewModels.</span><span class="sxs-lookup"><span data-stu-id="0f447-124">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="0f447-125">Vrácená data (ViewModel) může být výsledkem spojování dat z více entit nebo tabulky v databázi, nebo dokonce i v jiných více agregace definované v modelu domény oblasti transakcí.</span><span class="sxs-lookup"><span data-stu-id="0f447-125">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="0f447-126">V takovém případě vzhledem k tomu, že při vytváření dotazů nezávislé na modelu domény, agregace hranice a omezení jsou zcela ignorovány a jste volné dotaz na všechny tabulky a sloupce, který může být nutné.</span><span class="sxs-lookup"><span data-stu-id="0f447-126">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="0f447-127">Tento přístup poskytuje flexibilitu a produktivitu pro vývojáře vytváření nebo aktualizaci dotazy.</span><span class="sxs-lookup"><span data-stu-id="0f447-127">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="0f447-128">ViewModels může být statické typy definované v třídy.</span><span class="sxs-lookup"><span data-stu-id="0f447-128">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="0f447-129">Nebo je lze vytvořit dynamicky na základě dotazů provést (jak je implementované v řazení mikroslužbu), což je velmi agilní pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="0f447-129">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="0f447-130">Použití Dapper jako malých ORM provádět dotazy</span><span class="sxs-lookup"><span data-stu-id="0f447-130">Using Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="0f447-131">Pro zadávání dotazů můžete použít všechny malých ORM, Entity Framework Core nebo i prostý ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="0f447-131">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="0f447-132">V ukázkové aplikaci pro řazení mikroslužbu v eShopOnContainers jako dobrým příkladem oblíbených malých ORM byl vybrán Dapper.</span><span class="sxs-lookup"><span data-stu-id="0f447-132">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="0f447-133">Může probíhat prostý dotazy SQL s vysoký výkon, protože je velmi malé rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0f447-133">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="0f447-134">Pomocí Dapper, můžete napsat dotaz SQL, který můžete používat a připojení k několika tabulkám.</span><span class="sxs-lookup"><span data-stu-id="0f447-134">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="0f447-135">Dapper je otevřený projekt (původně vytvořil šafrán Sam) a je součástí stavební bloky v [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="0f447-135">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="0f447-136">Pokud chcete používat Dapper, stačí nainstalovat přes [balíček Dapper NuGet](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="0f447-136">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![](./media/image4.1.png)

<span data-ttu-id="0f447-137">Musíte taky přidat pomocí příkazu tak kódu má přístup k Dapper rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="0f447-137">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="0f447-138">Pokud používáte Dapper ve vašem kódu, přímo použít <xref:System.Data.SqlClient.SqlConnection> třídy, které jsou k dispozici v <xref:System.Data.SqlClient> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="0f447-138">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="0f447-139">Prostřednictvím metody QueryAsync a dalších rozšiřující metody, které rozšiřují <xref:System.Data.SqlClient.SqlConnection> třídu, můžete jednoduše spouštět dotazy přehledné a původce způsobem.</span><span class="sxs-lookup"><span data-stu-id="0f447-139">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="0f447-140">Dynamická zobrazení vs. statické ViewModels</span><span class="sxs-lookup"><span data-stu-id="0f447-140">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="0f447-141">Při vracení ViewModels z na straně serveru, na klientských aplikací, si myslíte o těchto ViewModels jako DTOs, které může být jiné na interní doméně entity modelu entity, protože blokování ViewModels data potřebuje způsob, jakým klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f447-141">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="0f447-142">Proto v mnoha případech můžete agregovat data z více entit domény a tvoří ViewModels přesně podle jak klientská aplikace musí tato data.</span><span class="sxs-lookup"><span data-stu-id="0f447-142">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="0f447-143">Tyto ViewModels nebo DTOs může být definované explicitně (jako datové třídy držitele) jako [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) třída zobrazí v novější fragment kódu, nebo může vrátit pouze dynamické ViewModels nebo dynamické DTOs jednoduše na základě atributů vrátil vaše dotazy jako `dynamic` typu.</span><span class="sxs-lookup"><span data-stu-id="0f447-143">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a `dynamic` type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="0f447-144">ViewModel jako dynamické typ</span><span class="sxs-lookup"><span data-stu-id="0f447-144">ViewModel as dynamic type</span></span>

<span data-ttu-id="0f447-145">Jak je znázorněno v následujícím kódu, ViewModel mohou být přímo vrácena v dotazech vrácením dynamické typ, který interně je na základě atributů vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="0f447-145">As shown in the following code, a ViewModel can be directly returned by the queries by returning a dynamic type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="0f447-146">To znamená, že do něj podmnožinu atributy, které mají být vráceny je založen na samotný dotaz.</span><span class="sxs-lookup"><span data-stu-id="0f447-146">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="0f447-147">Proto pokud dotaz nebo připojení k přidáte nový sloupec, tato data se dynamicky přidá do vrácený ViewModel.</span><span class="sxs-lookup"><span data-stu-id="0f447-147">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span>

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

<span data-ttu-id="0f447-148">Důležité je, že pomocí dynamické typ vrácený shromažďování dat je dynamicky sestavena jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="0f447-148">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="0f447-149">*Specialisté:* tento přístup snižuje nutnost upravit statické třídy ViewModel při každé aktualizaci větu SQL dotazu, díky čemuž je tento přístup návrhu poměrně agilní případě kódování, přehledné a rychle momentální ohledně budoucí změny.</span><span class="sxs-lookup"><span data-stu-id="0f447-149">*Pros:* This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="0f447-150">*Cons:* na dlouhou dobu, můžete dynamické typy negativní dopad přehlednost a ovlivnit kompatibilitu služby s klientské aplikace.</span><span class="sxs-lookup"><span data-stu-id="0f447-150">*Cons:* In the long term, dynamic types can impact negatively the clarity and impact the compatibility of a service with client apps.</span></span> <span data-ttu-id="0f447-151">Kromě toho middleware softwaru, třeba Swagger nemůžete zadat stejnou úroveň dokumentace na vrácený typy při použití dynamické typy.</span><span class="sxs-lookup"><span data-stu-id="0f447-151">In addition, middleware software like Swagger cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="0f447-152">ViewModel jako předdefinované DTO třídy</span><span class="sxs-lookup"><span data-stu-id="0f447-152">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="0f447-153">*Specialisté:* statické předdefinované ViewModel třídy, jako jsou "smlouvami" podle třídy explicitní DTO, je výborný lepší pro veřejné rozhraní API, ale i na dlouhodobé mikroslužeb i v případě, že se používají pouze stejnou aplikací.</span><span class="sxs-lookup"><span data-stu-id="0f447-153">*Pros:* Having static predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="0f447-154">Pokud chcete určit typy odpovědi pro swagger, budete muset použít explicitní DTO třídy jako návratový typ.</span><span class="sxs-lookup"><span data-stu-id="0f447-154">If you want to specify response types for swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="0f447-155">Proto předdefinované třídy DTO umožňují nabízejí širší informace ze Swaggeru.</span><span class="sxs-lookup"><span data-stu-id="0f447-155">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="0f447-156">Která zvyšuje dokumentaci k rozhraní API a kompatibilitu při využívání rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="0f447-156">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="0f447-157">*Cons:* jak je uvedeno dříve, při aktualizaci kód, trvá některé další kroky k aktualizaci DTO třídy.</span><span class="sxs-lookup"><span data-stu-id="0f447-157">*Cons:* As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="0f447-158">*Tip podle našich zkušeností:* v dotazech implementovat mikroslužbu řazení v eShopOnContainers, jsme práce s vývojem pomocí dynamické ViewModels stejně jako tomu bylo velmi jednoduché a agilní počátečních fázích vývoje.</span><span class="sxs-lookup"><span data-stu-id="0f447-158">*Tip based on our experience:* In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="0f447-159">Ale po vývoj byl provozním měřítku, jsme zvolili refaktorovat rozhraní API a použití statické nebo předem definované DTOs pro ViewModels, protože je jasnější pro spotřebitele mikroslužbu vědět explicitní typy DTO používá jen "smlouva".</span><span class="sxs-lookup"><span data-stu-id="0f447-159">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="0f447-160">V následujícím příkladu vidíte, jak dotaz vrací data pomocí třídu explicitní ViewModel DTO: Třída OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="0f447-160">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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
            var result = await connection.QueryAsync<dynamic>(
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

#### <a name="describing-response-types-of-web-apis"></a><span data-ttu-id="0f447-161">Popisující typy odezvy webové rozhraní API</span><span class="sxs-lookup"><span data-stu-id="0f447-161">Describing response types of Web APIs</span></span>

<span data-ttu-id="0f447-162">Vývojáři využívají webové rozhraní API a mikroslužeb jsou nejvíce zajímají co je vrácen – konkrétně odpovědi typy a kódy chyb (Pokud není standard).</span><span class="sxs-lookup"><span data-stu-id="0f447-162">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="0f447-163">Tyto jsou zpracovávány v XML komentáře a data poznámky.</span><span class="sxs-lookup"><span data-stu-id="0f447-163">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="0f447-164">Bez správné dokumentace v uživatelském rozhraní Swagger, příjemci chybí znalostní báze se vrací jaké typy nebo jaké HTTP se může vracet kódy.</span><span class="sxs-lookup"><span data-stu-id="0f447-164">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="0f447-165">Tento problém vyřešen přidáním <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, takže Swagger může generovat bohatší informace o rozhraní API návratový modelu a hodnoty, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="0f447-165">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swagger can generate richer information about the API return model and values, as shown in the following code:</span></span>

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
           var orderTask = _orderQueries.GetOrdersAsync();
           var orders = await orderTask;
           return Ok(orders);
        }
    }
}
```

<span data-ttu-id="0f447-166">Ale `ProducesResponseType` nelze použít jako typ, ale vyžaduje explicitní typy, jako je třeba používat dynamické atribut `OrderSummary` DTO ViewModel, vidět v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="0f447-166">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="0f447-167">To je další důvod, proč explicitní vrácený typy jsou lepší, než dynamické typy z dlouhodobého hlediska.</span><span class="sxs-lookup"><span data-stu-id="0f447-167">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span>
<span data-ttu-id="0f447-168">Při použití `ProducesResponseType` atribut, můžete také určit, co je očekávaný výsledek v namapoval možné chyby/kódy HTTP, jako je 200,400, atd.</span><span class="sxs-lookup"><span data-stu-id="0f447-168">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200,400, etc.</span></span>

<span data-ttu-id="0f447-169">Na následujícím obrázku vidíte, jak uživatelské rozhraní Swagger, jsou uvedené informace o ResponseType.</span><span class="sxs-lookup"><span data-stu-id="0f447-169">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![](./media/image5.png)

<span data-ttu-id="0f447-170">**Obrázek 9-5**.</span><span class="sxs-lookup"><span data-stu-id="0f447-170">**Figure 9-5**.</span></span> <span data-ttu-id="0f447-171">Zobrazuje typy odpovědi a možné stavové kódy HTTP z webového rozhraní API uživatelské rozhraní swagger</span><span class="sxs-lookup"><span data-stu-id="0f447-171">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="0f447-172">Vidíte na obrázku výše některé ukázkové hodnoty na základě typů ViewModel a možné stavové kódy HTTP, které mohou být vráceny.</span><span class="sxs-lookup"><span data-stu-id="0f447-172">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="0f447-173">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0f447-173">Additional resources</span></span>

-   <span data-ttu-id="0f447-174">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="0f447-174">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="0f447-175">**Julie Lerman. Datové body - Dapper, rozhraní Entity Framework a hybridní aplikace (článek MSDN Mag.)**</span><span class="sxs-lookup"><span data-stu-id="0f447-175">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    *https://msdn.microsoft.com/magazine/mt703432.aspx*

-   <span data-ttu-id="0f447-176">**Stránky nápovědy k webovému rozhraní API technologie ASP.NET Core využívající Swagger**</span><span class="sxs-lookup"><span data-stu-id="0f447-176">**ASP.NET Core Web API Help Pages using Swagger**</span></span>

    *https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio*

>[!div class="step-by-step"]
<span data-ttu-id="0f447-177">[Předchozí] (eshoponcontainers-cqrs-ddd-microservice.md) [Další] (ddd-zaměřené na konkrétní microservice.md)</span><span class="sxs-lookup"><span data-stu-id="0f447-177">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
