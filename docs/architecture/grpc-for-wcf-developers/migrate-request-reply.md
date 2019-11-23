---
title: Migrace služby Request-Reply WCF do gRPC-gRPC pro vývojáře WCF
description: Naučte se migrovat jednoduchou službu Request-Reply z WCF na gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: f0b20e7b374438f90d83aebc6035a4e4dd94ae18
ms.sourcegitcommit: f348c84443380a1959294cdf12babcb804cfa987
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 11/12/2019
ms.locfileid: "73971789"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="09d3b-103">Migrace služby požadavek-odpověď WCF na gRPC unární RPC</span><span class="sxs-lookup"><span data-stu-id="09d3b-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="09d3b-104">V této části se dozvíte, jak migrovat základní službu Request-Reply ve službě WCF do unární služby RPC v ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="09d3b-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="09d3b-105">Tyto služby jsou nejjednodušší typy služeb v Windows Communication Foundation (WCF) i v gRPC, takže je to vynikající místo, kde začít.</span><span class="sxs-lookup"><span data-stu-id="09d3b-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="09d3b-106">Po migraci služby se dozvíte, jak vygenerovat klientskou knihovnu ze stejného `.proto` souboru pro využívání služby z klientské aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="09d3b-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="09d3b-107">Řešení WCF</span><span class="sxs-lookup"><span data-stu-id="09d3b-107">The WCF solution</span></span>

<span data-ttu-id="09d3b-108">[Řešení PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) zahrnuje jednoduchou službu portfolio požadavek-odpověď pro stažení jednoho portfolia nebo všechny portfolia pro daného dodavatele.</span><span class="sxs-lookup"><span data-stu-id="09d3b-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple Request-Reply Portfolio service to download a single portfolio, or all portfolios for a given Trader.</span></span> <span data-ttu-id="09d3b-109">Služba je definována v `IPortfolioService` rozhraní s atributem `ServiceContract`:</span><span class="sxs-lookup"><span data-stu-id="09d3b-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="09d3b-110">`Portfolio` model je jednoduchá C# třída označená pomocí [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), včetně seznamu objektů `PortfolioItem`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute), including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="09d3b-111">Tyto modely jsou definovány v projektu `TraderSys.PortfolioData` společně s třídou úložiště, která představuje abstrakci přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="09d3b-111">These models are defined in the `TraderSys.PortfolioData` project, along with a repository class representing a data access abstraction.</span></span>

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

<span data-ttu-id="09d3b-112">Implementace `ServiceContract` používá třídu úložiště poskytnutou prostřednictvím injektáže, který vrací instance `DataContract`ch typů.</span><span class="sxs-lookup"><span data-stu-id="09d3b-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types.</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="09d3b-113">Portfolio. soubor.</span><span class="sxs-lookup"><span data-stu-id="09d3b-113">The portfolios.proto file</span></span>

<span data-ttu-id="09d3b-114">Pokud jste postupovali podle pokynů v předchozí části, měli byste mít projekt gRPC s `portfolios.proto` souborem, který vypadá nějak takto.</span><span class="sxs-lookup"><span data-stu-id="09d3b-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this.</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="09d3b-115">Prvním krokem je migrace tříd `DataContract` na jejich ekvivalenty Protobuf.</span><span class="sxs-lookup"><span data-stu-id="09d3b-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontracts-to-grpc-messages"></a><span data-ttu-id="09d3b-116">Převod kontraktů DataContract na zprávy gRPC</span><span class="sxs-lookup"><span data-stu-id="09d3b-116">Convert the DataContracts to gRPC messages</span></span>

