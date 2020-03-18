---
title: Implementace čtení nebo dotazů v mikroslužbě CQRS
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pochopit implementaci dotazů straně CQRS na objednávání mikroslužby v eShopOnContainers pomocí Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 235b0e471a17e2a37a883a111cf499b7837f3ea1
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "73972077"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="8afb3-103">Implementovat čtení nebo dotazy v mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="8afb3-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="8afb3-104">Pro čtení/dotazy, řazení mikroslužby z eShopOnContainers referenční aplikace implementuje dotazy nezávisle na modelu DDD a transakční oblasti.</span><span class="sxs-lookup"><span data-stu-id="8afb3-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="8afb3-105">To bylo provedeno především proto, že požadavky na dotazy a transakce jsou drasticky odlišné.</span><span class="sxs-lookup"><span data-stu-id="8afb3-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="8afb3-106">Zápisy spouštějí transakce, které musí být kompatibilní s logikou domény.</span><span class="sxs-lookup"><span data-stu-id="8afb3-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="8afb3-107">Dotazy, na druhé straně jsou idempotentní a mohou být odděleny od pravidel domény.</span><span class="sxs-lookup"><span data-stu-id="8afb3-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="8afb3-108">Přístup je jednoduchý, jak je znázorněno na obrázku 7-3.</span><span class="sxs-lookup"><span data-stu-id="8afb3-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="8afb3-109">Rozhraní rozhraní API je implementováno řadiči webového rozhraní API pomocí libovolné infrastruktury, jako je například mikroobjektrelační mapovač (ORM), jako je Dapper, a vrácení dynamických ViewModels v závislosti na potřebách aplikací uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="8afb3-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Diagram znázorňující na straně dotazů vysoké úrovně ve zjednodušeném CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="8afb3-111">**Obrázek 7-3**.</span><span class="sxs-lookup"><span data-stu-id="8afb3-111">**Figure 7-3**.</span></span> <span data-ttu-id="8afb3-112">Nejjednodušší přístup pro dotazy v mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="8afb3-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="8afb3-113">Nejjednodušší přístup pro dotazy straně ve zjednodušené CQRS přístup lze implementovat pouze dotazování databáze s Micro-ORM jako Dapper, vrácení dynamické ViewModels.</span><span class="sxs-lookup"><span data-stu-id="8afb3-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by just querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="8afb3-114">Definice dotazu dotaz databáze a vrátit dynamické ViewModel postavené na průběžný pro každý dotaz.</span><span class="sxs-lookup"><span data-stu-id="8afb3-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="8afb3-115">Vzhledem k tomu, že dotazy jsou idempotentní, nebudou měnit data bez ohledu na to, kolikrát spustíte dotaz.</span><span class="sxs-lookup"><span data-stu-id="8afb3-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="8afb3-116">Proto není nutné omezit žádný vzorek DDD používaný na transakční straně, jako jsou agregace a další vzorky, a proto jsou dotazy odděleny od transakční oblasti.</span><span class="sxs-lookup"><span data-stu-id="8afb3-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="8afb3-117">Jednoduše dotaz databáze pro data, která potřebuje uI a vrátit dynamické ViewModel, který nemusí být staticky definovány kdekoli (žádné třídy pro ViewModels) s výjimkou samotných příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="8afb3-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="8afb3-118">Vzhledem k tomu, že se jedná o jednoduchý přístup, kód požadovaný pro straně dotazů (například kód pomocí mikro ORM jako [Dapper](https://github.com/StackExchange/Dapper)) lze implementovat [v rámci stejného projektu webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="8afb3-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="8afb3-119">Obrázek 7-4 to ukazuje.</span><span class="sxs-lookup"><span data-stu-id="8afb3-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="8afb3-120">Dotazy jsou definovány v projektu mikroslužeb **Ordering.API** v rámci řešení eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="8afb3-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Snímek obrazovky složky Dotazy projektu Ordering.API](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="8afb3-122">**Obrázek 7-4**.</span><span class="sxs-lookup"><span data-stu-id="8afb3-122">**Figure 7-4**.</span></span> <span data-ttu-id="8afb3-123">Dotazy v objednávání mikroslužby v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="8afb3-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="8afb3-124">Použití viewmodels speciálně pro klientské aplikace, nezávislé na omezeních modelu domény</span><span class="sxs-lookup"><span data-stu-id="8afb3-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="8afb3-125">Vzhledem k tomu, že dotazy jsou prováděny k získání dat potřebných pro klientské aplikace, vrácený typ lze speciálně pro klienty, na základě dat vrácených dotazy.</span><span class="sxs-lookup"><span data-stu-id="8afb3-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="8afb3-126">Tyto modely nebo objekty přenosu dat (DTO), se nazývají ViewModels.</span><span class="sxs-lookup"><span data-stu-id="8afb3-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="8afb3-127">Vrácená data (ViewModel) může být výsledkem spojování dat z více entit nebo tabulek v databázi nebo dokonce mezi více agregacemi definovanými v modelu domény pro transakční oblast.</span><span class="sxs-lookup"><span data-stu-id="8afb3-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="8afb3-128">V tomto případě, protože vytváříte dotazy nezávislé na modelu domény, agregace hranice a omezení jsou zcela ignorovány a máte možnost dotazovat se na libovolnou tabulku a sloupec, který budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="8afb3-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="8afb3-129">Tento přístup poskytuje velkou flexibilitu a produktivitu pro vývojáře vytváření nebo aktualizaci dotazů.</span><span class="sxs-lookup"><span data-stu-id="8afb3-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="8afb3-130">ViewModels mohou být statické typy definované ve třídách.</span><span class="sxs-lookup"><span data-stu-id="8afb3-130">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="8afb3-131">Nebo mohou být vytvořeny dynamicky na základě provedených dotazů (jak je implementováno v objednávání mikroslužby), což je velmi agilní pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="8afb3-131">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="8afb3-132">Použití dapperu jako mikroORSu k provádění dotazů</span><span class="sxs-lookup"><span data-stu-id="8afb3-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="8afb3-133">Můžete použít libovolné mikro ORM, Entity Framework Core, nebo dokonce prostý ADO.NET pro dotazování.</span><span class="sxs-lookup"><span data-stu-id="8afb3-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="8afb3-134">V ukázkové aplikaci byl Dapper vybrán pro objednávání mikroslužeb v eShopOnContainers jako dobrý příklad oblíbeného mikro ORM.</span><span class="sxs-lookup"><span data-stu-id="8afb3-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="8afb3-135">Může spouštět prosté dotazy SQL se skvělým výkonem, protože je to velmi lehký rámec.</span><span class="sxs-lookup"><span data-stu-id="8afb3-135">It can run plain SQL queries with great performance, because it's a very light framework.</span></span> <span data-ttu-id="8afb3-136">Pomocí Dapper, můžete napsat dotaz SQL, který může přistupovat a spojit více tabulek.</span><span class="sxs-lookup"><span data-stu-id="8afb3-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="8afb3-137">Dapper je open-source projekt (originál vytvořil Sam Saffron), a je součástí stavebních bloků používaných v [Stack Přetečení](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="8afb3-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="8afb3-138">Chcete-li použít Dapper, stačí jej nainstalovat přes [balíček Dapper NuGet](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="8afb3-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Snímek obrazovky s balíčkem Dapper v zobrazení balíčků NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="8afb3-140">Také je třeba přidat using prohlášení, takže váš kód má přístup k metodám rozšíření Dapper.</span><span class="sxs-lookup"><span data-stu-id="8afb3-140">You also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="8afb3-141">Při použití Dapper v kódu, můžete <xref:System.Data.SqlClient.SqlConnection> přímo použít <xref:System.Data.SqlClient> třídu k dispozici v oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="8afb3-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="8afb3-142">Prostřednictvím QueryAsync metody a další <xref:System.Data.SqlClient.SqlConnection> metody rozšíření, které rozšiřují třídu, můžete jednoduše spustit dotazy v jednoduché a performant způsobem.</span><span class="sxs-lookup"><span data-stu-id="8afb3-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="8afb3-143">Dynamické versus statické ViewModels</span><span class="sxs-lookup"><span data-stu-id="8afb3-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="8afb3-144">Při vracení ViewModels ze serverové aplikace do klientských aplikací, můžete přemýšlet o těchto ViewModels jako DTO (Objekty přenosu dat), které se mohou lišit od interní chložských entit modelu entity, protože ViewModels uchovávat data tak, jak klientské aplikace Potřeby.</span><span class="sxs-lookup"><span data-stu-id="8afb3-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="8afb3-145">Proto v mnoha případech můžete agregovat data pocházející z více entit domény a sestavit ViewModels přesně podle toho, jak klientská aplikace potřebuje tato data.</span><span class="sxs-lookup"><span data-stu-id="8afb3-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="8afb3-146">Tyto ViewModels nebo DTO lze explicitně definovat (jako `OrderSummary` třídy držitele dat), jako je třída zobrazená v pozdějším fragmentu kódu, nebo můžete vrátit dynamické ViewModels nebo dynamické DTO jednoduše na základě atributů vrácených dotazy jako dynamický typ.</span><span class="sxs-lookup"><span data-stu-id="8afb3-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes) like the `OrderSummary` class shown in a later code snippet, or you could just return dynamic ViewModels or dynamic DTOs simply based on the attributes returned by your queries, as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="8afb3-147">ViewModel jako dynamický typ</span><span class="sxs-lookup"><span data-stu-id="8afb3-147">ViewModel as dynamic type</span></span>

<span data-ttu-id="8afb3-148">Jak je znázorněno v `ViewModel` následujícím kódu, a může být přímo vrácena dotazy pouze vrácení *dynamického* typu, který interně je založen na atributy vrácené dotazem.</span><span class="sxs-lookup"><span data-stu-id="8afb3-148">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="8afb3-149">To znamená, že podmnožina atributů, které mají být vráceny, je založena na samotném dotazu.</span><span class="sxs-lookup"><span data-stu-id="8afb3-149">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="8afb3-150">Proto pokud přidáte nový sloupec do dotazu nebo spojení, tato data `ViewModel`se dynamicky přidá do vrácené .</span><span class="sxs-lookup"><span data-stu-id="8afb3-150">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="8afb3-151">Důležitým bodem je, že pomocí dynamického typu vrácené kolekce dat je dynamicky sestavenjako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="8afb3-151">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="8afb3-152">**Klady:** Tento přístup snižuje potřebu upravit statické ViewModel třídy při každé aktualizaci věty SQL dotazu, takže tento návrh přístup docela agilní při kódování, jednoduché a rychle vyvíjet s ohledem na budoucí změny.</span><span class="sxs-lookup"><span data-stu-id="8afb3-152">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach pretty agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="8afb3-153">**Nevýhody:** Z dlouhodobého hlediska dynamické typy mohou negativně ovlivnit srozumitelnost a kompatibilitu služby s klientskými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="8afb3-153">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="8afb3-154">Kromě toho middleware software jako Swashbuckle nemůže poskytnout stejnou úroveň dokumentace na vrácené typy, pokud používáte dynamické typy.</span><span class="sxs-lookup"><span data-stu-id="8afb3-154">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="8afb3-155">ViewModel jako předdefinované třídy DTO</span><span class="sxs-lookup"><span data-stu-id="8afb3-155">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="8afb3-156">**Klady**: S statické předdefinované ViewModel třídy, jako je "smlouvy" na základě explicitní DTO třídy, je rozhodně lepší pro veřejná api, ale také pro dlouhodobé mikroslužeb, i v případě, že jsou používány pouze stejnou aplikací.</span><span class="sxs-lookup"><span data-stu-id="8afb3-156">**Pros**: Having static predefined ViewModel classes, like “contracts” based on explicit DTO classes, is definitely better for public APIs but also for long term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="8afb3-157">Pokud chcete zadat typy odpovědí pro Swagger, musíte použít explicitní Třídy DTO jako návratový typ.</span><span class="sxs-lookup"><span data-stu-id="8afb3-157">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="8afb3-158">Proto předdefinované třídy DTO umožňují nabízet bohatší informace od Swagger.</span><span class="sxs-lookup"><span data-stu-id="8afb3-158">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="8afb3-159">To zlepšuje dokumentaci rozhraní API a kompatibilitu při využívání rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="8afb3-159">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="8afb3-160">**Nevýhody**: Jak již bylo zmíněno dříve, při aktualizaci kódu trvá některé další kroky k aktualizaci tříd DTO.</span><span class="sxs-lookup"><span data-stu-id="8afb3-160">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="8afb3-161">*Tip na základě našich zkušeností*: V dotazech implementovaných v objednávání mikroslužby v eShopOnContainers jsme začali vyvíjet pomocí dynamické ViewModels, protože to bylo velmi jednoduché a agilní v raných fázích vývoje.</span><span class="sxs-lookup"><span data-stu-id="8afb3-161">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was very straightforward and agile on the early development stages.</span></span> <span data-ttu-id="8afb3-162">Ale jakmile vývoj byl stabilizován, jsme se rozhodli refaktorovat api a použití statické nebo předdefinované DTO pro ViewModels, protože je jasnější pro spotřebitele mikroslužeb znát explicitní typy DTO, který se používá jako "smlouvy".</span><span class="sxs-lookup"><span data-stu-id="8afb3-162">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice’s consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="8afb3-163">V následujícím příkladu můžete vidět, jak dotaz vrací data pomocí explicitní třídy ViewModel DTO: OrderSummary třídy.</span><span class="sxs-lookup"><span data-stu-id="8afb3-163">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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
            return await connection.QueryAsync<OrderSummary>(
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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="8afb3-164">Popište typy odpovědí webových api</span><span class="sxs-lookup"><span data-stu-id="8afb3-164">Describe response types of Web APIs</span></span>

<span data-ttu-id="8afb3-165">Vývojáři, kteří spotřebovávají webová rozhraní API a mikroslužeb, se nejvíce zabývají tím, co je vráceno – konkrétně typy odpovědí a kódy chyb (pokud ne standardní).</span><span class="sxs-lookup"><span data-stu-id="8afb3-165">Developers consuming web APIs and microservices are most concerned with what is returned — specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="8afb3-166">Ty jsou zpracovány v komentářích XML a datových poznámkách.</span><span class="sxs-lookup"><span data-stu-id="8afb3-166">These are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="8afb3-167">Bez řádné dokumentace v ui Swagger, spotřebitel postrádá znalosti o tom, jaké typy jsou vráceny nebo jaké kódy HTTP mohou být vráceny.</span><span class="sxs-lookup"><span data-stu-id="8afb3-167">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="8afb3-168">Tento problém je vyřešen <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>přidáním , takže Swashbuckle může generovat bohatší informace o návratovém modelu rozhraní API a hodnotách, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="8afb3-168">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="8afb3-169">`ProducesResponseType` Atribut však nelze použít dynamic jako typ, ale vyžaduje `OrderSummary` použití explicitní typy, jako je ViewModel DTO, je uvedeno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="8afb3-169">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="8afb3-170">To je další důvod, proč explicitní vrácené typy jsou lepší než dynamické typy, v dlouhodobém horizontu.</span><span class="sxs-lookup"><span data-stu-id="8afb3-170">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="8afb3-171">Při použití `ProducesResponseType` atributu můžete také určit, jaký je očekávaný výsledek, pokud jde o možné chyby/kódy HTTP, jako je 200, 400 atd.</span><span class="sxs-lookup"><span data-stu-id="8afb3-171">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="8afb3-172">Na následujícím obrázku můžete vidět, jak swagger uI zobrazuje responsetype informace.</span><span class="sxs-lookup"><span data-stu-id="8afb3-172">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Snímek obrazovky se stránkou s rozhraním Swagger pro rozhraní API pro objednávání](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="8afb3-174">**Obrázek 7-5**.</span><span class="sxs-lookup"><span data-stu-id="8afb3-174">**Figure 7-5**.</span></span> <span data-ttu-id="8afb3-175">Uživatelské rozhraní Swagger zobrazující typy odpovědí a možné kódy stavu HTTP z webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="8afb3-175">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="8afb3-176">Na obrázku nad některé ukázkové hodnoty založené na typech ViewModel a možných stavových kódech HTTP, které lze vrátit, můžete zobrazit na obrázku výše.</span><span class="sxs-lookup"><span data-stu-id="8afb3-176">You can see in the image above some example values based on the ViewModel types plus the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="8afb3-177">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="8afb3-177">Additional resources</span></span>

- <span data-ttu-id="8afb3-178">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="8afb3-178">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="8afb3-179">**Julie Lermanová. Datové body - Dapper, Entity Framework a hybridní aplikace (článek časopisu MSDN)**</span><span class="sxs-lookup"><span data-stu-id="8afb3-179">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="8afb3-180">**Stránky nápovědy k webovému rozhraní API technologie ASP.NET Core využívající Swagger**</span><span class="sxs-lookup"><span data-stu-id="8afb3-180">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="8afb3-181">[Předchozí](eshoponcontainers-cqrs-ddd-microservice.md)
>[další](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="8afb3-181">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
