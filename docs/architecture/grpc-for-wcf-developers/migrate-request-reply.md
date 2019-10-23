---
title: Migrace služby Request-Reply WCF do gRPC-gRPC pro vývojáře WCF
description: Naučte se migrovat jednoduchou službu Request-Reply z WCF na gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: 183e3b0ab1ce5c63714ced064f0d0901f59819c7
ms.sourcegitcommit: 559259da2738a7b33a46c0130e51d336091c2097
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 10/22/2019
ms.locfileid: "72770403"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>Migrace služby požadavek-odpověď WCF na gRPC unární RPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V této části se dozvíte, jak migrovat základní službu Request-Reply ve službě WCF do unární služby RPC v ASP.NET Core gRPC. Tyto služby jsou nejjednodušší typy služeb v Windows Communication Foundation (WCF) i v gRPC, takže je to vynikající místo, kde začít. Po migraci služby se dozvíte, jak vygenerovat klientskou knihovnu ze stejného `.proto` souboru pro využívání služby z klientské aplikace .NET.

## <a name="the-wcf-solution"></a>Řešení WCF

[Řešení PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) zahrnuje jednoduchou službu portfolio požadavek-odpověď pro stažení jednoho portfolia nebo všechny portfolia pro daného dodavatele. Služba je definována v `IPortfolioService` rozhraní s atributem `ServiceContract`:

```csharp
[ServiceContract]
public interface IPortfolioService
{
    [OperationContract]
    Task<Portfolio> Get(Guid traderId, int portfolioId);

    [OperationContract]
    Task<List<Portfolio>> GetAll(Guid traderId);
}
```

@No__t_0 model je jednoduchá C# třída označená pomocí [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), včetně seznamu objektů `PortfolioItem`. Tyto modely jsou definovány v projektu `TraderSys.PortfolioData` společně s třídou úložiště, která představuje abstrakci přístupu k datům.

```csharp
[DataContract]
public class Portfolio
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public Guid TraderId { get; set; }

    [DataMember]
    public List<PortfolioItem> Items { get; set; }
}

[DataContract]
public class PortfolioItem
{
    [DataMember]
    public int Id { get; set; }

    [DataMember]
    public int ShareId { get; set; }

    [DataMember]
    public int Holding { get; set; }

    [DataMember]
    public decimal Cost { get; set; }
}
```

Implementace `ServiceContract` používá třídu úložiště poskytnutou prostřednictvím injektáže, který vrací instance `DataContract`ch typů.

```csharp
public class PortfolioService : IPortfolioService
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }

    public async Task<Portfolio> Get(Guid traderId, int portfolioId)
    {
        return await _repository.GetAsync(traderId, portfolioId);
    }

    public async Task<List<Portfolio>> GetAll(Guid traderId)
    {
        return await _repository.GetAllAsync(traderId);
    }
}
```

## <a name="the-portfoliosproto-file"></a>Portfolio. soubor.

Pokud jste postupovali podle pokynů v předchozí části, měli byste mít projekt gRPC s `portfolios.proto` souborem, který vypadá nějak takto.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

Prvním krokem je migrace tříd `DataContract` na jejich ekvivalenty Protobuf.

## <a name="convert-the-datacontracts-to-grpc-messages"></a>Převod kontraktů DataContract na zprávy gRPC

Třída `PortfolioItem` bude nejprve převedena na zprávu Protobuf, protože na ní závisí `Portfolio` třída. Třída je velmi jednoduchá a tři vlastnosti jsou mapovány přímo na gRPC datové typy. Vlastnost `Cost` představující cenu vyplácenou za akcie při nákupu, je `decimal` pole a gRPC podporuje pouze `float` nebo `double` pro reálné hodnoty, které nejsou vhodné pro měnu. Vzhledem k tomu, že se ceny za sdílení liší v rozmezí minimálně 1 centu, je možné náklady vyjádřit jako `int32` z centů.