<span data-ttu-id="09d3b-117">Třída `PortfolioItem` bude nejprve převedena na zprávu Protobuf, protože na ní závisí `Portfolio` třída.</span><span class="sxs-lookup"><span data-stu-id="09d3b-117">The `PortfolioItem` class will be converted to a Protobuf message first, as the `Portfolio` class depends on it.</span></span> <span data-ttu-id="09d3b-118">Třída je velmi jednoduchá a tři vlastnosti jsou mapovány přímo na gRPC datové typy.</span><span class="sxs-lookup"><span data-stu-id="09d3b-118">The class is very simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="09d3b-119">Vlastnost `Cost` představující cenu vyplácenou za akcie při nákupu, je `decimal` pole a gRPC podporuje pouze `float` nebo `double` pro reálné hodnoty, které nejsou vhodné pro měnu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-119">The `Cost` property, representing the price paid for the shares at purchase, is a `decimal` field, and gRPC only supports `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="09d3b-120">Vzhledem k tomu, že se ceny za sdílení liší v rozmezí minimálně 1 centu, je možné náklady vyjádřit jako `int32` z centů.</span><span class="sxs-lookup"><span data-stu-id="09d3b-120">Since share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="09d3b-121">Nezapomeňte použít `camelCase` pro názvy polí v souboru `.proto`; generátor C# kódu je převede na `PascalCase` za vás a uživatelé dalších jazyků budou děkují za dodržování různých standardů kódování.</span><span class="sxs-lookup"><span data-stu-id="09d3b-121">Remember to use `camelCase` for field names in your `.proto` file; the C# code generator will convert them to `PascalCase` for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="09d3b-122">Třída `Portfolio` je trochu složitější.</span><span class="sxs-lookup"><span data-stu-id="09d3b-122">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="09d3b-123">V kódu WCF vývojář použil `Guid` pro vlastnost `TraderId` a obsahuje `List<PortfolioItem>`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-123">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="09d3b-124">V Protobuf, který nemá `UUID` typ první třídy, byste měli použít `string` pro pole `traderId` a analyzovat ho ve vlastním kódu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-124">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="09d3b-125">Pro seznam položek použijte klíčové slovo `repeated` v poli.</span><span class="sxs-lookup"><span data-stu-id="09d3b-125">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="09d3b-126">Teď máme naši datovou zprávu, abychom mohli deklarovat koncové body RPC služby.</span><span class="sxs-lookup"><span data-stu-id="09d3b-126">Now we have our data messages, we can declare the service RPC endpoints.</span></span>

## <a name="convert-the-servicecontract-to-a-grpc-service"></a><span data-ttu-id="09d3b-127">Převést třídu ServiceContract na službu gRPC</span><span class="sxs-lookup"><span data-stu-id="09d3b-127">Convert the ServiceContract to a gRPC service</span></span>

<span data-ttu-id="09d3b-128">Metoda `Get` WCF používá dva parametry: `Guid traderId` a `int portfolioId`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-128">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="09d3b-129">metody služby gRPC mohou převzít pouze jeden parametr, takže je nutné vytvořit zprávu pro uložení dvou hodnot.</span><span class="sxs-lookup"><span data-stu-id="09d3b-129">gRPC service methods can only take a single parameter, so a message must be created to hold the two values.</span></span> <span data-ttu-id="09d3b-130">Běžným postupem je pojmenování těchto objektů požadavků stejným názvem jako metoda a přípona `Request`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-130">It's common practice to name these request objects with the same name as the method and the suffix `Request`.</span></span> <span data-ttu-id="09d3b-131">`string` se znovu používá pro pole `traderId` namísto `Guid`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-131">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="09d3b-132">Služba může pouze vrátit `Portfolio` zprávu přímo, ale to může mít dopad na zpětnou kompatibilitu v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-132">The service could just return a `Portfolio` message directly, but again, this could impact backward compatibility in the future.</span></span> <span data-ttu-id="09d3b-133">Je vhodné definovat samostatné `Request` a `Response` zprávy pro každou metodu ve službě, a to i v případě, že je mnoho z nich stejné, a to v případě, že se jedná o `GetResponse` zprávu s jediným `Portfolio` polem.</span><span class="sxs-lookup"><span data-stu-id="09d3b-133">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now, so declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="09d3b-134">Následující příklad ukazuje deklaraci metody služby gRPC pomocí zprávy `GetRequest`:</span><span class="sxs-lookup"><span data-stu-id="09d3b-134">The following example shows the declaration of the gRPC service method using the `GetRequest` message:</span></span>

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

