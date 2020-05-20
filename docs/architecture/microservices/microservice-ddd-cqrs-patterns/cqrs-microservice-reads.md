---
title: Implementace čtení nebo dotazů v mikroslužbě CQRS
description: Architektura mikroslužeb .NET pro kontejnerové aplikace .NET | Pochopení implementace dotazů, které jsou součástí CQRS, na základě řazení mikroslužby v eShopOnContainers pomocí Dapperem.
ms.date: 10/08/2018
ms.openlocfilehash: 71db95e6fc17475693183be9c6854884cd331ce1
ms.sourcegitcommit: 27db07ffb26f76912feefba7b884313547410db5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/19/2020
ms.locfileid: "83614406"
---
# <a name="implement-readsqueries-in-a-cqrs-microservice"></a>Implementace čtení/dotazů v mikroslužbě CQRS

Pro čtení a dotazování mikroslužba řazení z referenční aplikace eShopOnContainers implementuje dotazy nezávisle na modelu DDD a transakční oblasti. To bylo provedeno hlavně proto, že požadavky na dotazy a pro transakce jsou drasticky odlišné. Zapisuje transakce Execute, které musí být kompatibilní s logikou domény. Na druhé straně jsou dotazy idempotentní a je možné je oddělit od pravidel domény.

Přístup je jednoduchý, jak je znázorněno na obrázku 7-3. Rozhraní API se implementuje řadiči webového rozhraní API pomocí libovolné infrastruktury, jako je například mikrorelační mapování (ORM), jako je Dapperem, a vrácení dynamické ViewModels v závislosti na potřebách aplikací uživatelského rozhraní.

![Diagram znázorňující dotazy na nejvyšší úrovni v zjednodušené CQRS.](./media/cqrs-microservice-reads/simple-approach-cqrs-queries.png)

**Obrázek 7-3**. Nejjednodušší přístup k dotazům v mikroslužbě CQRS

Nejjednodušší přístup k dotazům na straně zjednodušeného přístupu CQRS je možné implementovat dotazování databáze pomocí mikroorm, jako je Dapperem, a vrácení dynamického ViewModels. Definice dotazů dotazují databázi a vrátí pro každý dotaz dynamický ViewModel sestavený za běhu. Vzhledem k tomu, že jsou dotazy idempotentní, nemění data bez ohledu na to, kolikrát spustíte dotaz. Proto nemusíte být omezeny žádným vzorem DDD použitým v transakční straně, jako jsou agregace a jiné vzory, a proto jsou dotazy odděleny od transakční oblasti. Dotazujte databázi na data, která uživatelské rozhraní potřebuje, a vraťte dynamické ViewModel, které není nutné staticky definovat kdekoli (žádné třídy pro ViewModels), s výjimkou samotných příkazů SQL.