> [!NOTE]
> Nezapomeňte použít `camelCase` pro názvy polí v souboru `.proto`; generátor C# kódu je převede na `PascalCase` za vás a uživatelé dalších jazyků budou děkují za dodržování různých standardů kódování.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

Třída `Portfolio` je trochu složitější. V kódu WCF vývojář použil `Guid` pro vlastnost `TraderId` a obsahuje `List<PortfolioItem>`. V Protobuf, který nemá `UUID` typ první třídy, byste měli použít `string` pro pole `traderId` a analyzovat ho ve vlastním kódu. Pro seznam položek použijte klíčové slovo `repeated` v poli.

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

Teď máme naši datovou zprávu, abychom mohli deklarovat koncové body RPC služby.

## <a name="convert-the-servicecontract-to-a-grpc-service"></a>Převést třídu ServiceContract na službu gRPC

Metoda `Get` WCF používá dva parametry: `Guid traderId` a `int portfolioId`. metody služby gRPC mohou převzít pouze jeden parametr, takže je nutné vytvořit zprávu pro uložení dvou hodnot. Běžným postupem je pojmenování těchto objektů požadavků stejným názvem jako metoda a přípona `Request`. @No__t_0 se znovu používá pro pole `traderId` namísto `Guid`.

Služba může pouze vrátit `Portfolio` zprávu přímo, ale to může mít dopad na zpětnou kompatibilitu v budoucnu. Je vhodné definovat samostatné `Request` a `Response` zprávy pro každou metodu ve službě, a to i v případě, že je mnoho z nich stejné, a to v případě, že se jedná o `GetResponse` zprávu s jediným `Portfolio` polem.

Následující příklad ukazuje deklaraci metody služby gRPC pomocí zprávy `GetRequest`:

```protobuf
message GetRequest {
    string trader_id = 1;
    int32 portfolio_id = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

Metoda `GetAll` WCF přijímá pouze jeden parametr, `traderId`, takže se může zdát, že jako typ parametru lze zadat `string`, ale gRPC vyžaduje definovaný typ zprávy. Tento požadavek pomáhá vyhodnotit postup použití vlastních zpráv pro všechny vstupy a výstupy, a to z důvodu zpětné kompatibility v budoucnu.

Metoda WCF vrátila také `List<Portfolio>`, ale ze stejného důvodu nepovoluje jednoduché typy parametrů, gRPC nepovoluje `repeated Portfolio` jako návratový typ. Místo toho vytvořte `GetAllResponse` typ pro zabalení seznamu.

> [!WARNING]
> Můžete se rozhodnout vytvořit zprávu `PortfolioList` nebo podobnou a použít ji napříč různými metodami služby, ale tuto pokušení byste měli odolat. Není možné zjistit, jak se různé metody v rámci služby můžou v budoucnu vyvíjet, takže jejich zprávy jsou specifické a čistě oddělené.

```protobuf
message GetAllRequest {
    string trader_id = 1;
}

message PortfolioList {
    repeated Portfolio portfolios = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (Portfolio);
    rpc GetAll(GetAllRequest) returns (GetAllResponse);
}
```

Pokud uložíte projekt s těmito změnami, cíl sestavení gRPC se spustí na pozadí a vygeneruje všechny typy zpráv Protobuf a základní třídu, kterou můžete zdědit k implementaci služby.

Otevřete třídu `Services/GreeterService.cs` a odstraňte ukázkový kód. Nyní můžete přidat implementaci služby portfolio. Vygenerovaná základní třída bude v oboru názvů `Protos` a je vygenerována jako vnořená třída. gRPC vytvoří statickou třídu se stejným názvem jako služba v souboru `.proto` a pak základní třídu s příponou `Base` uvnitř této statické třídy, takže úplný identifikátor základního typu je `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