<span data-ttu-id="09d3b-135">Metoda `GetAll` WCF přijímá pouze jeden parametr, `traderId`, takže se může zdát, že jako typ parametru lze zadat `string`, ale gRPC vyžaduje definovaný typ zprávy.</span><span class="sxs-lookup"><span data-stu-id="09d3b-135">The WCF `GetAll` method only takes a single parameter, `traderId`, so it might seem that one could specify `string` as the parameter type, but gRPC requires a defined message type.</span></span> <span data-ttu-id="09d3b-136">Tento požadavek pomáhá vyhodnotit postup použití vlastních zpráv pro všechny vstupy a výstupy, a to z důvodu zpětné kompatibility v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-136">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="09d3b-137">Metoda WCF vrátila také `List<Portfolio>`, ale ze stejného důvodu nepovoluje jednoduché typy parametrů, gRPC nepovoluje `repeated Portfolio` jako návratový typ.</span><span class="sxs-lookup"><span data-stu-id="09d3b-137">The WCF method also returned a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="09d3b-138">Místo toho vytvořte `GetAllResponse` typ pro zabalení seznamu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-138">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="09d3b-139">Můžete se rozhodnout vytvořit zprávu `PortfolioList` nebo podobnou a použít ji napříč různými metodami služby, ale tuto pokušení byste měli odolat.</span><span class="sxs-lookup"><span data-stu-id="09d3b-139">You may be tempted to create a `PortfolioList` message or similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="09d3b-140">Není možné zjistit, jak se různé metody v rámci služby můžou v budoucnu vyvíjet, takže jejich zprávy jsou specifické a čistě oddělené.</span><span class="sxs-lookup"><span data-stu-id="09d3b-140">It's impossible to know how the various methods on a service may evolve in the future, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="09d3b-141">Pokud uložíte projekt s těmito změnami, cíl sestavení gRPC se spustí na pozadí a vygeneruje všechny typy zpráv Protobuf a základní třídu, kterou můžete zdědit k implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="09d3b-141">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class you can inherit to implement the service.</span></span>

