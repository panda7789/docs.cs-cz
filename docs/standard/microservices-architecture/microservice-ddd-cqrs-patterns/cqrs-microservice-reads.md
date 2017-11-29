---
title: "Implementace čtení či dotazy v CQRS mikroslužbu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace čtení či dotazy v CQRS mikroslužbu"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 05/26/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.openlocfilehash: e017aaaa701d8033110be8d6244d3e1120fc4fd9
ms.sourcegitcommit: bd1ef61f4bb794b25383d3d72e71041a5ced172e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/18/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a><span data-ttu-id="0d978-104">Implementace čtení či dotazy v CQRS mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="0d978-104">Implementing reads/queries in a CQRS microservice</span></span>

<span data-ttu-id="0d978-105">Řazení mikroslužbu z aplikace eShopOnContainers odkaz pro čtení nebo dotazy, implementuje dotazy nezávisle DDD modelu a transakční oblasti.</span><span class="sxs-lookup"><span data-stu-id="0d978-105">For reads/queries, the ordering microservice from the eShopOnContainers reference application implements the queries independently from the DDD model and transactional area.</span></span> <span data-ttu-id="0d978-106">K tomu bylo potřeba především, protože požadavky pro dotazy a transakce se výrazně liší.</span><span class="sxs-lookup"><span data-stu-id="0d978-106">This was done primarily because the demands for queries and for transactions are drastically different.</span></span> <span data-ttu-id="0d978-107">Zápisy provedení transakcí, které musí být v souladu s logiku domény.</span><span class="sxs-lookup"><span data-stu-id="0d978-107">Writes execute transactions that must be compliant with the domain logic.</span></span> <span data-ttu-id="0d978-108">Dotazy, na druhé straně jsou idempotent a může být oddělené od domény pravidel.</span><span class="sxs-lookup"><span data-stu-id="0d978-108">Queries, on the other hand, are idempotent and can be segregated from the domain rules.</span></span>

<span data-ttu-id="0d978-109">Přístup je jednoduchý, jak je znázorněno v obrázek 9-3.</span><span class="sxs-lookup"><span data-stu-id="0d978-109">The approach is simple, as shown in Figure 9-3.</span></span> <span data-ttu-id="0d978-110">Rozhraní API je implementováno modulem řadiče webového rozhraní API pomocí jakékoliv infrastruktury (třeba micro ORM jako Dapper) a vrácení dynamické ViewModels podle potřeb uživatelského rozhraní aplikace.</span><span class="sxs-lookup"><span data-stu-id="0d978-110">The API interface is implemented by the Web API controllers using any infrastructure (such as a micro ORM like Dapper) and returning dynamic ViewModels depending on the needs of the UI applications.</span></span>

![](./media/image3.png)

<span data-ttu-id="0d978-111">**Obrázek 9-3**.</span><span class="sxs-lookup"><span data-stu-id="0d978-111">**Figure 9-3**.</span></span> <span data-ttu-id="0d978-112">Nejjednodušším přístupem pro dotazy v CQRS mikroslužbu</span><span class="sxs-lookup"><span data-stu-id="0d978-112">The simplest approach for queries in a CQRS microservice</span></span>

<span data-ttu-id="0d978-113">Toto je nejjednodušší možný přístup pro dotazy.</span><span class="sxs-lookup"><span data-stu-id="0d978-113">This is the simplest possible approach for queries.</span></span> <span data-ttu-id="0d978-114">Definice dotazu dotaz na databázi a vrátit dynamické ViewModel vytvořené za chodu při každém dotazu.</span><span class="sxs-lookup"><span data-stu-id="0d978-114">The query definitions query the database and return a dynamic ViewModel built on the fly for each query.</span></span> <span data-ttu-id="0d978-115">Vzhledem k tomu, že dotazy jsou idempotent, že nedojde ke změně dat bez ohledu na to, kolikrát spuštění dotazu.</span><span class="sxs-lookup"><span data-stu-id="0d978-115">Since the queries are idempotent, they will not change the data no matter how many times you run a query.</span></span> <span data-ttu-id="0d978-116">Proto není potřeba být omezena žádnému DDD vzoru používá na straně transakcí, jako agregace a dalšími vzory, a proto dotazy, jsou odděleni od oblasti transakcí.</span><span class="sxs-lookup"><span data-stu-id="0d978-116">Therefore, you do not need to be restricted by any DDD pattern used in the transactional side, like aggregates and other patterns, and that is why queries are separated from the transactional area.</span></span> <span data-ttu-id="0d978-117">Jednoduše dotaz na databázi pro data, která je uživatelské rozhraní a vrátit dynamické ViewModel, který nemusí být staticky definovanými v odkudkoli (žádné třídy pro ViewModels) s výjimkou v příkazech SQL, sami.</span><span class="sxs-lookup"><span data-stu-id="0d978-117">You simply query the database for the data that the UI needs and return a dynamic ViewModel that does not need to be statically defined anywhere (no classes for the ViewModels) except in the SQL statements themselves.</span></span>