Základní třída deklaruje `virtual` metody pro `Get` a `GetAll`, které lze přepsat pro implementaci služby. Metody jsou `virtual` spíše než `abstract`, takže pokud je neimplementujete, může služba vrátit explicitní stavový kód gRPC `Unimplemented`, podobně jako můžete vyvolat `NotImplementedException` v běžném C# kódu.

Signatura všech gRPC unárních metod služby v ASP.NET Core je konzistentní. Existují dva parametry: první je typ zprávy deklarovaný v souboru `.proto` a druhý je `ServerCallContext`, který funguje podobně jako `HttpContext` od ASP.NET Core. Ve skutečnosti existuje metoda rozšíření s názvem `GetHttpContext` ve třídě `ServerCallContext`, kterou můžete použít k získání základní `HttpContext`, i když byste ji neměli potřebovat často použít. Podíváme se na `ServerCallContext` později v této kapitole a také v kapitole, která se zabývá ověřováním.

Návratový typ metody je `Task<T>`, kde `T` je typ zprávy odpovědi. Všechny metody služby gRPC jsou asynchronní.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>Migrace knihovny PortfolioData do .NET Core

V tomto okamžiku projekt potřebuje úložiště portfolia a modely obsažené v knihovně tříd `TraderSys.PortfolioData` v řešení WCF. Nejjednodušší způsob, jak je přenést do více instancí, je vytvořit novou knihovnu tříd pomocí dialogového okna **Nový projekt** aplikace Visual Studio se šablonou *knihovny tříd (.NET Standard)* , nebo z příkazového řádku pomocí .NET Core CLI spustit následující příkazy z adresáře, který obsahuje soubor `TraderSys.sln`.

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

Jakmile je knihovna vytvořena a přidána do řešení, odstraňte vygenerovaný `Class1.cs` soubor a zkopírujte soubory z knihovny řešení WCF do složky nové knihovny tříd, čímž zachováte strukturu složek.

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

Projekty .NET ve stylu sady SDK automaticky zahrnují všechny `.cs` soubory do jejich vlastního adresáře, takže není nutné je explicitně přidávat do projektu. Jediným krokem je odebrání atributů `DataContract` a `DataMember` z tříd `Portfolio` a `PortfolioItem`, aby byly prostými starými C# třídami.

```csharp
public class Portfolio
{
    public int Id { get; set; }
    public Guid TraderId { get; set; }
    public List<PortfolioItem> Items { get; set; }
}

public class PortfolioItem
{
    public int Id { get; set; }
    public int ShareId { get; set; }
    public int Holding { get; set; }
    public decimal Cost { get; set; }
}
```

## <a name="use-aspnet-core-dependency-injection"></a>Použít vkládání závislostí ASP.NET Core

Nyní můžete přidat odkaz na tuto knihovnu do projektu aplikace gRPC a spotřebovat třídu `PortfolioRepository` pomocí injektáže závislosti v implementaci služby gRPC. V aplikaci WCF bylo vkládání závislostí zajištěno kontejnerem Autofac IoC. ASP.NET Core má v nástroji vloženýmiy pro vkládání závislostí. úložiště lze zaregistrovat v metodě `ConfigureServices` `Startup` třídy.

```csharp
public class Startup
{
    public void ConfigureServices(IServiceCollection services)
    {
        // Register the repository class as a scoped service (instance per request)
        services.AddScoped<IPortfolioRepository, PortfolioRepository>();

        services.AddGrpc();
    }

    // ...
}
```

Implementaci `IPortfolioRepository` lze nyní zadat jako parametr konstruktoru ve třídě `PortfolioService`, jak je znázorněno níže:

```csharp
public class PortfolioService : Protos.Portfolios.PortfoliosBase
{
    private readonly IPortfolioRepository _repository;

    public PortfolioService(IPortfolioRepository repository)
    {
        _repository = repository;
    }
}
```

## <a name="implement-the-grpc-service"></a>Implementace služby gRPC

