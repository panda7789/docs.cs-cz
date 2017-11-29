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
# <a name="implementing-readsqueries-in-a-cqrs-microservice"></a>Implementace čtení či dotazy v CQRS mikroslužbu

Řazení mikroslužbu z aplikace eShopOnContainers odkaz pro čtení nebo dotazy, implementuje dotazy nezávisle DDD modelu a transakční oblasti. K tomu bylo potřeba především, protože požadavky pro dotazy a transakce se výrazně liší. Zápisy provedení transakcí, které musí být v souladu s logiku domény. Dotazy, na druhé straně jsou idempotent a může být oddělené od domény pravidel.

Přístup je jednoduchý, jak je znázorněno v obrázek 9-3. Rozhraní API je implementováno modulem řadiče webového rozhraní API pomocí jakékoliv infrastruktury (třeba micro ORM jako Dapper) a vrácení dynamické ViewModels podle potřeb uživatelského rozhraní aplikace.

![](./media/image3.png)

**Obrázek 9-3**. Nejjednodušším přístupem pro dotazy v CQRS mikroslužbu

Toto je nejjednodušší možný přístup pro dotazy. Definice dotazu dotaz na databázi a vrátit dynamické ViewModel vytvořené za chodu při každém dotazu. Vzhledem k tomu, že dotazy jsou idempotent, že nedojde ke změně dat bez ohledu na to, kolikrát spuštění dotazu. Proto není potřeba být omezena žádnému DDD vzoru používá na straně transakcí, jako agregace a dalšími vzory, a proto dotazy, jsou odděleni od oblasti transakcí. Jednoduše dotaz na databázi pro data, která je uživatelské rozhraní a vrátit dynamické ViewModel, který nemusí být staticky definovanými v odkudkoli (žádné třídy pro ViewModels) s výjimkou v příkazech SQL, sami.

Vzhledem k tomu, že toto je jednoduchá přístup, vyžaduje se kód pro dotazy na straně (například kódu pomocí micro, jako jsou ORM [Dapper](https://github.com/StackExchange/Dapper)) může být implementováno [v rámci stejné projekt webového rozhraní API](https://github.com/dotnet-architecture/eShopOnContainers/blob/master/src/Services/Ordering/Ordering.API/Application/Queries/OrderQueries.cs). Na obrázku 9 – 4 je to. Dotazy jsou definovány v **Ordering.API** mikroslužbu projektu v eShopOnContainers řešení.

![](./media/image4.png)

**Obrázek 9 – 4**. Dotazy v mikroslužbu řazení v eShopOnContainers

## <a name="using-viewmodels-specifically-made-for-client-apps-independent-from-domain-model-constraints"></a>Pomocí ViewModels konkrétně vytvořené pro klientské aplikace, nezávislé na omezení domény modelu.

Vzhledem k tomu, že dotazy jsou provedena za účelem získání dat potřebných v klientských aplikacích, typ vrácený konkrétně lze pro klienty, na základě dat vrácených dotazy. Tyto modely nebo objekty přenos dat (DTOs), se nazývají ViewModels.

Vrácená data (ViewModel) může být výsledkem spojování dat z více entit nebo tabulky v databázi, nebo dokonce i v jiných více agregace definované v modelu domény oblasti transakcí. V takovém případě vzhledem k tomu, že při vytváření dotazů nezávislé na modelu domény, agregace hranice a omezení jsou zcela ignorovány a můžete všechny tabulky a sloupce, který může být nutné dotazů. Tento přístup poskytuje flexibilitu a produktivitu pro vývojáře vytváření nebo aktualizaci dotazy.

ViewModels může být statické typy definované v třídy. Nebo je lze vytvořit dynamicky na základě dotazů provést (jak je implementované v řazení mikroslužbu), což je velmi agilní pro vývojáře.

## <a name="using-dapper-as-a-micro-orm-to-perform-queries"></a>Použití Dapper jako malých ORM provádět dotazy 

Pro zadávání dotazů můžete použít všechny malých ORM, Entity Framework Core nebo i prostý ADO.NET. V ukázkové aplikace jsme vybrali Dapper pro řazení mikroslužbu v eShopOnContainers jako dobrým příkladem oblíbených malých ORM. Může probíhat prostý dotazy SQL s vysoký výkon, protože je velmi malé rozhraní. Pomocí Dapper, můžete napsat dotaz SQL, který můžete používat a připojení k několika tabulkám.

Dapper je opensourcový projekt (původně vytvořil šafrán Sam) a je součástí stavební bloky v [Stack Overflow](https://stackoverflow.com/). Pokud chcete používat Dapper, stačí nainstalovat přes [balíček Dapper NuGet](https://www.nuget.org/packages/Dapper), jak je znázorněno na následujícím obrázku.

![](./media/image5.png)

Budete také muset přidat, pomocí příkazu tak kódu má přístup k Dapper rozšiřující metody.

Pokud používáte Dapper ve vašem kódu, použijete přímo k dispozici v oboru názvů System.Data.SqlClient SqlClient třídu. Prostřednictvím metody QueryAsync a jiné metody rozšíření, které rozšiřují třídu SqlClient můžete jednoduše spouštět dotazy přehledné a původce způsobem.

## <a name="dynamic-and-static-viewmodels"></a>Dynamických a statických ViewModels

Jak je znázorněno v následujícím kódu z řazení mikroslužbu, většina ViewModels vrácený dotazy jsou implementované jako *dynamické*. To znamená, že do něj podmnožinu atributy, které mají být vráceny je založen na samotný dotaz. Pokud přidáte nový sloupec dotazu nebo spojení, tato data dynamicky přidány do vrácený ViewModel. Tento přístup snižuje nutnost úpravě dotazů v reakci na aktualizace základní datový model, provedení tohoto návrhu přístupu flexibilnější a toleranci vůči budoucí změny.

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

Důležité je, že pomocí dynamické typ vrácený shromažďování dat bude dynamicky sestavit jako ViewModel.

Pro většinu dotazů není potřeba předdefinovat třídě DTO nebo ViewModel, který převede na kódování je snadný a produktivitu. Pokud chcete mít ViewModels s definicí omezenější jako kontrakty, ale můžete předdefinovat ViewModels (jako jsou předdefinované DTOs).

#### <a name="additional-resources"></a>Další zdroje

-   **Dapper**
    [*https://github.com/StackExchange/dapper-dot-net*](https://github.com/StackExchange/dapper-dot-net)

-   **Julie Lerman. Datové body - Dapper, rozhraní Entity Framework a hybridní aplikace (článek MSDN Mag.)**

    *https://msdn.microsoft.com/en-us/Magazine/mt703432.aspx*


>[!div class="step-by-step"]
[Předchozí] (eshoponcontainers-cqrs-ddd-microservice.md) [Další] (ddd-zaměřené na konkrétní microservice.md)
