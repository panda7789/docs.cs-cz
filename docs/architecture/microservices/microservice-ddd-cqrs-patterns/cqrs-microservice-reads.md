---
title: Implementace čtení nebo dotazů v mikroslužbě CQRS
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopení implementace dotazů, které jsou součástí CQRS, na základě řazení mikroslužby v eShopOnContainers pomocí Dapperem.
ms.date: 10/08/2018
ms.openlocfilehash: 41932122326cf4c49b9c9e2c344d2ac17da7466b
ms.sourcegitcommit: ae2e8a61a93c5cf3f0035c59e6b064fa2f812d14
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/02/2020
ms.locfileid: "89358892"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="56c03-103">Implementace čtení/dotazů v mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="56c03-103">Implement reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="56c03-104">Pro čtení a dotazování mikroslužba řazení z referenční aplikace eShopOnContainers implementuje dotazy nezávisle na modelu DDD a transakční oblasti.</span><span class="sxs-lookup"><span data-stu-id="56c03-104">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="56c03-105">To bylo provedeno hlavně proto, že požadavky na dotazy a pro transakce jsou drasticky odlišné.</span><span class="sxs-lookup"><span data-stu-id="56c03-105">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="56c03-106">Zapisuje transakce Execute, které musí být kompatibilní s logikou domény.</span><span class="sxs-lookup"><span data-stu-id="56c03-106">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="56c03-107">Na druhé straně jsou dotazy idempotentní a je možné je oddělit od pravidel domény.</span><span class="sxs-lookup"><span data-stu-id="56c03-107">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="56c03-108">Přístup je jednoduchý, jak je znázorněno na obrázku 7-3.</span><span class="sxs-lookup"><span data-stu-id="56c03-108">The approach is simple, as shown in Figure 7-3.</span></span> <span data-ttu-id="56c03-109">Rozhraní API se implementuje řadiči webového rozhraní API pomocí libovolné infrastruktury, jako je například mikrorelační mapování (ORM), jako je Dapperem, a vrácení dynamické ViewModels v závislosti na potřebách aplikací uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="56c03-109">The API interface is implemented by the Web API controllers using any infrastructure, such as a micro Object Relational Mapper (ORM) like Dapper, and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![Diagram znázorňující dotazy na nejvyšší úrovni v zjednodušené CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

<span data-ttu-id="56c03-111">**Obrázek 7-3**.</span><span class="sxs-lookup"><span data-stu-id="56c03-111">**Figure 7-3**.</span></span> <span data-ttu-id="56c03-112">Nejjednodušší přístup k dotazům v mikroslužbě CQRS</span><span class="sxs-lookup"><span data-stu-id="56c03-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="56c03-113">Nejjednodušší přístup k dotazům na straně zjednodušeného přístupu CQRS je možné implementovat dotazování databáze pomocí mikroorm, jako je Dapperem, a vrácení dynamického ViewModels.</span><span class="sxs-lookup"><span data-stu-id="56c03-113">The simplest approach for the queries-side in a simplified CQRS approach can be implemented by querying the database with a Micro-ORM like Dapper, returning dynamic ViewModels.</span></span> <span data-ttu-id="56c03-114">Definice dotazů dotazují databázi a vrátí pro každý dotaz dynamický ViewModel sestavený za běhu.</span><span class="sxs-lookup"><span data-stu-id="56c03-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="56c03-115">Vzhledem k tomu, že jsou dotazy idempotentní, nemění data bez ohledu na to, kolikrát spustíte dotaz.</span><span class="sxs-lookup"><span data-stu-id="56c03-115">Since the queries are idempotent, they won't change the data no matter how many times you run a query.</span></span> <span data-ttu-id="56c03-116">Proto nemusíte být omezeny žádným vzorem DDD použitým v transakční straně, jako jsou agregace a jiné vzory, a proto jsou dotazy odděleny od transakční oblasti.</span><span class="sxs-lookup"><span data-stu-id="56c03-116">Therefore, you don't need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="56c03-117">Dotazujte databázi na data, která uživatelské rozhraní potřebuje, a vraťte dynamické ViewModel, které není nutné staticky definovat kdekoli (žádné třídy pro ViewModels), s výjimkou samotných příkazů SQL.</span><span class="sxs-lookup"><span data-stu-id="56c03-117">You query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="56c03-118">Vzhledem k tomu, že tento přístup je jednoduchý, kód požadovaný pro dotazy na straně (například kód pomocí mikroorm jako [dapperem](https://github.com/StackExchange/Dapper)) je možné implementovat [do stejného projektu webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="56c03-118">Since this approach is simple, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="56c03-119">Obrázek 7-4 ukazuje toto.</span><span class="sxs-lookup"><span data-stu-id="56c03-119">Figure 7-4 shows this.</span></span> <span data-ttu-id="56c03-120">Dotazy jsou definovány v projektu pro **objednávání. API** mikroslužeb v rámci řešení eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="56c03-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![Snímek složky dotazů v projektu řazení. API](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

<span data-ttu-id="56c03-122">**Obrázek 7-4**.</span><span class="sxs-lookup"><span data-stu-id="56c03-122">**Figure 7-4**.</span></span> <span data-ttu-id="56c03-123">Dotazy na mikroslužbu řazení v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="56c03-123">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="56c03-124">Použijte ViewModels specificky pro klientské aplikace nezávisle na omezeních doménového modelu.</span><span class="sxs-lookup"><span data-stu-id="56c03-124">Use ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="56c03-125">Vzhledem k tomu, že se dotazy provádějí pro získání dat potřebných klientskými aplikacemi, může být vrácený typ konkrétně vytvořen pro klienty na základě dat vrácených dotazy.</span><span class="sxs-lookup"><span data-stu-id="56c03-125">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="56c03-126">Tyto modely, neboli Přenos dat objektů (DTO), se nazývají ViewModels.</span><span class="sxs-lookup"><span data-stu-id="56c03-126">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="56c03-127">Vrácená data (ViewModel) mohou být výsledkem propojení dat z více entit nebo tabulek v databázi, nebo dokonce napříč více agregovanými definicemi, které jsou definovány v doménovém modelu pro transakční oblast.</span><span class="sxs-lookup"><span data-stu-id="56c03-127">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="56c03-128">V takovém případě, protože vytváříte dotazy nezávislé na doménovém modelu, budou hranice agregace a omezení ignorovány a vy budete moci dotazovat na libovolnou tabulku a sloupec, které možná budete potřebovat.</span><span class="sxs-lookup"><span data-stu-id="56c03-128">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are ignored and you're free to query any table and column you might need.</span></span> <span data-ttu-id="56c03-129">Tento přístup poskytuje vývojářům pro vytváření a aktualizaci dotazů skvělou flexibilitu a produktivitu.</span><span class="sxs-lookup"><span data-stu-id="56c03-129">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="56c03-130">ViewModels může být statických typů definovaných ve třídách (jak je implementováno v mikroslužbě řazení).</span><span class="sxs-lookup"><span data-stu-id="56c03-130">The ViewModels can be static types defined in classes (as is implemented in the ordering microservice).</span></span> <span data-ttu-id="56c03-131">Nebo je lze vytvořit dynamicky na základě provedených dotazů, což je pro vývojáře velmi agilní.</span><span class="sxs-lookup"><span data-stu-id="56c03-131">Or they can be created dynamically based on the queries performed, which is very agile for developers.</span></span>

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="56c03-132">Použití Dapperem jako mikroorm k provádění dotazů</span><span class="sxs-lookup"><span data-stu-id="56c03-132">Use Dapper as a micro ORM to perform queries</span></span>

<span data-ttu-id="56c03-133">Pro dotazování můžete použít jakýkoli mikroorm, Entity Framework Core nebo i prostý ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="56c03-133">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="56c03-134">V ukázkové aplikaci byl jako dobrý příklad oblíbených mikroorm vybraný Dapperem pro řazení mikroslužeb v eShopOnContainers.</span><span class="sxs-lookup"><span data-stu-id="56c03-134">In the sample application, Dapper was selected for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="56c03-135">Může spouštět prosté dotazy SQL se skvělým výkonem, protože se jedná o světelný rámec.</span><span class="sxs-lookup"><span data-stu-id="56c03-135">It can run plain SQL queries with great performance, because it's a light framework.</span></span> <span data-ttu-id="56c03-136">Pomocí Dapperem můžete napsat dotaz SQL, který může přistupovat k několika tabulkám a připojovat se k nim.</span><span class="sxs-lookup"><span data-stu-id="56c03-136">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="56c03-137">Dapperem je open source projekt (originál vytvořený pomocí Sam Saffron) a je součástí stavebních bloků používaných v [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="56c03-137">Dapper is an open-source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="56c03-138">Chcete-li použít Dapperem, stačí ji nainstalovat prostřednictvím [balíčku NuGet dapperem](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku:</span><span class="sxs-lookup"><span data-stu-id="56c03-138">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure:</span></span>

![Snímek obrazovky s balíčkem Dapperem v zobrazení balíčků NuGet](./media/cqrs-microservice-reads/drapper-package-nuget.png)

<span data-ttu-id="56c03-140">Je také nutné přidat `using` direktivu, aby váš kód měl přístup k metodám rozšíření dapperem.</span><span class="sxs-lookup"><span data-stu-id="56c03-140">You also need to add a `using` directive so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="56c03-141">Při použití Dapperem v kódu přímo použijete <xref:System.Data.SqlClient.SqlConnection> třídu dostupnou v <xref:System.Data.SqlClient> oboru názvů.</span><span class="sxs-lookup"><span data-stu-id="56c03-141">When you use Dapper in your code, you directly use the <xref:System.Data.SqlClient.SqlConnection> class available in the <xref:System.Data.SqlClient> namespace.</span></span> <span data-ttu-id="56c03-142">Prostřednictvím metody QueryAsync a dalších metod rozšíření, které tuto třídu rozšířily <xref:System.Data.SqlClient.SqlConnection> , můžete spouštět dotazy jednoduchým a vykonávajícím způsobem.</span><span class="sxs-lookup"><span data-stu-id="56c03-142">Through the QueryAsync method and other extension methods that extend the <xref:System.Data.SqlClient.SqlConnection> class, you can run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-versus-static-viewmodels"></a><span data-ttu-id="56c03-143">Dynamické versus statické ViewModels</span><span class="sxs-lookup"><span data-stu-id="56c03-143">Dynamic versus static ViewModels</span></span>

<span data-ttu-id="56c03-144">Při vracení ViewModels z klientských aplikací na straně serveru můžete uvažovat o těchto ViewModels jako DTO (Přenos dat objekty), které se mohou lišit od interních entit domény modelu entity, protože ViewModels drží data způsobem, jakým aplikace potřebuje klientská aplikace.</span><span class="sxs-lookup"><span data-stu-id="56c03-144">When returning ViewModels from the server-side to client apps, you can think about those ViewModels as DTOs (Data Transfer Objects) that can be different to the internal domain entities of your entity model because the ViewModels hold the data the way the client app needs.</span></span> <span data-ttu-id="56c03-145">Proto můžete v mnoha případech agregovat data přicházející z více doménových entit a ViewModels vytvořit přesně podle toho, jak klientská aplikace potřebuje tato data.</span><span class="sxs-lookup"><span data-stu-id="56c03-145">Therefore, in many cases, you can aggregate data coming from multiple domain entities and compose the ViewModels precisely according to how the client app needs that data.</span></span>

<span data-ttu-id="56c03-146">Tyto ViewModels nebo DTO lze definovat explicitně (jako třídy pro držitele dat), jako je `OrderSummary` Třída zobrazená v pozdějším fragmentu kódu.</span><span class="sxs-lookup"><span data-stu-id="56c03-146">Those ViewModels or DTOs can be defined explicitly (as data holder classes), like the `OrderSummary` class shown in a later code snippet.</span></span> <span data-ttu-id="56c03-147">Nebo můžete pouze vrátit dynamické ViewModels nebo dynamické Dtoy na základě atributů vrácených dotazy jako dynamického typu.</span><span class="sxs-lookup"><span data-stu-id="56c03-147">Or, you could just return dynamic ViewModels or dynamic DTOs based on the attributes returned by your queries as a dynamic type.</span></span>

### <a name="viewmodel-as-dynamic-type"></a><span data-ttu-id="56c03-148">ViewModel jako dynamický typ</span><span class="sxs-lookup"><span data-stu-id="56c03-148">ViewModel as dynamic type</span></span>

<span data-ttu-id="56c03-149">Jak je znázorněno v následujícím kódu, `ViewModel` může být přímo vrácen pomocí dotazů pouhým vrácením *dynamického* typu, který interně vychází z atributů vrácených dotazem.</span><span class="sxs-lookup"><span data-stu-id="56c03-149">As shown in the following code, a `ViewModel` can be directly returned by the queries by just returning a *dynamic* type that internally is based on the attributes returned by a query.</span></span> <span data-ttu-id="56c03-150">To znamená, že podmnožina atributů, které mají být vráceny, je založena na samotném dotazu.</span><span class="sxs-lookup"><span data-stu-id="56c03-150">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="56c03-151">Proto pokud přidáte do dotazu nebo JOIN nový sloupec, budou tato data dynamicky přidána do vráceného `ViewModel` .</span><span class="sxs-lookup"><span data-stu-id="56c03-151">Therefore, if you add a new column to the query or join, that data is dynamically added to the returned `ViewModel`.</span></span>

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

<span data-ttu-id="56c03-152">Důležité je, že při použití dynamického typu je vrácená kolekce dat dynamicky sestavena jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="56c03-152">The important point is that by using a dynamic type, the returned collection of data is dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="56c03-153">**Profesionály:** Tento přístup omezuje nutnost upravovat statické třídy ViewModel vždy, když aktualizujete větu SQL dotazu. Tento přístup k návrhu se zjednodušuje při kódování, snadném a rychlém vývoje v souvislosti s budoucími změnami.</span><span class="sxs-lookup"><span data-stu-id="56c03-153">**Pros:** This approach reduces the need to modify static ViewModel classes whenever you update the SQL sentence of a query, making this design approach agile when coding, straightforward, and quick to evolve in regard to future changes.</span></span>

<span data-ttu-id="56c03-154">**Nevýhody:** V dlouhodobém období můžou dynamické typy negativně ovlivnit přehlednost a kompatibilitu služby s klientskými aplikacemi.</span><span class="sxs-lookup"><span data-stu-id="56c03-154">**Cons:** In the long term, dynamic types can negatively impact the clarity and the compatibility of a service with client apps.</span></span> <span data-ttu-id="56c03-155">Kromě toho middlewarský software, jako je swashbuckle, nemůže poskytnout stejnou úroveň dokumentace k vráceným typům, pokud používáte dynamické typy.</span><span class="sxs-lookup"><span data-stu-id="56c03-155">In addition, middleware software like Swashbuckle cannot provide the same level of documentation on returned types if using dynamic types.</span></span>

### <a name="viewmodel-as-predefined-dto-classes"></a><span data-ttu-id="56c03-156">ViewModel jako předdefinované třídy DTO</span><span class="sxs-lookup"><span data-stu-id="56c03-156">ViewModel as predefined DTO classes</span></span>

<span data-ttu-id="56c03-157">**Odborníci**: statické a předdefinované třídy ViewModel, jako je například kontrakty založené na explicitních třídách DTO, jsou jednoznačně vhodnější pro veřejná rozhraní API, ale také pro dlouhodobé mikroslužby, i když jsou používány pouze stejnou aplikací.</span><span class="sxs-lookup"><span data-stu-id="56c03-157">**Pros**: Having static, predefined ViewModel classes, like "contracts" based on explicit DTO classes, is definitely better for public APIs but also for long-term microservices, even if they are only used by the same application.</span></span>

<span data-ttu-id="56c03-158">Pokud chcete určit typy odezvy pro Swagger, musíte jako návratový typ použít explicitní třídy DTO.</span><span class="sxs-lookup"><span data-stu-id="56c03-158">If you want to specify response types for Swagger, you need to use explicit DTO classes as the return type.</span></span> <span data-ttu-id="56c03-159">Předdefinované třídy DTO proto umožňují nabízet bohatší informace z Swagger.</span><span class="sxs-lookup"><span data-stu-id="56c03-159">Therefore, predefined DTO classes allow you to offer richer information from Swagger.</span></span> <span data-ttu-id="56c03-160">Což vylepšuje dokumentaci rozhraní API a kompatibilitu při využívání rozhraní API.</span><span class="sxs-lookup"><span data-stu-id="56c03-160">That improves the API documentation and compatibility when consuming an API.</span></span>

<span data-ttu-id="56c03-161">**Nevýhody**: jak bylo zmíněno dříve, při aktualizaci kódu je potřeba provést několik dalších kroků, které aktualizují třídy DTO.</span><span class="sxs-lookup"><span data-stu-id="56c03-161">**Cons**: As mentioned earlier, when updating the code, it takes some more steps to update the DTO classes.</span></span>

<span data-ttu-id="56c03-162">*Tip na základě našeho prostředí*: v dotazech implementovaných při řazení mikroslužeb v eShopOnContainers jsme začali vyvíjet pomocí dynamických ViewModels, protože byly jednoduché a agilní na fázích předčasného vývoje.</span><span class="sxs-lookup"><span data-stu-id="56c03-162">*Tip based on our experience*: In the queries implemented at the Ordering microservice in eShopOnContainers, we started developing by using dynamic ViewModels as it was straightforward and agile on the early development stages.</span></span> <span data-ttu-id="56c03-163">Ale jakmile byl vývoj stabilizovaný, rozhodli jsme se refaktorovat rozhraní API a použít pro ViewModels statické nebo předem definované DTO, protože je jasný pro spotřebitele mikroslužeb, aby znali explicitní typy DTO, které se používají jako "kontrakty".</span><span class="sxs-lookup"><span data-stu-id="56c03-163">But, once the development was stabilized, we chose to refactor the APIs and use static or pre-defined DTOs for the ViewModels, because it is clearer for the microservice's consumers to know explicit DTO types, used as "contracts".</span></span>

<span data-ttu-id="56c03-164">V následujícím příkladu můžete vidět, jak dotaz vrací data pomocí explicitní třídy ViewModel DTO: třídy OrderSummary.</span><span class="sxs-lookup"><span data-stu-id="56c03-164">In the following example, you can see how the query is returning data by using an explicit ViewModel DTO class: the OrderSummary class.</span></span>

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

#### <a name="describe-response-types-of-web-apis"></a><span data-ttu-id="56c03-165">Popis typů odpovědí webových rozhraní API</span><span class="sxs-lookup"><span data-stu-id="56c03-165">Describe response types of Web APIs</span></span>

<span data-ttu-id="56c03-166">Vývojáři, kteří využívají webová rozhraní API a mikroslužby, mají největší obavy s tím, co se vrátí – konkrétně typy a chybové kódy (Pokud není standard).</span><span class="sxs-lookup"><span data-stu-id="56c03-166">Developers consuming web APIs and microservices are most concerned with what is returned—specifically response types and error codes (if not standard).</span></span> <span data-ttu-id="56c03-167">Typy odpovědí jsou zpracovávány v komentářích XML a datových anotacích.</span><span class="sxs-lookup"><span data-stu-id="56c03-167">The response types are handled in the XML comments and data annotations.</span></span>

<span data-ttu-id="56c03-168">Bez správné dokumentace v uživatelském rozhraní Swagger nemá spotřebitel znalosti o tom, jaké typy jsou vraceny nebo jaké kódy HTTP je možné vrátit.</span><span class="sxs-lookup"><span data-stu-id="56c03-168">Without proper documentation in the Swagger UI, the consumer lacks knowledge of what types are being returned or what HTTP codes can be returned.</span></span> <span data-ttu-id="56c03-169">Tento problém je vyřešen přidáním <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> , takže swashbuckle může generovat rozsáhlejší informace o návratovém modelu a hodnotách rozhraní API, jak je znázorněno v následujícím kódu:</span><span class="sxs-lookup"><span data-stu-id="56c03-169">That problem is fixed by adding the <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, so Swashbuckle can generate richer information about the API return model and values, as shown in the following code:</span></span>

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

<span data-ttu-id="56c03-170">`ProducesResponseType`Atribut však nemůže použít Dynamic jako typ, ale vyžaduje použití explicitních typů, jako je `OrderSummary` ViewModel DTO, jak je znázorněno v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="56c03-170">However, the `ProducesResponseType` attribute cannot use dynamic as a type but requires to use explicit types, like the `OrderSummary` ViewModel DTO, shown in the following example:</span></span>

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

<span data-ttu-id="56c03-171">To je další důvod, proč jsou explicitní vrácené typy lepší než dynamické typy v dlouhodobém horizontu.</span><span class="sxs-lookup"><span data-stu-id="56c03-171">This is another reason why explicit returned types are better than dynamic types, in the long term.</span></span> <span data-ttu-id="56c03-172">Při použití `ProducesResponseType` atributu můžete také určit, jaký je očekávaný výsledek v souvislosti s možnými chybami protokolu HTTP/kódy, například 200, 400 atd.</span><span class="sxs-lookup"><span data-stu-id="56c03-172">When using the `ProducesResponseType` attribute, you can also specify what is the expected outcome in regards possible HTTP errors/codes, like 200, 400, etc.</span></span>

<span data-ttu-id="56c03-173">Na následujícím obrázku vidíte, jak uživatelské rozhraní Swagger zobrazuje ResponseType informace.</span><span class="sxs-lookup"><span data-stu-id="56c03-173">In the following image, you can see how Swagger UI shows the ResponseType information.</span></span>

![Snímek obrazovky se stránkou uživatelského rozhraní Swagger pro rozhraní API řazení](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

<span data-ttu-id="56c03-175">**Obrázek 7-5**.</span><span class="sxs-lookup"><span data-stu-id="56c03-175">**Figure 7-5**.</span></span> <span data-ttu-id="56c03-176">Uživatelské rozhraní Swagger zobrazující typy odpovědí a možné stavové kódy HTTP z webového rozhraní API</span><span class="sxs-lookup"><span data-stu-id="56c03-176">Swagger UI showing response types and possible HTTP status codes from a Web API</span></span>

<span data-ttu-id="56c03-177">Obrázek ukazuje několik ukázkových hodnot na základě typů ViewModel a možných stavových kódů HTTP, které mohou být vráceny.</span><span class="sxs-lookup"><span data-stu-id="56c03-177">The image shows some example values based on the ViewModel types and the possible HTTP status codes that can be returned.</span></span>

## <a name="additional-resources"></a><span data-ttu-id="56c03-178">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="56c03-178">Additional resources</span></span>

- <span data-ttu-id="56c03-179">**Dapper**</span><span class="sxs-lookup"><span data-stu-id="56c03-179">**Dapper**</span></span>  
 <https://github.com/StackExchange/dapper-dot-net>

- <span data-ttu-id="56c03-180">**Julie Lerman. Datové body – Dapperem, Entity Framework a hybridní aplikace (článek na webu MSDN Magazine)**</span><span class="sxs-lookup"><span data-stu-id="56c03-180">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN magazine article)**</span></span>  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- <span data-ttu-id="56c03-181">**Stránky nápovědy k webovému rozhraní API technologie ASP.NET Core využívající Swagger**</span><span class="sxs-lookup"><span data-stu-id="56c03-181">**ASP.NET Core Web API Help Pages using Swagger**</span></span>  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
><span data-ttu-id="56c03-182">[Předchozí](eshoponcontainers-cqrs-ddd-microservice.md) 
> [Další](ddd-oriented-microservice.md)</span><span class="sxs-lookup"><span data-stu-id="56c03-182">[Previous](eshoponcontainers-cqrs-ddd-microservice.md)
[Next](ddd-oriented-microservice.md)</span></span>
