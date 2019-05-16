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
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implementace čtení nebo dotazů v mikroslužbě CQRS

Pro čtení nebo dotazů implementuje pořadí mikroslužeb z aplikace odkaz na aplikaci eShopOnContainers dotazy odděleně od modelu DDD a transakční oblasti. To bylo provedeno primárně, protože požadavky pro dotazy a transakce se výrazně liší. Zápisy provádět transakce, které musí být v souladu se logiku domény. Dotazy, na druhé straně jsou idempotentní a může být odděleni od domény pravidla.

Tento přístup je jednoduchý, jak je znázorněno v obrázek 7 – 3. Kontrolerů rozhraní Web API pomocí jakékoliv infrastruktury, jako je například micro objekt relační Mapovač (ORM) určené jako Dapperem a vrací dynamický modely ViewModels v závislosti na potřebách aplikace uživatelského rozhraní je implementováno rozhraní API.

![Nejjednodušším přístupem pro dotazy na straně zjednodušený přístup modelu CQRS může být implementována pouze dotazování na databázi s Micro-ORM jako Dapperem, vrací dynamický modely ViewModel.](./media/image3.png)

**Obrázek 7 – 3**. Nejjednodušším přístupem dotazů v mikroslužbě CQRS

Toto je nejjednodušší možný přístup pro dotazy. Definice dotazů dotaz na databázi a vracet dynamické ViewModel vytvořené v reálném čase pro každý dotaz. Vzhledem k tomu, že dotazy jsou idempotentní, že nedojde ke změně dat bez ohledu na to, kolikrát můžete spustit dotaz. Proto není nutné být omezeni prostředím DDD používaným v transakcí na straně, jako je agregace a další způsoby, a proto dotazy, jsou odděleni od oblasti transakční. Jednoduše dotaz na databázi pro data, která potřebuje uživatelského rozhraní a vracet dynamické ViewModel, který nemusí být staticky kdekoli (žádné třídy pro modely ViewModel) definované s výjimkou v příkazech SQL sami.