<span data-ttu-id="09d3b-142">Otevřete třídu `Services/GreeterService.cs` a odstraňte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="09d3b-142">Open up the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="09d3b-143">Nyní můžete přidat implementaci služby portfolio.</span><span class="sxs-lookup"><span data-stu-id="09d3b-143">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="09d3b-144">Vygenerovaná základní třída bude v oboru názvů `Protos` a je vygenerována jako vnořená třída.</span><span class="sxs-lookup"><span data-stu-id="09d3b-144">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="09d3b-145">gRPC vytvoří statickou třídu se stejným názvem jako služba v souboru `.proto` a pak základní třídu s příponou `Base` uvnitř této statické třídy, takže úplný identifikátor základního typu je `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-145">gRPC creates a static class with the same name as the service in the `.proto` file, and then a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="09d3b-146">Základní třída deklaruje `virtual` metody pro `Get` a `GetAll`, které lze přepsat pro implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="09d3b-146">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="09d3b-147">Metody jsou `virtual` spíše než `abstract`, takže pokud je neimplementujete, může služba vrátit explicitní stavový kód gRPC `Unimplemented`, podobně jako můžete vyvolat `NotImplementedException` v běžném C# kódu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-147">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="09d3b-148">Signatura všech gRPC unárních metod služby v ASP.NET Core je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="09d3b-148">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="09d3b-149">Existují dva parametry: první je typ zprávy deklarovaný v souboru `.proto` a druhý je `ServerCallContext`, který funguje podobně jako `HttpContext` od ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="09d3b-149">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="09d3b-150">Ve skutečnosti existuje metoda rozšíření s názvem `GetHttpContext` ve třídě `ServerCallContext`, kterou můžete použít k získání základní `HttpContext`, i když byste ji neměli potřebovat často použít.</span><span class="sxs-lookup"><span data-stu-id="09d3b-150">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="09d3b-151">Podíváme se na `ServerCallContext` později v této kapitole a také v kapitole, která se zabývá ověřováním.</span><span class="sxs-lookup"><span data-stu-id="09d3b-151">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="09d3b-152">Návratový typ metody je `Task<T>`, kde `T` je typ zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="09d3b-152">The method's return type is a `Task<T>` where `T` is the response message type.</span></span> <span data-ttu-id="09d3b-153">Všechny metody služby gRPC jsou asynchronní.</span><span class="sxs-lookup"><span data-stu-id="09d3b-153">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="09d3b-154">Migrace knihovny PortfolioData do .NET Core</span><span class="sxs-lookup"><span data-stu-id="09d3b-154">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="09d3b-155">V tomto okamžiku projekt potřebuje úložiště portfolia a modely obsažené v knihovně tříd `TraderSys.PortfolioData` v řešení WCF.</span><span class="sxs-lookup"><span data-stu-id="09d3b-155">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="09d3b-156">Nejjednodušší způsob, jak je přenést do více instancí, je vytvořit novou knihovnu tříd pomocí dialogového okna **Nový projekt** aplikace Visual Studio se šablonou *knihovny tříd (.NET Standard)* , nebo z příkazového řádku pomocí .NET Core CLI spustit následující příkazy z adresáře, který obsahuje soubor `TraderSys.sln`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-156">The easiest way to bring them across is to create a new class library using either the Visual Studio **New project** dialog with the *Class Library (.NET Standard)* template, or from the command line using the .NET Core CLI, running the following commands from the directory containing the `TraderSys.sln` file.</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="09d3b-157">Jakmile je knihovna vytvořena a přidána do řešení, odstraňte vygenerovaný `Class1.cs` soubor a zkopírujte soubory z knihovny řešení WCF do složky nové knihovny tříd, čímž zachováte strukturu složek.</span><span class="sxs-lookup"><span data-stu-id="09d3b-157">Once the library has been created and added to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure.</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="09d3b-158">Projekty .NET ve stylu sady SDK automaticky zahrnují všechny `.cs` soubory do jejich vlastního adresáře, takže není nutné je explicitně přidávat do projektu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-158">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so there's no need to explicitly add them to the project.</span></span> <span data-ttu-id="09d3b-159">Jediným krokem je odebrání atributů `DataContract` a `DataMember` z tříd `Portfolio` a `PortfolioItem`, aby byly prostými starými C# třídami.</span><span class="sxs-lookup"><span data-stu-id="09d3b-159">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes.</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="09d3b-160">Použít vkládání závislostí ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="09d3b-160">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="09d3b-161">Nyní můžete přidat odkaz na tuto knihovnu do projektu aplikace gRPC a spotřebovat třídu `PortfolioRepository` pomocí injektáže závislosti v implementaci služby gRPC.</span><span class="sxs-lookup"><span data-stu-id="09d3b-161">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="09d3b-162">V aplikaci WCF bylo vkládání závislostí zajištěno kontejnerem Autofac IoC.</span><span class="sxs-lookup"><span data-stu-id="09d3b-162">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="09d3b-163">ASP.NET Core má v nástroji vloženýmiy pro vkládání závislostí. úložiště lze zaregistrovat v metodě `ConfigureServices` `Startup` třídy.</span><span class="sxs-lookup"><span data-stu-id="09d3b-163">ASP.NET Core has dependency injection baked in; the repository can be registered in the `ConfigureServices` method in the `Startup` class.</span></span>

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

<span data-ttu-id="09d3b-164">Implementaci `IPortfolioRepository` lze nyní zadat jako parametr konstruktoru ve třídě `PortfolioService`, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="09d3b-164">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="09d3b-165">Implementace služby gRPC</span><span class="sxs-lookup"><span data-stu-id="09d3b-165">Implement the gRPC service</span></span>

<span data-ttu-id="09d3b-166">Nyní, když jste deklarovali vaše zprávy a službu v souboru `portfolios.proto`, je nutné implementovat metody služby ve třídě `PortfolioService`, která dědí z třídy `Portfolios.PortfoliosBase` generované v gRPC.</span><span class="sxs-lookup"><span data-stu-id="09d3b-166">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="09d3b-167">Metody jsou deklarovány jako `virtual` v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="09d3b-167">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="09d3b-168">Pokud je nepřepíšete, budou ve výchozím nastavení vráceny stavový kód "neimplementováno" gRPC.</span><span class="sxs-lookup"><span data-stu-id="09d3b-168">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="09d3b-169">Začněte implementací metody `Get`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-169">Start by implementing the `Get` method.</span></span> <span data-ttu-id="09d3b-170">Výchozí přepsání vypadá jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="09d3b-170">The default override looks like the following example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="09d3b-171">Prvním problémem je, že `request.TraderId` je řetězec a služba vyžaduje `Guid`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-171">The first issue is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="09d3b-172">I když je očekávaný formát pro řetězec `UUID`, kód musí zabývat se možností, že volající odeslal neplatnou hodnotu a správně reagovat.</span><span class="sxs-lookup"><span data-stu-id="09d3b-172">Even though the expected format for the string is a `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="09d3b-173">Služba může s chybami reagovat vyvoláním `RpcException`a pomocí standardního stavového kódu `InvalidArgument` tento problém vyjádřit.</span><span class="sxs-lookup"><span data-stu-id="09d3b-173">The service can respond with errors by throwing an `RpcException`, and use the standard `InvalidArgument` status code to express the problem.</span></span>

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

