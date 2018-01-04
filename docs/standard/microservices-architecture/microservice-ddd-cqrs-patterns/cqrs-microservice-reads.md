---
title: "Implementace čtení či dotazy v CQRS mikroslužbu"
description: "Architektura Mikroslužeb .NET pro aplikace .NET Kontejnerizované | Implementace čtení či dotazy v CQRS mikroslužbu"
keywords: "Docker, Mikroslužeb, ASP.NET, kontejneru"
author: CESARDELATORRE
ms.author: wiwagn
ms.date: 11/02/2017
ms.prod: .net-core
ms.technology: dotnet-docker
ms.topic: article
ms.workload:
- dotnet
- dotnetcore
ms.openlocfilehash: ca9bcefb317d2b3c7c225b773918ca4a2484cb8f
ms.sourcegitcommit: e7f04439d78909229506b56935a1105a4149ff3d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/23/2017
---
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>Implementace čtení či dotazy v CQRS mikroslužbu

Řazení mikroslužbu z aplikace eShopOnContainers odkaz pro čtení nebo dotazy, implementuje dotazy nezávisle DDD modelu a transakční oblasti. K tomu bylo potřeba především, protože požadavky pro dotazy a transakce se výrazně liší. Zápisy provedení transakcí, které musí být v souladu s logiku domény. Dotazy, na druhé straně jsou idempotent a může být oddělené od domény pravidel.

Přístup je jednoduchý, jak je znázorněno v obrázek 9-3. Rozhraní API je implementováno modulem řadiče webového rozhraní API pomocí jakékoliv infrastruktury, jako je například micro relační Mapper ORM (Object) jako Dapper a vrátí dynamické ViewModels podle potřeb uživatelského rozhraní aplikace.

![](./media/image3.png)

**Obrázek 9-3**. Nejjednodušším přístupem pro dotazy v CQRS mikroslužbu

Toto je nejjednodušší možný přístup pro dotazy. Definice dotazu dotaz na databázi a vrátit dynamické ViewModel vytvořené za chodu při každém dotazu. Vzhledem k tomu, že dotazy jsou idempotent, že nedojde ke změně dat bez ohledu na to, kolikrát spuštění dotazu. Proto nemusíte být omezena žádnému DDD vzoru používá na straně transakcí, jako agregace a dalšími vzory, a proto dotazy, jsou odděleni od oblasti transakcí. Jednoduše dotaz na databázi pro data, která je uživatelské rozhraní a vrátit dynamické ViewModel, který nemusí být staticky definovanými v odkudkoli (žádné třídy pro ViewModels) s výjimkou v příkazech SQL, sami.