Protože se jedná o jednoduchý přístup, vyžaduje kód pro dotazy na straně (například kód pomocí micro ORM, jako jsou [Dapperem](https://github.com/StackExchange/Dapper)) je možné implementovat [v rámci stejného projektu webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Obrázek 7 – 4 ukazuje to. Dotazy jsou definovány v **Ordering.API** mikroslužeb projektu v aplikaci eShopOnContainers řešení.

![Zobrazení Průzkumníka řešení projektu Ordering.API zobrazující aplikaci > složky dotazů.](./media/image4.png)

**Obrázek 7 – 4**. Dotazy v mikroslužbě řazení v aplikaci eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Používat modely ViewModels specificky vytvořené pro klientské aplikace, nezávisle na omezení modelu domény

Protože dotazy probíhají na získat data, která klientské aplikace potřebují, vrácený typ konkrétně lze pro klienty, na základě dat vrácených dotazy. Tyto modely nebo objekty přenosu dat (DTO), se nazývají modely ViewModel.

Vrácená data (ViewModel) může být výsledkem spojování dat z několika entit nebo tabulek v databázi, nebo dokonce napříč více agregace definované v modelu domény pro transakční oblast. Protože vytváříte dotazy nezávisle na doménový model, v tomto případě agregace hranice a omezení jsou zcela ignorovány a můžete zadávat dotazy na všechny tabulky a sloupce, který může být nutné. Tento přístup poskytuje flexibilitu a zvýšení produktivity pro vývojáře se vytváří nebo aktualizuje dotazy.

Modely ViewModels může být statické typy definované v třídách. Nebo je lze vytvořit dynamicky na základě dotazů provést (jak je implementován v pořadí mikroslužeb), což je velmi agile pro vývojáře.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Použít Dapperem jako micro ORM pro provádění dotazů 

Pro dotazování můžete použít libovolný micro ORM, Entity Framework Core nebo dokonce prostý ADO.NET. V ukázkové aplikaci pro objednávání mikroslužeb v aplikaci eShopOnContainers jako dobrý příklad oblíbených micro ORM nebyla vybrána Dapperem. Může probíhat prostý dotazy SQL s vynikajícím výkonem, protože je velmi malé framework. Dapperem můžete napsat dotaz SQL, který může přistupovat k a připojte se k několika tabulkám.

Dapperem je projekt open source (původně vytvořil Sam šafrán) a je součástí stavební bloky v [Stack Overflow](https://stackoverflow.com/). Použití Dapperem, stačí nainstalovat prostřednictvím [balíček Dapper NuGet](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku:

![Dapper balíčku jako zobrazené v zobrazení Správa balíčků NuGet v sadě Visual Studio.](./media/image4.1.png)

Musíte také přidat, a s použitím příkazu tak, že váš kód má přístup k metodám Dapper rozšíření.

Při použití Dapperem ve vašem kódu, můžete přímo použít <xref:System.Data.SqlClient.SqlConnection> třídy, které jsou k dispozici v <xref:System.Data.SqlClient> oboru názvů. Metoda QueryAsync a další rozšiřující metody, které rozšiřují <xref:System.Data.SqlClient.SqlConnection> třídy, můžete jednoduše spustit dotazy jednoduché a výkonné způsobem.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamická zobrazení vs. statické modely ViewModels

Při návratu modely ViewModels do klientské aplikace na straně serveru, se dá chápat tyto modely ViewModels jako DTO (objekty přenosu dat), které mohou být různé entity interní doméně modelu entity, protože modely ViewModels uchovávání dat tak, jak klientská aplikace potřebuje. Proto v mnoha případech můžete agregovat data přicházející z několika entit domény a compose modely ViewModels přesně podle jak klientská aplikace musí tato data.

Tyto modely ViewModels nebo DTO může být definované explicitně (jako vlastník datové třídy) stejně jako `OrderSummary` uvedená v pozdější fragment kódu, nebo třída může vrátit pouze dynamické modely ViewModels nebo dynamické DTO, jednoduše na základě atributů vráceny vaše dotazy jako dynamické Zadejte.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako dynamický typ.

Jak je znázorněno v následujícím kódu `ViewModel` může být přímo vrácená metodou dotazy jenom vrácením *dynamické* typ, který interně je na základě atributů vrácených dotazem. To znamená, že dílčí sadu atributů, které mají být vráceny je založen na samotný dotaz. Proto pokud přidáte nový sloupec do dotazu nebo join, tato data se dynamicky přidat na vrácenou `ViewModel`.

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

Důležité je, že pomocí dynamický typ vrácené kolekce dat je dynamicky sestavena jako ViewModel.

**V oblasti IT:** Tento přístup snižuje nutnost upravit statických tříd ViewModel pokaždé, když aktualizujete věty SQL dotazu, což tento postup návrhu poměrně agile při psaní kódu, jednoduchý a rychlý rozvoj ve vztahu budoucí změny.

**Nevýhody:** V dlouhodobém horizontu dynamické typy může mít negativní dopad jasné a kompatibility služby pomocí klientské aplikace. Kromě toho middleware softwarem, jako je Swashbuckle nemůže poskytovat stejnou úroveň dokumentace u typů vrácených při použití dynamické typy.

### <a name="viewmodel-as-predefined-dto-classes"></a>Jako předdefinovaných DTO tříd ViewModel

**Profesionálové**: Statické předdefinovaných tříd ViewModel, jako je "smluv" podle třídy explicitní objekt DTO, je určitě lepší pro veřejné rozhraní API, ale i na dlouhodobém horizontu mikroslužeb, i v případě, že se používají pouze ve stejné aplikaci.

Pokud chcete určit typy odpověď pro Swagger, budete muset použít explicitní DTO třídy jako návratový typ. Předdefinované třídy DTO proto umožňují nabízí bohatší informace ze Swaggeru. Který zlepšuje dokumentaci k rozhraní API a kompatibility při využívání rozhraní API.

**Nevýhody**: Jak bylo zmíněno výše, při aktualizaci kódu, má některé další kroky a aktualizujete DTO třídy.

*Tip založené na našich zkušenostech*: V dotazech implementovat mikroslužby řazení v aplikaci eShopOnContainers můžeme začít vyvíjet pomocí dynamické modely ViewModels jako byl v raných fázích vývoje velmi jednoduché a flexibilní. Ale po vývoj byla stabilizovaná, Rozhodli jsme se refaktorovat rozhraní API a použití statické nebo předem definované DTO pro modely ViewModels, protože je jasnější mikroslužbách uživatelům vědět, explicitních typů objekt DTO, použít jako "kontrakty".

V následujícím příkladu vidíte, jak dotaz vrací data pomocí explicitní tříd ViewModel DTO: OrderSummary třídy.

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

#### <a name="describe-response-types-of-web-apis"></a>Popisují typy odezvy webové rozhraní API

Vývojáři využívající webové rozhraní API a mikroslužeb jsou nejvíce zajímají co bude vráceno – konkrétně typů odpovědi a chybové kódy (Pokud není standard). Tyto jsou zpracovány v poznámkách komentáře a data XML.

Bez správnou dokumentaci v Uživatelském rozhraní Swagger, nemá příjemce znalostní báze se vrací typy nebo které HTTP může být vrácen kódy. Tento problém vyřešen tak, že přidáte <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>, takže Swashbuckle může generovat rozsáhlejší informace o vrácené modelu rozhraní API a hodnoty, jak je znázorněno v následujícím kódu:

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

Ale `ProducesResponseType` atribut nelze použít jako typ, ale vyžaduje použití explicitních typů, jako je dynamické `OrderSummary` ViewModel DTO, je znázorněno v následujícím příkladu:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

To je další důvod, proč explicitní vrácené typy jsou lepší než dynamické typy v dlouhodobém horizontu. Při použití `ProducesResponseType` atribut, můžete také určit, co je očekávaný výsledek v kódy nebo pokud jde o možné HTTP chyby, jako je třeba 200, 400, atd.

Na následujícím obrázku vidíte způsob, jakým zobrazuje uživatelské rozhraní Swagger informace hodnotu ResponseType.

![Zobrazení prohlížeče s stránka uživatelského rozhraní Swagger pro rozhraní API pro řazení.](./media/image5.png)

**Obrázek 7 – 5**. Zobrazení typů odpovědi a je to možné stavové kódy HTTP z webového rozhraní API uživatelské rozhraní swagger

Vidíte na obrázku výše jsou některé příklady hodnot na základě typů ViewModel a je to možné stavové kódy HTTP, které mohou být vráceny.

## <a name="additional-resources"></a>Další zdroje

- **Dapper** \
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Datové body – Dapper, Entity Framework a hybridních aplikací (článek znalostní báze MSDN Mag.)** \
  <https://msdn.microsoft.com/magazine/mt703432.aspx>

- **ASP.NET Core webové rozhraní API stránky nápovědy k využívající Swagger** \
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Předchozí](eshoponcontainers-cqrs-ddd-microservice.md)
>[další](ddd-oriented-microservice.md)
