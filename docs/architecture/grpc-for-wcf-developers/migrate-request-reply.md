---
title: Migrace služby Request-Reply WCF do gRPC-gRPC pro vývojáře WCF
description: Naučte se migrovat jednoduchou službu Request-Reply z WCF na gRPC.
author: markrendle
ms.date: 09/02/2019
ms.openlocfilehash: ac9eecf66a7ac37a1df9714e6383f7eaebae4781
ms.sourcegitcommit: 55f438d4d00a34b9aca9eedaac3f85590bb11565
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/23/2019
ms.locfileid: "71184307"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a>Migrace služby požadavek-odpověď WCF na gRPC unární RPC

[!INCLUDE [book-preview](../../../includes/book-preview.md)]

V této části se dozvíte, jak migrovat základní službu Request-Reply ve službě WCF do unární služby RPC v ASP.NET Core gRPC. Tyto služby jsou nejjednodušší typy služeb v Windows Communication Foundation (WCF) i v gRPC, takže je to vynikající místo, kde začít. Po migraci služby se dozvíte, jak vygenerovat klientskou knihovnu ze stejného `.proto` souboru, aby se služba mohla využívat z klientské aplikace .NET.

## <a name="the-wcf-solution"></a>Řešení WCF

[Řešení PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) zahrnuje jednoduchou službu portfolio požadavek-odpověď pro stažení jednoho portfolia nebo všechny portfolia pro daného dodavatele. Služba je definována v rozhraní `IPortfolioService` `ServiceContract` s atributem:

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

Model je jednoduchá C# třída označená pomocí [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), včetně seznamu `PortfolioItem` objektů. `Portfolio` Tyto modely jsou definovány v `TraderSys.PortfolioData` projektu společně s třídou úložiště, která představuje abstrakci přístupu k datům.

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

Implementace používá třídu úložiště poskytovanou prostřednictvím injektáže závislosti, který vrací instance `DataContract` typů. `ServiceContract`

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

Pokud jste postupovali podle pokynů v předchozí části, měli byste mít projekt gRPC se `portfolios.proto` souborem, který vypadá takto.

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

Prvním krokem je migrace `DataContract` tříd na jejich ekvivalenty Protobuf.

## <a name="convert-the-datacontracts-to-grpc-messages"></a>Převod kontraktů DataContract na zprávy gRPC

Třída bude nejprve převedena na zprávu Protobuf, `Portfolio` protože na ní závisí třída. `PortfolioItem` Třída je velmi jednoduchá a tři vlastnosti jsou mapovány přímo na gRPC datové typy. Vlastnost, která představuje cenu vyplácenou za akcie při nákupu, `decimal` je pole `double` a gRPC podporuje `float` pouze reálné hodnoty, které nejsou vhodné pro měnu. `Cost` Vzhledem k tomu, že se ceny za sdílení liší minimálně v jednom centu, náklady mohou `int32` být vyjádřeny jako v centech.

> [!NOTE]
> Nezapomeňte použít `camelCase` pro názvy polí `.proto` v souboru; generátor C# kódu je `PascalCase` převede za vás a uživatelé dalších jazyků vám budou děkují, že budou respektovat různé standardy kódování.

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 shareId = 2;
    int32 holding = 3;
    int32 costCents = 4;
}
```

`Portfolio` Třída je trochu složitější. V kódu WCF vývojář použil `Guid` `TraderId` pro `List<PortfolioItem>`vlastnost vlastnost a obsahuje. V Protobuf, který nemá typ první třídy `UUID` , byste měli `string` použít pro `traderId` pole a analyzovat ho ve vlastním kódu. Pro seznam položek použijte `repeated` klíčové slovo v poli.

```protobuf
message Portfolio {
    int32 id = 1;
    string traderId = 2;
    repeated PortfolioItem items = 3;
}
```

Teď máme naši datovou zprávu, abychom mohli deklarovat koncové body RPC služby.

## <a name="convert-the-servicecontract-to-a-grpc-service"></a>Převést třídu ServiceContract na službu gRPC

Metoda WCF `Get` používá dva parametry: `Guid traderId` a `int portfolioId`. metody služby gRPC mohou převzít pouze jeden parametr, takže je nutné vytvořit zprávu pro uložení dvou hodnot. Běžným postupem je pojmenování těchto objektů požadavků stejným názvem jako metoda a přípona `Request`. Znovu se používá `traderId` pro pole místo `Guid`. `string`

Služba by mohla jednoduše vrátit `Portfolio` zprávu přímo, ale to může mít vliv na zpětnou kompatibilitu v budoucnu. `Request` Je vhodné definovat samostatné `Response` zprávy pro každou metodu ve službě, a to i v případě, že mnoho z nich je `GetResponse` nyní stejné, takže deklarujete zprávu s jedním `Portfolio` polem.

Následující příklad ukazuje deklaraci metody služby gRPC pomocí `GetRequest` zprávy:

```protobuf
message GetRequest {
    string traderId = 1;
    int32 portfolioId = 2;
}