<span data-ttu-id="0d978-118">Vzhledem k tomu, že toto je jednoduchá přístup, vyžaduje se kód pro dotazy na straně (například kódu pomocí micro, jako jsou ORM [Dapper](https://github.com/StackExchange/Dapper)) může být implementováno [v rámci stejné projekt webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span><span class="sxs-lookup"><span data-stu-id="0d978-118">Since this is a simple approach, the code required for the queries side (such as code using a micro ORM like [Dapper](https://github.com/StackExchange/Dapper)) can be implemented [within the same Web API project](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs).</span></span> <span data-ttu-id="0d978-119">Na obrázku 9 – 4 je to.</span><span class="sxs-lookup"><span data-stu-id="0d978-119">Figure 9-4 shows this.</span></span> <span data-ttu-id="0d978-120">Dotazy jsou definovány v **Ordering.API** mikroslužbu projektu v eShopOnContainers řešení.</span><span class="sxs-lookup"><span data-stu-id="0d978-120">The queries are defined in the **Ordering.API** microservice project within the eShopOnContainers solution.</span></span>

![](./media/image4.png)

<span data-ttu-id="0d978-121">**Obrázek 9 – 4**.</span><span class="sxs-lookup"><span data-stu-id="0d978-121">**Figure 9-4**.</span></span> <span data-ttu-id="0d978-122">Dotazy v mikroslužbu řazení v eShopOnContainers</span><span class="sxs-lookup"><span data-stu-id="0d978-122">Queries in the Ordering microservice in eShopOnContainers</span></span>

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a><span data-ttu-id="0d978-123">Pomocí ViewModels konkrétně vytvořené pro klientské aplikace, nezávislé na omezení domény modelu.</span><span class="sxs-lookup"><span data-stu-id="0d978-123">Using ViewModels specifically made for client apps, independent from domain model constraints</span></span>

<span data-ttu-id="0d978-124">Vzhledem k tomu, že dotazy jsou provedena za účelem získání dat potřebných v klientských aplikacích, typ vrácený konkrétně lze pro klienty, na základě dat vrácených dotazy.</span><span class="sxs-lookup"><span data-stu-id="0d978-124">Since the queries are performed to obtain the data needed by the client applications, the returned type can be specifically made for the clients, based on the data returned by the queries.</span></span> <span data-ttu-id="0d978-125">Tyto modely nebo objekty přenos dat (DTOs), se nazývají ViewModels.</span><span class="sxs-lookup"><span data-stu-id="0d978-125">These models, or Data Transfer Objects (DTOs), are called ViewModels.</span></span>

<span data-ttu-id="0d978-126">Vrácená data (ViewModel) může být výsledkem spojování dat z více entit nebo tabulky v databázi, nebo dokonce i v jiných více agregace definované v modelu domény oblasti transakcí.</span><span class="sxs-lookup"><span data-stu-id="0d978-126">The returned data (ViewModel) can be the result of joining data from multiple entities or tables in the database, or even across multiple aggregates defined in the domain model for the transactional area.</span></span> <span data-ttu-id="0d978-127">V takovém případě vzhledem k tomu, že při vytváření dotazů nezávislé na modelu domény, agregace hranice a omezení jsou zcela ignorovány a můžete všechny tabulky a sloupce, který může být nutné dotazů.</span><span class="sxs-lookup"><span data-stu-id="0d978-127">In this case, because you are creating queries independent of the domain model, the aggregates boundaries and constraints are completely ignored and you are free to query any table and column you might need.</span></span> <span data-ttu-id="0d978-128">Tento přístup poskytuje flexibilitu a produktivitu pro vývojáře vytváření nebo aktualizaci dotazy.</span><span class="sxs-lookup"><span data-stu-id="0d978-128">This approach provides great flexibility and productivity for the developers creating or updating the queries.</span></span>

<span data-ttu-id="0d978-129">ViewModels může být statické typy definované v třídy.</span><span class="sxs-lookup"><span data-stu-id="0d978-129">The ViewModels can be static types defined in classes.</span></span> <span data-ttu-id="0d978-130">Nebo je lze vytvořit dynamicky na základě dotazů provést (jak je implementované v řazení mikroslužbu), což je velmi agilní pro vývojáře.</span><span class="sxs-lookup"><span data-stu-id="0d978-130">Or they can be created dynamically based on the queries performed (as is implemented in the ordering microservice), which is very agile for developers.</span></span>

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a><span data-ttu-id="0d978-131">Použití Dapper jako malých ORM provádět dotazy</span><span class="sxs-lookup"><span data-stu-id="0d978-131">Using Dapper as a micro ORM to perform queries</span></span> 

<span data-ttu-id="0d978-132">Pro zadávání dotazů můžete použít všechny malých ORM, Entity Framework Core nebo i prostý ADO.NET.</span><span class="sxs-lookup"><span data-stu-id="0d978-132">You can use any micro ORM, Entity Framework Core, or even plain ADO.NET for querying.</span></span> <span data-ttu-id="0d978-133">V ukázkové aplikace jsme vybrali Dapper pro řazení mikroslužbu v eShopOnContainers jako dobrým příkladem oblíbených malých ORM.</span><span class="sxs-lookup"><span data-stu-id="0d978-133">In the sample application, we selected Dapper for the ordering microservice in eShopOnContainers as a good example of a popular micro ORM.</span></span> <span data-ttu-id="0d978-134">Může probíhat prostý dotazy SQL s vysoký výkon, protože je velmi malé rozhraní.</span><span class="sxs-lookup"><span data-stu-id="0d978-134">It can run plain SQL queries with great performance, because it is a very light framework.</span></span> <span data-ttu-id="0d978-135">Pomocí Dapper, můžete napsat dotaz SQL, který můžete používat a připojení k několika tabulkám.</span><span class="sxs-lookup"><span data-stu-id="0d978-135">Using Dapper, you can write a SQL query that can access and join multiple tables.</span></span>

<span data-ttu-id="0d978-136">Dapper je opensourcový projekt (původně vytvořil šafrán Sam) a je součástí stavební bloky v [Stack Overflow](https://stackoverflow.com/).</span><span class="sxs-lookup"><span data-stu-id="0d978-136">Dapper is an open source project (original created by Sam Saffron), and is part of the building blocks used in [Stack Overflow](https://stackoverflow.com/).</span></span> <span data-ttu-id="0d978-137">Pokud chcete používat Dapper, stačí nainstalovat přes [balíček Dapper NuGet](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku.</span><span class="sxs-lookup"><span data-stu-id="0d978-137">To use Dapper, you just need to install it through the [Dapper NuGet package](https://www.nuget.org/packages/Dapper), as shown in the following figure.</span></span>

![](./media/image5.png)

<span data-ttu-id="0d978-138">Budete také muset přidat, pomocí příkazu tak kódu má přístup k Dapper rozšiřující metody.</span><span class="sxs-lookup"><span data-stu-id="0d978-138">You will also need to add a using statement so your code has access to the Dapper extension methods.</span></span>

<span data-ttu-id="0d978-139">Pokud používáte Dapper ve vašem kódu, použijete přímo k dispozici v oboru názvů System.Data.SqlClient SqlClient třídu.</span><span class="sxs-lookup"><span data-stu-id="0d978-139">When you use Dapper in your code, you directly use the SqlClient class available in the System.Data.SqlClient namespace.</span></span> <span data-ttu-id="0d978-140">Prostřednictvím metody QueryAsync a jiné metody rozšíření, které rozšiřují třídu SqlClient můžete jednoduše spouštět dotazy přehledné a původce způsobem.</span><span class="sxs-lookup"><span data-stu-id="0d978-140">Through the QueryAsync method and other extension methods which extend the SqlClient class, you can simply run queries in a straightforward and performant way.</span></span>

## <a name="dynamic-and-static-viewmodels"></a><span data-ttu-id="0d978-141">Dynamických a statických ViewModels</span><span class="sxs-lookup"><span data-stu-id="0d978-141">Dynamic and static ViewModels</span></span>

<span data-ttu-id="0d978-142">Jak je znázorněno v následujícím kódu z řazení mikroslužbu, většina ViewModels vrácený dotazy jsou implementované jako *dynamické*.</span><span class="sxs-lookup"><span data-stu-id="0d978-142">As shown in the following code from the ordering microservice, most of the ViewModels returned by the queries are implemented as *dynamic*.</span></span> <span data-ttu-id="0d978-143">To znamená, že do něj podmnožinu atributy, které mají být vráceny je založen na samotný dotaz.</span><span class="sxs-lookup"><span data-stu-id="0d978-143">That means that the subset of attributes to be returned is based on the query itself.</span></span> <span data-ttu-id="0d978-144">Pokud přidáte nový sloupec dotazu nebo spojení, tato data dynamicky přidány do vrácený ViewModel.</span><span class="sxs-lookup"><span data-stu-id="0d978-144">If you add a new column to the query or join, that data is dynamically added to the returned ViewModel.</span></span> <span data-ttu-id="0d978-145">Tento přístup snižuje nutnost úpravě dotazů v reakci na aktualizace základní datový model, provedení tohoto návrhu přístupu flexibilnější a toleranci vůči budoucí změny.</span><span class="sxs-lookup"><span data-stu-id="0d978-145">This approach reduces the need to modify queries in response to updates to the underlying data model, making this design approach more flexible and tolerant of future changes.</span></span>

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

<span data-ttu-id="0d978-146">Důležité je, že pomocí dynamické typ vrácený shromažďování dat bude dynamicky sestavit jako ViewModel.</span><span class="sxs-lookup"><span data-stu-id="0d978-146">The important point is that by using a dynamic type, the returned collection of data will be dynamically assembled as the ViewModel.</span></span>

<span data-ttu-id="0d978-147">Pro většinu dotazů není potřeba předdefinovat třídě DTO nebo ViewModel, který převede na kódování je snadný a produktivitu.</span><span class="sxs-lookup"><span data-stu-id="0d978-147">For most queries, you do not need to predefine a DTO or ViewModel class, which makes coding them straightforward and productive.</span></span> <span data-ttu-id="0d978-148">Pokud chcete mít ViewModels s definicí omezenější jako kontrakty, ale můžete předdefinovat ViewModels (jako jsou předdefinované DTOs).</span><span class="sxs-lookup"><span data-stu-id="0d978-148">However, you can predefine ViewModels (like predefined DTOs) if you want to have ViewModels with a more restricted definition as contracts.</span></span>

#### <a name="additional-resources"></a><span data-ttu-id="0d978-149">Další zdroje</span><span class="sxs-lookup"><span data-stu-id="0d978-149">Additional resources</span></span>

-   <span data-ttu-id="0d978-150">**Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span><span class="sxs-lookup"><span data-stu-id="0d978-150">**Dapper**
[*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)</span></span>

-   <span data-ttu-id="0d978-151">**Julie Lerman. Datové body - Dapper, rozhraní Entity Framework a hybridní aplikace (článek MSDN Mag.)**</span><span class="sxs-lookup"><span data-stu-id="0d978-151">**Julie Lerman. Data Points - Dapper, Entity Framework and Hybrid Apps (MSDN Mag. article)**</span></span>

    <span data-ttu-id="0d978-152">*https://msdn.microsoft.com/en-us/Magazine/mt703432.aspx*</span><span class="sxs-lookup"><span data-stu-id="0d978-152">*https://msdn.microsoft.com/en-us/magazine/mt703432.aspx*</span></span>


>[!div class="step-by-step"]
<span data-ttu-id="0d978-153">[Předchozí] (eshoponcontainers-cqrs-ddd-microservice.md) [Další] (ddd-zaměřené na konkrétní microservice.md)</span><span class="sxs-lookup"><span data-stu-id="0d978-153">[Previous] (eshoponcontainers-cqrs-ddd-microservice.md) [Next] (ddd-oriented-microservice.md)</span></span>