Vzhledem k tomu, že toto je jednoduchá přístup, vyžaduje se kód pro dotazy na straně (například kódu pomocí micro, jako jsou ORM [Dapper](https://github.com/StackExchange/Dapper)) může být implementováno [v rámci stejné projekt webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Na obrázku 9 – 4 je to. Dotazy jsou definovány v **Ordering.API** mikroslužbu projektu v eShopOnContainers řešení.

![](./media/image4.png)

**Obrázek 9 – 4**. Dotazy v mikroslužbu řazení v eShopOnContainers

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Pomocí ViewModels konkrétně vytvořené pro klientské aplikace, nezávislé na omezení domény modelu.

Vzhledem k tomu, že dotazy jsou provedena za účelem získání dat potřebných v klientských aplikacích, typ vrácený konkrétně lze pro klienty, na základě dat vrácených dotazy. Tyto modely nebo objekty přenos dat (DTOs), se nazývají ViewModels.

Vrácená data (ViewModel) může být výsledkem spojování dat z více entit nebo tabulky v databázi, nebo dokonce i v jiných více agregace definované v modelu domény oblasti transakcí. V takovém případě vzhledem k tomu, že při vytváření dotazů nezávislé na modelu domény, agregace hranice a omezení jsou zcela ignorovány a jste volné dotaz na všechny tabulky a sloupce, který může být nutné. Tento přístup poskytuje flexibilitu a produktivitu pro vývojáře vytváření nebo aktualizaci dotazy.

ViewModels může být statické typy definované v třídy. Nebo je lze vytvořit dynamicky na základě dotazů provést (jak je implementované v řazení mikroslužbu), což je velmi agilní pro vývojáře.

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>Použití Dapper jako malých ORM provádět dotazy

Pro zadávání dotazů můžete použít všechny malých ORM, Entity Framework Core nebo i prostý ADO.NET. V ukázkové aplikaci pro řazení mikroslužbu v eShopOnContainers jako dobrým příkladem oblíbených malých ORM byl vybrán Dapper. Může probíhat prostý dotazy SQL s vysoký výkon, protože je velmi malé rozhraní. Pomocí Dapper, můžete napsat dotaz SQL, který můžete používat a připojení k několika tabulkám.

Dapper je otevřený projekt (původně vytvořil šafrán Sam) a je součástí stavební bloky v [Stack Overflow](https://stackoverflow.com/). Pokud chcete používat Dapper, stačí nainstalovat přes [balíček Dapper NuGet](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku:

![](./media/image4.1.png)

Musíte taky přidat pomocí příkazu tak kódu má přístup k Dapper rozšiřující metody.

Pokud používáte Dapper ve vašem kódu, přímo použít <xref:System.Data.SqlClient.SqlConnection> třídy, které jsou k dispozici v <xref:System.Data.SqlClient> oboru názvů. Prostřednictvím metody QueryAsync a dalších rozšiřující metody, které rozšiřují <xref:System.Data.SqlClient.SqlConnection> třídu, můžete jednoduše spouštět dotazy přehledné a původce způsobem.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamická zobrazení vs. statické ViewModels

Při vracení ViewModels z na straně serveru, na klientských aplikací, si myslíte o těchto ViewModels jako DTOs, které může být jiné na interní doméně entity modelu entity, protože blokování ViewModels data potřebuje způsob, jakým klientské aplikace. Proto v mnoha případech můžete agregovat data z více entit domény a tvoří ViewModels přesně podle jak klientská aplikace musí tato data.

Tyto ViewModels nebo DTOs může být definované explicitně (jako datové třídy držitele) jako [OrderSummary](https://github.com/dotnet-architecture/eShopOnContainers/blob/dev/src/Services/Ordering/Ordering.API/Application/Queries/OrderViewModel.cs) třída zobrazí v novější fragment kódu, nebo může vrátit pouze dynamické ViewModels nebo dynamické DTOs jednoduše na základě atributů vrátil vaše dotazy jako `dynamic` typu.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako dynamické typ

Jak je znázorněno v následujícím kódu, ViewModel mohou být přímo vrácena v dotazech vrácením dynamické typ, který interně je na základě atributů vrácených dotazem. To znamená, že do něj podmnožinu atributy, které mají být vráceny je založen na samotný dotaz. Proto pokud dotaz nebo připojení k přidáte nový sloupec, tato data se dynamicky přidá do vrácený ViewModel.

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

Důležité je, že pomocí dynamické typ vrácený shromažďování dat je dynamicky sestavena jako ViewModel.

*Specialisté:* tento přístup snižuje nutnost upravit statické třídy ViewModel při každé aktualizaci větu SQL dotazu, díky čemuž je tento přístup návrhu poměrně agilní případě kódování, přehledné a rychle momentální ohledně budoucí změny.

*Cons:* na dlouhou dobu, můžete dynamické typy negativní dopad přehlednost a ovlivnit kompatibilitu služby s klientské aplikace. Kromě toho middleware softwaru, třeba Swagger nemůžete zadat stejnou úroveň dokumentace na vrácený typy při použití dynamické typy.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako předdefinované DTO třídy

*Specialisté:* statické předdefinované ViewModel třídy, jako jsou "smlouvami" podle třídy explicitní DTO, je výborný lepší pro veřejné rozhraní API, ale i na dlouhodobé mikroslužeb i v případě, že se používají pouze stejnou aplikací.

Pokud chcete určit typy odpovědi pro swagger, budete muset použít explicitní DTO třídy jako návratový typ. Proto předdefinované třídy DTO umožňují nabízejí širší informace ze Swaggeru. Která zvyšuje dokumentaci k rozhraní API a kompatibilitu při využívání rozhraní API.

*Cons:* jak je uvedeno dříve, při aktualizaci kód, trvá některé další kroky k aktualizaci DTO třídy.

*Tip podle našich zkušeností:* v dotazech implementovat mikroslužbu řazení v eShopOnContainers, jsme práce s vývojem pomocí dynamické ViewModels stejně jako tomu bylo velmi jednoduché a agilní počátečních fázích vývoje. Ale po vývoj byl provozním měřítku, jsme zvolili refaktorovat rozhraní API a použití statické nebo předem definované DTOs pro ViewModels, protože je jasnější pro spotřebitele mikroslužbu vědět explicitní typy DTO používá jen "smlouva".

V následujícím příkladu vidíte, jak dotaz vrací data pomocí třídu explicitní ViewModel DTO: Třída OrderSummary.

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

#### <a name="describing-response-types-of-web-apis"></a>Popisující typy odezvy webové rozhraní API

Vývojáři využívají webové rozhraní API a mikroslužeb jsou nejvíce zajímají co je vrácen – konkrétně odpovědi typy a kódy chyb (Pokud není standard). Tyto jsou zpracovávány v XML komentáře a data poznámky.

Bez správné dokumentace v uživatelském rozhraní Swagger, příjemci chybí znalostní báze se vrací jaké typy nebo jaké HTTP se může vracet kódy. Tento problém vyřešen přidáním <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, takže Swagger může generovat bohatší informace o rozhraní API návratový modelu a hodnoty, jak je znázorněno v následujícím kódu:

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

Ale `ProducesResponseType` nelze použít jako typ, ale vyžaduje explicitní typy, jako je třeba používat dynamické atribut `OrderSummary` DTO ViewModel, vidět v následujícím příkladu:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

To je další důvod, proč explicitní vrácený typy jsou lepší, než dynamické typy z dlouhodobého hlediska.
Při použití `ProducesResponseType` atribut, můžete také určit, co je očekávaný výsledek v namapoval možné chyby/kódy HTTP, jako je 200,400, atd.

Na následujícím obrázku vidíte, jak uživatelské rozhraní Swagger, jsou uvedené informace o ResponseType.

![](./media/image5.png)

**Obrázek 9-5**. Zobrazuje typy odpovědi a možné stavové kódy HTTP z webového rozhraní API uživatelské rozhraní swagger

Vidíte na obrázku výše některé ukázkové hodnoty na základě typů ViewModel a možné stavové kódy HTTP, které mohou být vráceny.

## <a name="additional-resources"></a>Další zdroje

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman. Datové body - Dapper, rozhraní Entity Framework a hybridní aplikace (článek MSDN Mag.)**

    *https://msdn.microsoft.com/Magazine/mt703432.aspx*

-   **Stránky nápovědy k webovému rozhraní API technologie ASP.NET Core využívající Swagger**

    *https://docs.microsoft.com/ASPNET/Core/tutorials/web-API-Help-Pages-Using-swagger?Tabs=Visual-Studio*

>[!div class="step-by-step"]
[Předchozí] (eshoponcontainers-cqrs-ddd-microservice.md) [Další] (ddd-zaměřené na konkrétní microservice.md)