message GetResponse {
    Portfolio portfolio = 1;
}

service Portfolios {
    rpc Get(GetRequest) returns (GetResponse);
}
```

Metoda WCF `GetAll` přijímá pouze jeden parametr, `traderId`a proto se může zdát, že jeden může být zadán `string` jako typ parametru, ale gRPC vyžaduje definovaný typ zprávy. Tento požadavek pomáhá vyhodnotit postup použití vlastních zpráv pro všechny vstupy a výstupy, a to z důvodu zpětné kompatibility v budoucnu.

Metoda WCF také vrátila `List<Portfolio>`, ale ze stejného důvodu nepovoluje jednoduché typy parametrů, gRPC nepovoluje `repeated Portfolio` jako návratový typ. Místo toho vytvořte `GetAllResponse` typ pro zabalení seznamu.

> [!WARNING]
> Můžete se rozhodnout, že vytvoříte `PortfolioList` zprávu nebo podobnou a použijete ji napříč různými metodami služby, ale tuto pokušení byste měli odolat. Není možné zjistit, jak se různé metody v rámci služby můžou v budoucnu vyvíjet, takže jejich zprávy jsou specifické a čistě oddělené.

```protobuf
message GetAllRequest {
    string traderId = 1;
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

`Services/GreeterService.cs` Otevřete třídu a odstraňte ukázkový kód. Nyní můžete přidat implementaci služby portfolio. Vygenerovaná základní třída bude v `Protos` oboru názvů a je vygenerována jako vnořená třída. gRPC vytvoří statickou třídu se stejným názvem, jako má služba v `.proto` souboru, a pak základní třídu s příponou `Base` uvnitř této statické třídy, takže úplný identifikátor základního typu je `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

Základní třída deklaruje `virtual` metody pro `Get` a `GetAll` , které lze přepsat pro implementaci služby. Metody `virtual` jsou spíše než `abstract` tak, že pokud je neimplementujete, může služba vrátit explicitní stavový `NotImplementedException` kód `Unimplemented` gRPC, podobně jako byste mohli vyvolat v běžném C# kódu.

Signatura všech gRPC unárních metod služby v ASP.NET Core je konzistentní. Existují dva parametry: první je typ zprávy deklarovaný v `.proto` souboru a druhý `ServerCallContext` je `HttpContext` , který funguje podobně jako z ASP.NET Core. Ve skutečnosti existuje metoda rozšíření, která je volána `GetHttpContext` `ServerCallContext` na třídu, kterou můžete použít k získání základní `HttpContext`třídy, i když byste ji neměli potřebovat často použít. Podíváme se na `ServerCallContext` Další informace v této kapitole a také v kapitole, která popisuje ověřování.

Návratový typ metody je `Task<T>` , kde `T` je typ zprávy odpovědi. Všechny metody služby gRPC jsou asynchronní.

## <a name="migrate-the-portfoliodata-library-to-net-core"></a>Migrace knihovny PortfolioData do .NET Core

V tomto okamžiku projekt potřebuje úložiště portfolia a modely obsažené v `TraderSys.PortfolioData` knihovně tříd v řešení WCF. Nejjednodušší způsob, jak je přenést do více instancí, je vytvořit novou knihovnu tříd pomocí dialogového okna **Nový projekt** aplikace Visual Studio se šablonou *knihovny tříd (.NET Standard)* , nebo z příkazového řádku pomocí .NET Core CLI spustit následující příkazy z adresáře, který obsahuje `TraderSys.sln` soubor.

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

Moderní soubory projektu .NET automaticky zahrnují všechny `.cs` soubory ve svém vlastním adresáři, takže není nutné je explicitně přidávat do projektu. `DataContract` Jediným krokem je odebrání atributů a `DataMember` z `Portfolio` tříd a `PortfolioItem` , aby byly prosté staré C# třídy.

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

Nyní můžete přidat odkaz na tuto knihovnu do projektu aplikace gRPC a spotřebovat `PortfolioRepository` třídu pomocí injektáže závislosti v implementaci služby gRPC. V aplikaci WCF bylo vkládání závislostí zajištěno kontejnerem Autofac IoC. ASP.NET Core má v nástroji vloženýmiy pro vkládání závislostí. úložiště lze zaregistrovat v `ConfigureServices` metodě `Startup` ve třídě.

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

Implementaci lze nyní určit jako parametr konstruktoru `PortfolioService` ve třídě následujícím způsobem: `IPortfolioRepository`

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

Nyní, když jste deklarovali zprávy a službu v `portfolios.proto` souboru, je nutné implementovat metody služby `PortfolioService` ve třídě, která dědí z třídy generované `Portfolios.PortfoliosBase` gRPC. Metody jsou deklarovány jako `virtual` v základní třídě. Pokud je nepřepíšete, budou ve výchozím nastavení vráceny stavový kód "neimplementováno" gRPC.

Začněte implementací `Get` metody. Výchozí přepsání vypadá jako v následujícím příkladu:

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

Prvním problémem je `request.TraderId` řetězec a služba `Guid`vyžaduje. I když je `UUID`očekávaný formát pro řetězec, kód musí zabývat s možností, že volající odeslal neplatnou hodnotu a odpovídajícím způsobem reagovat. Služba může reagovat s chybami vyvoláním `RpcException`a pomocí standardního `InvalidArgument` stavového kódu tento problém vyjádřit.

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

Po správné `Guid` hodnotě pro `traderId`je možné úložiště použít k načtení portfolia a k jeho vrácení klientovi.

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a>Mapování interních modelů na zprávy gRPC

Předchozí kód ve skutečnosti nefunguje, protože úložiště vrací svůj vlastní POCO model `Portfolio`, ale gRPC potřebuje vlastní zprávu `Portfolio`Protobuf. Podobně jako mapování Entity Framework typů na typy přenosů dat, nejlepším řešením je poskytnout převod mezi těmito dvěma. Vhodným místem pro vložení kódu je do třídy generované Protobuf, která je deklarována jako `partial` třída, takže ji lze rozšířit.

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
> Můžete použít knihovnu, jako je například [automapper](https://automapper.org/) , pro zpracování tohoto převodu z interních tříd modelu na typy Protobuf, pokud nakonfigurujete převody typu nižší úrovně jako `string` nebo `decimal` / `Guid` /amapováníseznamu. `double`

S kódem převodu na místě `Get` může být implementace metody dokončena.

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

Implementace `GetAll` metody je podobná. Všimněte si, `repeated` že pole ve zprávách Protobuf jsou generována jako `readonly` vlastnosti `RepeatedField<T>`typu, takže je `AddRange` nutné do nich přidat položky pomocí metody, jako v následujícím příkladu:

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

Po úspěšné migraci služby požadavek-odpověď WCF na gRPC se podívejme na vytvoření klienta ze `.proto` souboru.

## <a name="generate-client-code"></a>Vygenerovat kód klienta

Vytvořte .NET Standard knihovnu tříd ve stejném řešení, aby obsahovala klienta. Toto je primárně příklad vytváření kódu klienta, ale můžete ho zabalit pomocí NuGet a distribuovat ho do interního úložiště, aby se daly využívat jiné týmy .NET. Pokračujte a přidejte do řešení novou knihovnu tříd .NET Standard s `TraderSys.Portfolios.Client` názvem a `Class1.cs` odstraňte soubor.

> [!CAUTION]
> Balíček NuGet pro [Grpc .NET. Client](https://www.nuget.org/packages/Grpc.Net.Client) vyžaduje rozhraní .net Core 3,0 (nebo jiný modul runtime kompatibilní s .NET Standard 2,1). Předchozí verze .NET Framework a .NET Core jsou podporovány balíčkem NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core) .

V aplikaci Visual Studio 2019 můžete přidat odkazy na gRPC Services podobně jako při přidávání odkazů na služby do projektů WCF v dřívějších verzích sady Visual Studio. Odkazy na služby a připojené služby jsou teď spravované ve stejném uživatelském rozhraní, ke kterému máte přístup kliknutím pravým tlačítkem myši na uzel **závislosti** v `TraderSys.Portfolios.Client` projektu v Průzkumník řešení a výběrem možnosti **Přidat připojenou službu**. V zobrazeném okně nástroje vyberte část odkazy na **služby** a klikněte na **Přidat nový odkaz na službu gRPC**.

![Uživatelské rozhraní připojené služby v aplikaci Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

Přejděte k `portfolios.proto` souboru `TraderSys.Portfolios` v projektu, ponechte **typ třídy, který se má vygenerovat** jako **klient**, a klikněte na **OK**.

![Dialogové okno Přidat nový odkaz na službu gRPC v aplikaci Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> Všimněte si, že toto dialogové okno také poskytuje pole Adresa URL. Pokud vaše organizace udržuje adresář souborů, který je přístupný `.proto` pro web, můžete vytvořit klienty, a to tak, že nastavíte tuto adresu URL.

Při použití funkce `portfolios.proto` **Přidat připojenou službu** sady Visual Studio je soubor přidán do projektu knihovny tříd jako *propojený soubor*namísto zkopírování, takže změny souboru v projektu služby budou automaticky použity v klientský projekt. `<Protobuf>` Element`csproj` v souboru vypadá takto:

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

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