Nyní, když jste deklarovali vaše zprávy a službu v souboru `portfolios.proto`, je nutné implementovat metody služby ve třídě `PortfolioService`, která dědí z třídy `Portfolios.PortfoliosBase` generované v gRPC. Metody jsou deklarovány jako `virtual` v základní třídě. Pokud je nepřepíšete, budou ve výchozím nastavení vráceny stavový kód "neimplementováno" gRPC.

Začněte implementací metody `Get`. Výchozí přepsání vypadá jako v následujícím příkladu:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

Prvním problémem je, že `request.TraderId` je řetězec a služba vyžaduje `Guid`. I když je očekávaný formát pro řetězec `UUID`, kód musí zabývat se možností, že volající odeslal neplatnou hodnotu a správně reagovat. Služba může s chybami reagovat vyvoláním `RpcException` a pomocí standardního stavového kódu `InvalidArgument` tento problém vyjádřit.

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    return base.Get(request, context);
}
```

Jakmile bude k dispozici správná `Guid` hodnota `traderId`, úložiště se dá použít k načtení portfolia a vrácení do klienta.

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>Mapování interních modelů na zprávy gRPC

Předchozí kód ve skutečnosti nefunguje, protože úložiště vrací svůj vlastní POCO model `Portfolio`, ale *gRPC potřebuje vlastní* zprávu Protobuf `Portfolio`. Podobně jako mapování Entity Framework typů na typy přenosů dat, nejlepším řešením je poskytnout převod mezi těmito dvěma. Vhodným místem pro vložení kódu je do třídy generované Protobuf, která je deklarována jako třída `partial`, aby ji bylo možné rozšířit.

```csharp
namespace TraderSys.Portfolios.Protos
{
    public partial class PortfolioItem
    {
        public static PortfolioItem FromRepositoryModel(PortfolioData.Models.PortfolioItem source)
        {
            if (source is null) return null;

            return new PortfolioItem
            {
                Id = source.Id,
                ShareId = source.ShareId,
                Holding = source.Holding,
                CostCents = (int)(source.Cost * 100)
            };
        }
    }

    public partial class Portfolio
    {
        public static Portfolio FromRepositoryModel(PortfolioData.Models.Portfolio source)
        {
            if (source is null) return null;

            var target = new Portfolio
            {
                Id = source.Id,
                TraderId = source.TraderId.ToString(),
            };

            target.Items.AddRange(source.Items.Select(PortfolioItem.FromRepositoryModel));

            return target;
        }
    }
}
```

> [!NOTE]
> Můžete použít knihovnu, jako je například [automapper](https://automapper.org/) , pro zpracování tohoto převodu z interních tříd modelu na Protobuf typy, pokud nakonfigurujete převody typu nižší úrovně jako `string` / `Guid` nebo `decimal` / `double` a mapování seznamu.

S kódem převodu na místě může být implementace metody `Get` dokončena.

```csharp
public override async Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolio = await _repository.GetAsync(traderId, request.PortfolioId);

    return new GetResponse
    {
        Portfolio = Portfolio.FromRepositoryModel(portfolio)
    };
}