<span data-ttu-id="09d3b-174">Jakmile bude k dispozici správná `Guid` hodnota `traderId`, úložiště se dá použít k načtení portfolia a vrácení do klienta.</span><span class="sxs-lookup"><span data-stu-id="09d3b-174">Once there's a proper `Guid` value for `traderId`, the repository can be used to retrieve the Portfolio and return it to the client.</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="09d3b-175">Mapování interních modelů na zprávy gRPC</span><span class="sxs-lookup"><span data-stu-id="09d3b-175">Map internal models to gRPC messages</span></span>

<span data-ttu-id="09d3b-176">Předchozí kód ve skutečnosti nefunguje, protože úložiště vrací svůj vlastní POCO model `Portfolio`, ale *gRPC potřebuje vlastní* zprávu Protobuf `Portfolio`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-176">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs *its* own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="09d3b-177">Podobně jako mapování Entity Framework typů na typy přenosů dat, nejlepším řešením je poskytnout převod mezi těmito dvěma.</span><span class="sxs-lookup"><span data-stu-id="09d3b-177">Much like mapping Entity Framework types to data transfer types, the best solution is to provide conversion between the two.</span></span> <span data-ttu-id="09d3b-178">Vhodným místem pro vložení kódu je do třídy generované Protobuf, která je deklarována jako třída `partial`, aby ji bylo možné rozšířit.</span><span class="sxs-lookup"><span data-stu-id="09d3b-178">A good place to put the code for this is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended.</span></span>

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
> <span data-ttu-id="09d3b-179">Můžete použít knihovnu, jako je například [automapper](https://automapper.org/) , pro zpracování tohoto převodu z interních tříd modelu na Protobuf typy, pokud nakonfigurujete převody typu nižší úrovně jako `string`/`Guid` nebo `decimal`/`double` a mapování seznamu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-179">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="09d3b-180">S kódem převodu na místě může být implementace metody `Get` dokončena.</span><span class="sxs-lookup"><span data-stu-id="09d3b-180">With the conversion code in place, the `Get` method implementation can be completed.</span></span>

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

<span data-ttu-id="09d3b-181">Implementace metody `GetAll` je podobná.</span><span class="sxs-lookup"><span data-stu-id="09d3b-181">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="09d3b-182">Všimněte si, že pole `repeated` ve zprávách Protobuf jsou generována jako `readonly` vlastností typu `RepeatedField<T>`, takže je nutné do nich přidat položky pomocí metody `AddRange`, jako v následujícím příkladu:</span><span class="sxs-lookup"><span data-stu-id="09d3b-182">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them using the `AddRange` method, like in the following example:</span></span>

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

<span data-ttu-id="09d3b-183">Po úspěšné migraci služby Request-Reply WCF do gRPC se podívejme na vytvoření klienta z `.proto`ho souboru.</span><span class="sxs-lookup"><span data-stu-id="09d3b-183">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="09d3b-184">Vygenerovat kód klienta</span><span class="sxs-lookup"><span data-stu-id="09d3b-184">Generate client code</span></span>

<span data-ttu-id="09d3b-185">Vytvořte .NET Standard knihovnu tříd ve stejném řešení, aby obsahovala klienta.</span><span class="sxs-lookup"><span data-stu-id="09d3b-185">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="09d3b-186">Toto je primárně příklad vytváření kódu klienta, ale můžete ho zabalit pomocí NuGet a distribuovat ho do interního úložiště, aby se daly využívat jiné týmy .NET.</span><span class="sxs-lookup"><span data-stu-id="09d3b-186">This is primarily an example of creating client code, but you could package such a library using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="09d3b-187">Pokračujte a přidejte do řešení novou knihovnu tříd .NET Standard nazvanou `TraderSys.Portfolios.Client` a odstraňte soubor `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="09d3b-187">Go ahead and add a new .NET Standard Class Library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="09d3b-188">Balíček NuGet pro [Grpc .NET. Client](https://www.nuget.org/packages/Grpc.Net.Client) vyžaduje rozhraní .net Core 3,0 (nebo jiný modul runtime kompatibilní s .NET Standard 2,1).</span><span class="sxs-lookup"><span data-stu-id="09d3b-188">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="09d3b-189">Předchozí verze .NET Framework a .NET Core jsou podporovány balíčkem NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core) .</span><span class="sxs-lookup"><span data-stu-id="09d3b-189">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="09d3b-190">V aplikaci Visual Studio 2019 můžete přidat odkazy na gRPC Services podobně jako při přidávání odkazů na služby do projektů WCF v dřívějších verzích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="09d3b-190">In Visual Studio 2019, you can add references to gRPC services similar to the way you'd add Service References to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="09d3b-191">Odkazy na služby a připojené služby jsou všechny spravované ve stejném uživatelském rozhraní, ke kterému máte přístup kliknutím pravým tlačítkem myši na uzel **závislosti** v `TraderSys.Portfolios.Client` projektu v Průzkumník řešení a vybráním možnosti **Přidat připojenou službu**.</span><span class="sxs-lookup"><span data-stu-id="09d3b-191">Service References and Connected Services are all managed under the same UI now, which you can access by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="09d3b-192">V zobrazeném okně nástroje vyberte část odkazy na **služby** a klikněte na **Přidat nový odkaz na službu gRPC**.</span><span class="sxs-lookup"><span data-stu-id="09d3b-192">In the tool window that appears, select the **Service References** section and click **Add new gRPC service reference**.</span></span>

![Uživatelské rozhraní připojené služby v aplikaci Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="09d3b-194">Přejděte k souboru `portfolios.proto` v projektu `TraderSys.Portfolios`, ponechte **typ třídy generovaný** jako **klient**a klikněte na **OK**.</span><span class="sxs-lookup"><span data-stu-id="09d3b-194">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave the **type of class to be generated** as **Client**, and click **OK**.</span></span>

![Dialogové okno Přidat nový odkaz na službu gRPC v aplikaci Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="09d3b-196">Všimněte si, že toto dialogové okno také poskytuje pole Adresa URL.</span><span class="sxs-lookup"><span data-stu-id="09d3b-196">Notice that this dialog also provides a URL field.</span></span> <span data-ttu-id="09d3b-197">Pokud vaše organizace udržuje adresář `.proto`ch souborů, který je přístupný pro web, můžete vytvořit klienty pouze nastavením této adresy URL.</span><span class="sxs-lookup"><span data-stu-id="09d3b-197">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="09d3b-198">Při použití funkce **Přidat připojenou službu** sady Visual Studio je soubor `portfolios.proto` přidán do projektu knihovny tříd jako *propojený soubor*namísto zkopírování, takže změny souboru v projektu služby budou automaticky použity v klientském projektu.</span><span class="sxs-lookup"><span data-stu-id="09d3b-198">When using the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the Class Library project as a *linked file*, rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="09d3b-199">Element `<Protobuf>` v souboru `csproj` vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="09d3b-199">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="09d3b-200">Pokud nepoužíváte aplikaci Visual Studio nebo dáváte přednost práci z příkazového řádku, můžete použít globální nástroj **dotnet-grpc** pro správu odkazů Protobuf v rámci projektu .NET grpc.</span><span class="sxs-lookup"><span data-stu-id="09d3b-200">If you are not using Visual Studio or prefer to work from the command line, you can use the **dotnet-grpc** global tool to manage Protobuf references within a .NET gRPC project.</span></span> <span data-ttu-id="09d3b-201">[Další informace najdete v dokumentaci **dotnet-grpc** ](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).</span><span class="sxs-lookup"><span data-stu-id="09d3b-201">[Refer to the **dotnet-grpc** documentation for more information](https://docs.microsoft.com/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="09d3b-202">Použití služby portfolio z klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="09d3b-202">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="09d3b-203">Následující kód představuje stručný příklad použití vygenerovaného klienta v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="09d3b-203">The following code is a brief example of using the generated client in a console application.</span></span> <span data-ttu-id="09d3b-204">Podrobnější zkoumání kódu klienta gRPC je na konci této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="09d3b-204">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="09d3b-205">Nyní jste migrovali základní aplikaci WCF do ASP.NET Core služby gRPC a vytvořili klienta pro využívání služby z aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="09d3b-205">Now, you've migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="09d3b-206">V další části jsou pokryty "duplexní" služby.</span><span class="sxs-lookup"><span data-stu-id="09d3b-206">The next section will cover the more involved "duplex" services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="09d3b-207">[Předchozí](create-project.md)
>[Další](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="09d3b-207">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
