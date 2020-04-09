---
title: Implementace čtení nebo dotazů v mikroslužbě CQRS
description: Architektura mikroslužeb .NET pro kontejnerizované aplikace .NET | Pochopit implementaci dotazů straně CQRS na objednávání mikroslužby v eShopOnContainers pomocí Dapper.
ms.date: 10/08/2018
ms.openlocfilehash: 49f42a5035bab38f800f3ec5ea24b01fde0d2964
ms.sourcegitcommit: e3cbf26d67f7e9286c7108a2752804050762d02d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/09/2020
ms.locfileid: "80988749"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implementovat čtení nebo dotazy v mikroslužbě CQRS

Pro čtení/dotazy, řazení mikroslužby z eShopOnContainers referenční aplikace implementuje dotazy nezávisle na modelu DDD a transakční oblasti. To bylo provedeno především proto, že požadavky na dotazy a transakce jsou drasticky odlišné. Zápisy spouštějí transakce, které musí být kompatibilní s logikou domény. Dotazy, na druhé straně jsou idempotentní a mohou být odděleny od pravidel domény.

Přístup je jednoduchý, jak je znázorněno na obrázku 7-3. Rozhraní rozhraní API je implementováno řadiči webového rozhraní API pomocí libovolné infrastruktury, jako je například mikroobjektrelační mapovač (ORM), jako je Dapper, a vrácení dynamických ViewModels v závislosti na potřebách aplikací uživatelského rozhraní.