```

Implementace metody `GetAll` je podobná. Všimněte si, že pole `repeated` ve zprávách Protobuf jsou generována jako `readonly` vlastností typu `RepeatedField<T>`, takže je nutné do nich přidat položky pomocí metody `AddRange`, jako v následujícím příkladu:

```csharp
public override async Task<GetAllResponse> GetAll(GetAllRequest request, ServerCallContext context)
{
    if (!Guid.TryParse(request.TraderId, out var traderId))
    {
        throw new RpcException(new Status(StatusCode.InvalidArgument, "traderId must be a UUID"));
    }

    var portfolios = await _repository.GetAllAsync(traderId);

    var response = new GetAllResponse();
    response.Portfolios.AddRange(portfolios.Select(Portfolio.FromRepositoryModel));

    return response;
}
```

Po úspěšné migraci služby Request-Reply WCF do gRPC se podívejme na vytvoření klienta z `.proto`ho souboru.

## <a name="generate-client-code"></a>Vygenerovat kód klienta

Vytvořte .NET Standard knihovnu tříd ve stejném řešení, aby obsahovala klienta. Toto je primárně příklad vytváření kódu klienta, ale můžete ho zabalit pomocí NuGet a distribuovat ho do interního úložiště, aby se daly využívat jiné týmy .NET. Pokračujte a přidejte do řešení novou knihovnu tříd .NET Standard nazvanou `TraderSys.Portfolios.Client` a odstraňte soubor `Class1.cs`.

> [!CAUTION]
> Balíček NuGet pro [Grpc .NET. Client](https://www.nuget.org/packages/Grpc.Net.Client) vyžaduje rozhraní .net Core 3,0 (nebo jiný modul runtime kompatibilní s .NET Standard 2,1). Předchozí verze .NET Framework a .NET Core jsou podporovány balíčkem NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core) .

V aplikaci Visual Studio 2019 můžete přidat odkazy na gRPC Services podobně jako při přidávání odkazů na služby do projektů WCF v dřívějších verzích sady Visual Studio. Odkazy na služby a připojené služby jsou všechny spravované ve stejném uživatelském rozhraní, ke kterému máte přístup kliknutím pravým tlačítkem myši na uzel **závislosti** v `TraderSys.Portfolios.Client` projektu v Průzkumník řešení a vybráním možnosti **Přidat připojenou službu**. V zobrazeném okně nástroje vyberte část odkazy na **služby** a klikněte na **Přidat nový odkaz na službu gRPC**.

![Uživatelské rozhraní připojené služby v aplikaci Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

Přejděte k souboru `portfolios.proto` v projektu `TraderSys.Portfolios`, ponechte **typ třídy generovaný** jako **klient**a klikněte na **OK**.

![Dialogové okno Přidat nový odkaz na službu gRPC v aplikaci Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Všimněte si, že toto dialogové okno také poskytuje pole Adresa URL. Pokud vaše organizace udržuje adresář `.proto`ch souborů, který je přístupný pro web, můžete vytvořit klienty pouze nastavením této adresy URL.

Při použití funkce **Přidat připojenou službu** sady Visual Studio je soubor `portfolios.proto` přidán do projektu knihovny tříd jako *propojený soubor*namísto zkopírování, takže změny souboru v projektu služby budou automaticky použity v klientovi. projektem. Element `<Protobuf>` v souboru `csproj` vypadá takto:

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> Pokud nepoužíváte aplikaci Visual Studio nebo dáváte přednost práci z příkazového řádku, můžete použít globální nástroj **dotnet-grpc** pro správu odkazů Protobuf v rámci projektu .NET grpc. [Další informace najdete v dokumentaci **dotnet-grpc** ](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).

### <a name="use-the-portfolios-service-from-a-client-application"></a>Použití služby portfolio z klientské aplikace

Následující kód představuje stručný příklad použití vygenerovaného klienta v konzolové aplikaci. Podrobnější zkoumání kódu klienta gRPC je na konci této kapitoly.

```csharp
public class Program
{
    public async Task Main(string[] args)
    {
        GetResponse response;

        using (var channel = GrpcChannel.ForAddress("https://localhost:5001"))
        {
            var client = new Protos.Portfolios.PortfoliosClient(channel);

            response = await client.GetAsync(new GetRequest
            {
                TraderId = args[0],
                PortfolioId = int.Parse(args[1])
            });
        }

        foreach (var item in response.Portfolio.Items)
        {
            Console.WriteLine($"Holding {item.Holding} of Share ID {item.ShareId}.");
        }
    }
}
```

Nyní jste migrovali základní aplikaci WCF do ASP.NET Core služby gRPC a vytvořili klienta pro využívání služby z aplikace .NET. V další části jsou pokryty "duplexní" služby.

>[!div class="step-by-step"]
>[Předchozí](create-project.md)
>[Další](migrate-duplex-services.md)