Vzhledem k tomu, že tento přístup je jednoduchý, kód požadovaný pro dotazy na straně (například kód pomocí mikroorm jako [dapperem](https://github.com/StackExchange/Dapper)) je možné implementovat [do stejného projektu webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Obrázek 7-4 ukazuje toto. Dotazy jsou definovány v projektu pro **objednávání. API** mikroslužeb v rámci řešení eShopOnContainers.

![Snímek složky dotazů v projektu řazení. API](./media/cqrs-microservice-reads/ordering-api-queries-folder.png)

**Obrázek 7-4**. Dotazy na mikroslužbu řazení v eShopOnContainers

## <a name="use-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Použijte ViewModels specificky pro klientské aplikace nezávisle na omezeních doménového modelu.

Vzhledem k tomu, že se dotazy provádějí pro získání dat potřebných klientskými aplikacemi, může být vrácený typ konkrétně vytvořen pro klienty na základě dat vrácených dotazy. Tyto modely, neboli Přenos dat objektů (DTO), se nazývají ViewModels.

Vrácená data (ViewModel) mohou být výsledkem propojení dat z více entit nebo tabulek v databázi, nebo dokonce napříč více agregovanými definicemi, které jsou definovány v doménovém modelu pro transakční oblast. V takovém případě, protože vytváříte dotazy nezávislé na doménovém modelu, budou hranice agregace a omezení ignorovány a vy budete moci dotazovat na libovolnou tabulku a sloupec, které možná budete potřebovat. Tento přístup poskytuje vývojářům pro vytváření a aktualizaci dotazů skvělou flexibilitu a produktivitu.

ViewModels mohou být statické typy definované v třídách. Nebo je lze vytvořit dynamicky na základě provedených dotazů (jak je implementováno v mikroslužbě řazení), což je pro vývojáře velmi agilní.

## <a name="use-dapper-as-a-micro-orm-to-perform-queries"></a>Použití Dapperem jako mikroorm k provádění dotazů

Pro dotazování můžete použít jakýkoli mikroorm, Entity Framework Core nebo i prostý ADO.NET. V ukázkové aplikaci byl jako dobrý příklad oblíbených mikroorm vybraný Dapperem pro řazení mikroslužeb v eShopOnContainers. Může spouštět prosté dotazy SQL se skvělým výkonem, protože se jedná o světelný rámec. Pomocí Dapperem můžete napsat dotaz SQL, který může přistupovat k několika tabulkám a připojovat se k nim.

Dapperem je open source projekt (originál vytvořený pomocí Sam Saffron) a je součástí stavebních bloků používaných v [Stack Overflow](https://stackoverflow.com/). Chcete-li použít Dapperem, stačí ji nainstalovat prostřednictvím [balíčku NuGet dapperem](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku:

![Snímek obrazovky s balíčkem Dapperem v zobrazení balíčků NuGet](./media/cqrs-microservice-reads/drapper-package-nuget.png)

Je také nutné přidat `using` direktivu, aby váš kód měl přístup k metodám rozšíření dapperem.

Při použití Dapperem v kódu přímo použijete <xref:System.Data.SqlClient.SqlConnection> třídu dostupnou v <xref:System.Data.SqlClient> oboru názvů. Prostřednictvím metody QueryAsync a dalších metod rozšíření, které tuto třídu rozšířily <xref:System.Data.SqlClient.SqlConnection> , můžete spouštět dotazy jednoduchým a vykonávajícím způsobem.

## <a name="dynamic-versus-static-viewmodels"></a>Dynamické versus statické ViewModels

Při vracení ViewModels z klientských aplikací na straně serveru můžete uvažovat o těchto ViewModels jako DTO (Přenos dat objekty), které se mohou lišit od interních entit domény modelu entity, protože ViewModels drží data způsobem, jakým aplikace potřebuje klientská aplikace. Proto můžete v mnoha případech agregovat data přicházející z více doménových entit a ViewModels vytvořit přesně podle toho, jak klientská aplikace potřebuje tato data.

Tyto ViewModels nebo DTO lze definovat explicitně (jako třídy pro držitele dat), jako je `OrderSummary` Třída zobrazená v pozdějším fragmentu kódu. Nebo můžete pouze vrátit dynamické ViewModels nebo dynamické Dtoy na základě atributů vrácených dotazy jako dynamického typu.

### <a name="viewmodel-as-dynamic-type"></a>ViewModel jako dynamický typ

Jak je znázorněno v následujícím kódu, `ViewModel` může být přímo vrácen pomocí dotazů pouhým vrácením *dynamického* typu, který interně vychází z atributů vrácených dotazem. To znamená, že podmnožina atributů, které mají být vráceny, je založena na samotném dotazu. Proto pokud přidáte do dotazu nebo JOIN nový sloupec, budou tato data dynamicky přidána do vráceného `ViewModel` .

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

Důležité je, že při použití dynamického typu je vrácená kolekce dat dynamicky sestavena jako ViewModel.

**Profesionály:** Tento přístup omezuje nutnost upravovat statické třídy ViewModel vždy, když aktualizujete větu SQL dotazu. Tento přístup k návrhu se zjednodušuje při kódování, snadném a rychlém vývoje v souvislosti s budoucími změnami.

**Nevýhody:** V dlouhodobém období můžou dynamické typy negativně ovlivnit přehlednost a kompatibilitu služby s klientskými aplikacemi. Kromě toho middlewarský software, jako je swashbuckle, nemůže poskytnout stejnou úroveň dokumentace k vráceným typům, pokud používáte dynamické typy.

### <a name="viewmodel-as-predefined-dto-classes"></a>ViewModel jako předdefinované třídy DTO

**Odborníci**: statické a předdefinované třídy ViewModel, jako je například kontrakty založené na explicitních třídách DTO, jsou jednoznačně vhodnější pro veřejná rozhraní API, ale také pro dlouhodobé mikroslužby, i když jsou používány pouze stejnou aplikací.

Pokud chcete určit typy odezvy pro Swagger, musíte jako návratový typ použít explicitní třídy DTO. Předdefinované třídy DTO proto umožňují nabízet bohatší informace z Swagger. Což vylepšuje dokumentaci rozhraní API a kompatibilitu při využívání rozhraní API.

**Nevýhody**: jak bylo zmíněno dříve, při aktualizaci kódu je potřeba provést několik dalších kroků, které aktualizují třídy DTO.

*Tip na základě našeho prostředí*: v dotazech implementovaných při řazení mikroslužeb v eShopOnContainers jsme začali vyvíjet pomocí dynamických ViewModels, protože byly jednoduché a agilní na fázích předčasného vývoje. Ale jakmile byl vývoj stabilizovaný, rozhodli jsme se refaktorovat rozhraní API a použít pro ViewModels statické nebo předem definované DTO, protože je jasný pro spotřebitele mikroslužeb, aby znali explicitní typy DTO, které se používají jako "kontrakty".

V následujícím příkladu můžete vidět, jak dotaz vrací data pomocí explicitní třídy ViewModel DTO: třídy OrderSummary.

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

#### <a name="describe-response-types-of-web-apis"></a>Popis typů odpovědí webových rozhraní API

Vývojáři, kteří využívají webová rozhraní API a mikroslužby, mají největší obavy s tím, co se vrátí – konkrétně typy a chybové kódy (Pokud není standard). Typy odpovědí jsou zpracovávány v komentářích XML a datových anotacích.

Bez správné dokumentace v uživatelském rozhraní Swagger nemá spotřebitel znalosti o tom, jaké typy jsou vraceny nebo jaké kódy HTTP je možné vrátit. Tento problém je vyřešen přidáním <xref:Microsoft.AspNetCore.Mvc.ProducesResponseTypeAttribute?displayProperty=nameWithType> , takže swashbuckle může generovat rozsáhlejší informace o návratovém modelu a hodnotách rozhraní API, jak je znázorněno v následujícím kódu:

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

`ProducesResponseType`Atribut však nemůže použít Dynamic jako typ, ale vyžaduje použití explicitních typů, jako je `OrderSummary` ViewModel DTO, jak je znázorněno v následujícím příkladu:

```csharp
public class OrderSummary
{
    public int ordernumber { get; set; }
    public DateTime date { get; set; }
    public string status { get; set; }
    public double total { get; set; }
}
```

To je další důvod, proč jsou explicitní vrácené typy lepší než dynamické typy v dlouhodobém horizontu. Při použití `ProducesResponseType` atributu můžete také určit, jaký je očekávaný výsledek v souvislosti s možnými chybami protokolu HTTP/kódy, například 200, 400 atd.

Na následujícím obrázku vidíte, jak uživatelské rozhraní Swagger zobrazuje ResponseType informace.

![Snímek obrazovky se stránkou uživatelského rozhraní Swagger pro rozhraní API řazení](./media/cqrs-microservice-reads/swagger-ordering-http-api.png)

**Obrázek 7-5**. Uživatelské rozhraní Swagger zobrazující typy odpovědí a možné stavové kódy HTTP z webového rozhraní API

Obrázek ukazuje několik ukázkových hodnot na základě typů ViewModel a možných stavových kódů HTTP, které mohou být vráceny.

## <a name="additional-resources"></a>Další zdroje

- **Dapper**  
 <https://github.com/StackExchange/dapper-dot-net>

- **Julie Lerman. Datové body – Dapperem, Entity Framework a hybridní aplikace (článek na webu MSDN Magazine)**  
  <https://docs.microsoft.com/archive/msdn-magazine/2016/may/data-points-dapper-entity-framework-and-hybrid-apps>

- **Stránky nápovědy k webovému rozhraní API technologie ASP.NET Core využívající Swagger**  
  <https://docs.microsoft.com/aspnet/core/tutorials/web-api-help-pages-using-swagger?tabs=visual-studio>

>[!div class="step-by-step"]
>[Předchozí](eshoponcontainers-cqrs-ddd-microservice.md) 
> [Další](ddd-oriented-microservice.md)