![Diagram znázorňující na straně dotazů vysoké úrovně ve zjednodušeném CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Obrázek 7-3**. Nejjednodušší přístup pro dotazy v mikroslužbě CQRS

Nejjednodušší přístup pro dotazy straně ve zjednodušené CQRS přístup lze implementovat pouze dotazování databáze s Micro-ORM jako Dapper, vrácení dynamické ViewModels. Definice dotazu dotaz databáze a vrátit dynamické ViewModel postavené na průběžný pro každý dotaz. Vzhledem k tomu, že dotazy jsou idempotentní, nebudou měnit data bez ohledu na to, kolikrát spustíte dotaz. Proto není nutné omezit žádný vzorek DDD používaný na transakční straně, jako jsou agregace a další vzorky, a proto jsou dotazy odděleny od transakční oblasti. Jednoduše dotaz databáze pro data, která potřebuje uI a vrátit dynamické ViewModel, který nemusí být staticky definovány kdekoli (žádné třídy pro ViewModels) s výjimkou samotných příkazů SQL.

Vzhledem k tomu, že se jedná o jednoduchý přístup, kód požadovaný pro straně dotazů (například kód pomocí mikro ORM jako [Dapper](https://github.com/StackExchange/Dapper)) lze implementovat [v rámci stejného projektu webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Obrázek 7-4 to ukazuje. Dotazy jsou definovány v projektu mikroslužeb **Ordering.API** v rámci řešení eShopOnContainers.

![Snímek obrazovky složky Dotazy projektu Ordering.API](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Obrázek 7-4**. Dotazy v objednávání mikroslužby v eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Použití viewmodels speciálně pro klientské aplikace, nezávislé na omezeních modelu domény

Vzhledem k tomu, že dotazy jsou prováděny k získání dat potřebných pro klientské aplikace, vrácený typ lze speciálně pro klienty, na základě dat vrácených dotazy. Tyto modely nebo objekty přenosu dat (DTO), se nazývají ViewModels.

Vrácená data (ViewModel) může být výsledkem spojování dat z více entit nebo tabulek v databázi nebo dokonce mezi více agregacemi definovanými v modelu domény pro transakční oblast. V tomto případě, protože vytváříte dotazy nezávislé na modelu domény, agregace hranice a omezení jsou zcela ignorovány a máte možnost dotazovat se na libovolnou tabulku a sloupec, který budete potřebovat. Tento přístup poskytuje velkou flexibilitu a produktivitu pro vývojáře vytváření nebo aktualizaci dotazů.

ViewModels mohou být statické typy definované ve třídách. Nebo mohou být vytvořeny dynamicky na základě provedených dotazů (jak je implementováno v objednávání mikroslužby), což je velmi agilní pro vývojáře.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Použití dapperu jako mikroORSu k provádění dotazů

Můžete použít libovolné mikro ORM, Entity Framework Core, nebo dokonce prostý ADO.NET pro dotazování. V ukázkové aplikaci byl Dapper vybrán pro objednávání mikroslužeb v eShopOnContainers jako dobrý příklad oblíbeného mikro ORM. Může spouštět prosté dotazy SQL se skvělým výkonem, protože je to velmi lehký rámec. Pomocí Dapper, můžete napsat dotaz SQL, který může přistupovat a spojit více tabulek.

Dapper je open-source projekt (originál vytvořil Sam Saffron), a je součástí stavebních bloků používaných v [Stack Přetečení](https://stackoverflow.com/). Chcete-li použít Dapper, stačí jej nainstalovat přes [balíček Dapper NuGet](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku:

![Snímek obrazovky s balíčkem Dapper v zobrazení balíčků NuGet.](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Také je třeba přidat using prohlášení, takže váš kód má přístup k metodám rozšíření Dapper.

Při použití Dapper v kódu, můžete <xref:System.Data.SqlClient.SqlConnection> přímo použít <xref:System.Data.SqlClient> třídu k dispozici v oboru názvů. Prostřednictvím QueryAsync metody a další <xref:System.Data.SqlClient.SqlConnection> metody rozšíření, které rozšiřují třídu, můžete jednoduše spustit dotazy v jednoduché a performant způsobem.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamické versus statické ViewModels

Při vracení ViewModels z klientské aplikace na straně serveru, můžete si myslet, že tyto ViewModels jako DTO (objekty přenosu dat), které se mohou lišit od interní chložských entit modelu entity, protože ViewModels uchovávat data tak, jak klientská aplikace potřebuje. Proto v mnoha případech můžete agregovat data pocházející z více entit domény a sestavit ViewModels přesně podle toho, jak klientská aplikace potřebuje tato data.

Tyto ViewModels nebo DTO lze explicitně definovat (jako `OrderSummary` třídy držitele dat), jako je třída zobrazená v pozdějším fragmentu kódu, nebo můžete vrátit dynamické ViewModels nebo dynamické DTO jednoduše na základě atributů vrácených dotazy jako dynamický typ.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako dynamický typ

Jak je znázorněno v `ViewModel` následujícím kódu, a může být přímo vrácena dotazy pouze vrácení *dynamického* typu, který interně je založen na atributy vrácené dotazem. To znamená, že podmnožina atributů, které mají být vráceny, je založena na samotném dotazu. Proto pokud přidáte nový sloupec do dotazu nebo spojení, tato data `ViewModel`se dynamicky přidá do vrácené .

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

Důležitým bodem je, že pomocí dynamického typu vrácené kolekce dat je dynamicky sestavenjako ViewModel.

**Klady:** Tento přístup snižuje potřebu upravit statické ViewModel třídy při každé aktualizaci věty SQL dotazu, takže tento návrh přístup docela agilní při kódování, jednoduché a rychle vyvíjet s ohledem na budoucí změny.

**Nevýhody:** Z dlouhodobého hlediska dynamické typy mohou negativně ovlivnit srozumitelnost a kompatibilitu služby s klientskými aplikacemi. Kromě toho middleware software jako Swashbuckle nemůže poskytnout stejnou úroveň dokumentace na vrácené typy, pokud používáte dynamické typy.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako předdefinované třídy DTO

**Klady**: S statické předdefinované ViewModel třídy, jako je "smlouvy" na základě explicitní DTO třídy, je rozhodně lepší pro veřejná api, ale také pro dlouhodobé mikroslužeb, i v případě, že jsou používány pouze stejnou aplikací.

Pokud chcete zadat typy odpovědí pro Swagger, musíte použít explicitní Třídy DTO jako návratový typ. Proto předdefinované třídy DTO umožňují nabízet bohatší informace od Swagger. To zlepšuje dokumentaci rozhraní API a kompatibilitu při využívání rozhraní API.

**Nevýhody**: Jak již bylo zmíněno dříve, při aktualizaci kódu trvá některé další kroky k aktualizaci tříd DTO.

*Tip na základě našich zkušeností*: V dotazech implementovaných v objednávání mikroslužby v eShopOnContainers jsme začali vyvíjet pomocí dynamické ViewModels, protože to bylo velmi jednoduché a agilní v raných fázích vývoje. Ale jakmile vývoj byl stabilizován, jsme se rozhodli refaktorovat api a použití statické nebo předdefinované DTO pro ViewModels, protože je jasnější pro spotřebitele mikroslužeb znát explicitní typy DTO, který se používá jako "smlouvy".

V následujícím příkladu můžete vidět, jak dotaz vrací data pomocí explicitní třídy ViewModel DTO: OrderSummary třídy.

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

#### <a name="describe-response-types-of-web-apis"></a>Popište typy odpovědí webových api

Vývojáři, kteří spotřebovávají webová rozhraní API a mikroslužeb, se nejvíce zabývají tím, co je vráceno – konkrétně typy odpovědí a kódy chyb (pokud ne standardní). Ty jsou zpracovány v komentářích XML a datových poznámkách.

Bez řádné dokumentace v ui Swagger, spotřebitel postrádá znalosti o tom, jaké typy jsou vráceny nebo jaké kódy HTTP mohou být vráceny. Tento problém je vyřešen <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType>přidáním , takže Swashbuckle může generovat bohatší informace o návratovém modelu rozhraní API a hodnotách, jak je znázorněno v následujícím kódu:

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

`ProducesResponseType` Atribut však nelze použít dynamic jako typ, ale vyžaduje `OrderSummary` použití explicitní typy, jako je ViewModel DTO, je uvedeno v následujícím příkladu:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

To je další důvod, proč explicitní vrácené typy jsou lepší než dynamické typy, v dlouhodobém horizontu. Při použití `ProducesResponseType` atributu můžete také určit, jaký je očekávaný výsledek, pokud jde o možné chyby/kódy HTTP, jako je 200, 400 atd.

Na následujícím obrázku můžete vidět, jak swagger uI zobrazuje responsetype informace.

![Snímek obrazovky se stránkou s rozhraním Swagger pro rozhraní API pro objednávání](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Obrázek 7-5**. Uživatelské rozhraní Swagger zobrazující typy odpovědí a možné kódy stavu HTTP z webového rozhraní API

Na obrázku nad některé ukázkové hodnoty založené na typech ViewModel a možných stavových kódech HTTP, které lze vrátit, můžete zobrazit na obrázku výše.

## <a name="additional-resources"></a>Další zdroje

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lermanová. Datové body - Dapper, Entity Framework a hybridní aplikace (článek časopisu MSDN)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **Stránky nápovědy k webovému rozhraní API technologie ASP.NET Core využívající Swagger**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Předchozí](eshoponcontainers-cqrs-ddd-microservice.md)
>[další](ddd-oriented-microservice.md)
