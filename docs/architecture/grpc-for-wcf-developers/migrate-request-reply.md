---
title: Migrace služby Request-Reply WCF do gRPC-gRPC pro vývojáře WCF
description: Naučte se migrovat jednoduchou službu Request-Reply z WCF na gRPC.
ms.date: 09/02/2019
ms.openlocfilehash: 018aa94a15cdcb1e0f559afb7b3a88cd4f915398
ms.sourcegitcommit: 44a7cd8687f227fc6db3211ccf4783dc20235e51
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 02/26/2020
ms.locfileid: "77628550"
---
# <a name="migrate-a-wcf-request-reply-service-to-a-grpc-unary-rpc"></a><span data-ttu-id="6ab38-103">Migrace služby požadavek-odpověď WCF na gRPC unární RPC</span><span class="sxs-lookup"><span data-stu-id="6ab38-103">Migrate a WCF request-reply service to a gRPC unary RPC</span></span>

<span data-ttu-id="6ab38-104">V této části se dozvíte, jak migrovat základní službu Request-Reply ve službě WCF do unární služby RPC v ASP.NET Core gRPC.</span><span class="sxs-lookup"><span data-stu-id="6ab38-104">This section covers how to migrate a basic request-reply service in WCF to a unary RPC service in ASP.NET Core gRPC.</span></span> <span data-ttu-id="6ab38-105">Tyto služby jsou nejjednodušší typy služeb v Windows Communication Foundation (WCF) i v gRPC, takže je to vynikající místo, kde začít.</span><span class="sxs-lookup"><span data-stu-id="6ab38-105">These services are the simplest service types in both Windows Communication Foundation (WCF) and gRPC, so it's an excellent place to start.</span></span> <span data-ttu-id="6ab38-106">Po migraci služby se dozvíte, jak vygenerovat klientskou knihovnu ze stejného `.proto` souboru pro využívání služby z klientské aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="6ab38-106">After migrating the service, you'll learn how to generate a client library from the same `.proto` file to consume the service from a .NET client application.</span></span>

## <a name="the-wcf-solution"></a><span data-ttu-id="6ab38-107">Řešení WCF</span><span class="sxs-lookup"><span data-stu-id="6ab38-107">The WCF solution</span></span>

<span data-ttu-id="6ab38-108">[Řešení PortfoliosSample](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) zahrnuje jednoduchou službu portfolio požadavků a odpovědí ke stažení jednoho portfolia nebo všech portfolií pro daného dodavatele.</span><span class="sxs-lookup"><span data-stu-id="6ab38-108">The [PortfoliosSample solution](https://github.com/dotnet-architecture/grpc-for-wcf-developers/tree/master/PortfoliosSample/wcf/TraderSys) includes a simple request-reply Portfolio service to download either a single portfolio or all portfolios for a given trader.</span></span> <span data-ttu-id="6ab38-109">Služba je definována v `IPortfolioService` rozhraní s atributem `ServiceContract`:</span><span class="sxs-lookup"><span data-stu-id="6ab38-109">The service is defined in the interface `IPortfolioService` with a `ServiceContract` attribute:</span></span>

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

<span data-ttu-id="6ab38-110">`Portfolio` model je jednoduchá C# třída označená pomocí [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) a obsahuje seznam objektů `PortfolioItem`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-110">The `Portfolio` model is a simple C# class marked with [DataContract](xref:System.Runtime.Serialization.DataContractAttribute) and including a list of `PortfolioItem` objects.</span></span> <span data-ttu-id="6ab38-111">Tyto modely jsou definovány v `TraderSys.PortfolioData` projektu společně s třídou úložiště, která představuje abstrakci přístupu k datům.</span><span class="sxs-lookup"><span data-stu-id="6ab38-111">These models are defined in the `TraderSys.PortfolioData` project along with a repository class that represents a data access abstraction.</span></span>

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

<span data-ttu-id="6ab38-112">Implementace `ServiceContract` používá třídu úložiště poskytovanou prostřednictvím injektáže, který vrací instance `DataContract`ch typů:</span><span class="sxs-lookup"><span data-stu-id="6ab38-112">The `ServiceContract` implementation uses a repository class provided via dependency injection that returns instances of the `DataContract` types:</span></span>

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

## <a name="the-portfoliosproto-file"></a><span data-ttu-id="6ab38-113">Portfolio. soubor.</span><span class="sxs-lookup"><span data-stu-id="6ab38-113">The portfolios.proto file</span></span>

<span data-ttu-id="6ab38-114">Pokud jste postupovali podle pokynů v předchozí části, měli byste mít projekt gRPC s `portfolios.proto` souborem, který vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="6ab38-114">If you followed the instructions in the previous section, you should have a gRPC project with a `portfolios.proto` file that looks like this:</span></span>

```protobuf
syntax = "proto3";

option csharp_namespace = "TraderSys.Portfolios.Protos";

package PortfolioServer;

service Portfolios {
  // RPCs will go here
}
```

<span data-ttu-id="6ab38-115">Prvním krokem je migrace tříd `DataContract` na jejich ekvivalenty Protobuf.</span><span class="sxs-lookup"><span data-stu-id="6ab38-115">The first step is to migrate the `DataContract` classes to their Protobuf equivalents.</span></span>

## <a name="convert-the-datacontract-classes-to-grpc-messages"></a><span data-ttu-id="6ab38-116">Převést třídy DataContract na zprávy gRPC</span><span class="sxs-lookup"><span data-stu-id="6ab38-116">Convert the DataContract classes to gRPC messages</span></span>

<span data-ttu-id="6ab38-117">Třída `PortfolioItem` bude nejprve převedena na zprávu Protobuf, protože na ní závisí třída `Portfolio`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-117">The `PortfolioItem` class will be converted to a Protobuf message first, because the `Portfolio` class depends on it.</span></span> <span data-ttu-id="6ab38-118">Třída je jednoduchá a tři vlastnosti jsou mapovány přímo na gRPC datové typy.</span><span class="sxs-lookup"><span data-stu-id="6ab38-118">The class is simple, and three of the properties map directly to gRPC data types.</span></span> <span data-ttu-id="6ab38-119">Vlastnost `Cost`, která představuje cenu vyplácenou za akcie při nákupu, je pole `decimal`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-119">The `Cost` property, which represents the price paid for the shares at purchase, is a `decimal` field.</span></span> <span data-ttu-id="6ab38-120">gRPC podporuje pouze `float` nebo `double` pro skutečná čísla, která nejsou vhodná pro měnu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-120">gRPC supports only `float` or `double` for real numbers, which aren't suitable for currency.</span></span> <span data-ttu-id="6ab38-121">Vzhledem k tomu, že se ceny za sdílení liší minimálně v jednom centu, je možné náklady vyjádřit jako `int32` z centů.</span><span class="sxs-lookup"><span data-stu-id="6ab38-121">Because share prices vary by a minimum of one cent, the cost can be expressed as an `int32` of cents.</span></span>

> [!NOTE]
> <span data-ttu-id="6ab38-122">Nezapomeňte použít camelCase pro názvy polí v souboru `.proto`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-122">Remember to use camelCase for field names in your `.proto` file.</span></span> <span data-ttu-id="6ab38-123">Generátor C# kódu je převede na PascalCase za vás a uživatelé dalších jazyků budou děkují za dodržování různých standardů kódování.</span><span class="sxs-lookup"><span data-stu-id="6ab38-123">The C# code generator will convert them to PascalCase for you, and users of other languages will thank you for respecting their different coding standards.</span></span>

```protobuf
message PortfolioItem {
    int32 id = 1;
    int32 share_id = 2;
    int32 holding = 3;
    int32 cost_cents = 4;
}
```

<span data-ttu-id="6ab38-124">Třída `Portfolio` je trochu složitější.</span><span class="sxs-lookup"><span data-stu-id="6ab38-124">The `Portfolio` class is a little more complicated.</span></span> <span data-ttu-id="6ab38-125">V kódu WCF vývojář použil `Guid` pro vlastnost `TraderId` a obsahuje `List<PortfolioItem>`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-125">In the WCF code, the developer used a `Guid` for the `TraderId` property, and contains a `List<PortfolioItem>`.</span></span> <span data-ttu-id="6ab38-126">V Protobuf, který nemá `UUID` typ první třídy, byste měli použít `string` pro pole `traderId` a analyzovat ho ve vlastním kódu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-126">In Protobuf, which doesn't have a first-class `UUID` type, you should use a `string` for the `traderId` field and parse it in your own code.</span></span> <span data-ttu-id="6ab38-127">Pro seznam položek použijte klíčové slovo `repeated` v poli.</span><span class="sxs-lookup"><span data-stu-id="6ab38-127">For the list of items, use the `repeated` keyword on the field.</span></span>

```protobuf
message Portfolio {
    int32 id = 1;
    string trader_id = 2;
    repeated PortfolioItem items = 3;
}
```

<span data-ttu-id="6ab38-128">Teď, když máte datové zprávy, můžete deklarovat koncové body RPC služby.</span><span class="sxs-lookup"><span data-stu-id="6ab38-128">Now that you have the data messages, you can declare the service RPC endpoints.</span></span>

## <a name="convert-servicecontract-to-a-grpc-service"></a><span data-ttu-id="6ab38-129">Převést třídu ServiceContract na službu gRPC</span><span class="sxs-lookup"><span data-stu-id="6ab38-129">Convert ServiceContract to a gRPC service</span></span>

<span data-ttu-id="6ab38-130">Metoda `Get` WCF používá dva parametry: `Guid traderId` a `int portfolioId`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-130">The WCF `Get` method takes two parameters: `Guid traderId` and `int portfolioId`.</span></span> <span data-ttu-id="6ab38-131">metody služby gRPC mohou převzít pouze jeden parametr, takže musíte vytvořit zprávu pro uložení těchto dvou hodnot.</span><span class="sxs-lookup"><span data-stu-id="6ab38-131">gRPC service methods can take only a single parameter, so you need to create a message to hold the two values.</span></span> <span data-ttu-id="6ab38-132">Běžným postupem je pojmenování těchto objektů požadavků stejným názvem jako metoda následovaná `Request`příponou.</span><span class="sxs-lookup"><span data-stu-id="6ab38-132">It's common practice to name these request objects with the same name as the method followed by the suffix `Request`.</span></span> <span data-ttu-id="6ab38-133">`string` se znovu používá pro pole `traderId` namísto `Guid`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-133">Again, `string` is being used for the `traderId` field instead of `Guid`.</span></span>

<span data-ttu-id="6ab38-134">Služba může pouze vrátit `Portfolio` zprávu přímo, ale to může mít vliv na zpětnou kompatibilitu v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-134">The service could just return a `Portfolio` message directly, but again, this could affect backward compatibility in the future.</span></span> <span data-ttu-id="6ab38-135">Je dobrým zvykem definovat samostatné `Request` a `Response` zprávy pro každou metodu ve službě, a to i v případě, že je mnoho z nich teď stejné.</span><span class="sxs-lookup"><span data-stu-id="6ab38-135">It's a good practice to define separate `Request` and `Response` messages for every method in a service, even if many of them are the same right now.</span></span> <span data-ttu-id="6ab38-136">Deklarujete `GetResponse`ovou zprávu s jedním `Portfolio` polem.</span><span class="sxs-lookup"><span data-stu-id="6ab38-136">So declare a `GetResponse` message with a single `Portfolio` field.</span></span>

<span data-ttu-id="6ab38-137">Tento příklad ukazuje deklaraci metody služby gRPC ve zprávě `GetRequest`:</span><span class="sxs-lookup"><span data-stu-id="6ab38-137">This example shows the declaration of the gRPC service method with the `GetRequest` message:</span></span>

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

<span data-ttu-id="6ab38-138">Metoda `GetAll` WCF přebírá pouze jeden parametr, `traderId`, takže se může zdát, že jako typ parametru lze zadat `string`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-138">The WCF `GetAll` method takes only a single parameter, `traderId`, so it might seem that you could specify `string` as the parameter type.</span></span> <span data-ttu-id="6ab38-139">Ale gRPC vyžaduje definovaný typ zprávy.</span><span class="sxs-lookup"><span data-stu-id="6ab38-139">But gRPC requires a defined message type.</span></span> <span data-ttu-id="6ab38-140">Tento požadavek pomáhá vyhodnotit postup použití vlastních zpráv pro všechny vstupy a výstupy, a to z důvodu zpětné kompatibility v budoucnu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-140">This requirement helps to enforce the practice of using custom messages for all inputs and outputs, for future backward compatibility.</span></span>

<span data-ttu-id="6ab38-141">Metoda WCF také vrací `List<Portfolio>`, ale ze stejného důvodu nepovoluje jednoduché typy parametrů, gRPC nepovoluje `repeated Portfolio` jako návratový typ.</span><span class="sxs-lookup"><span data-stu-id="6ab38-141">The WCF method also returns a `List<Portfolio>`, but for the same reason it doesn't allow simple parameter types, gRPC won't allow `repeated Portfolio` as a return type.</span></span> <span data-ttu-id="6ab38-142">Místo toho vytvořte `GetAllResponse` typ pro zabalení seznamu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-142">Instead, create a `GetAllResponse` type to wrap the list.</span></span>

> [!WARNING]
> <span data-ttu-id="6ab38-143">Můžete se rozhodnout, že vytvoříte zprávu `PortfolioList` nebo něco podobného a použijete ji napříč různými metodami služby, ale tuto pokušení byste měli odolat.</span><span class="sxs-lookup"><span data-stu-id="6ab38-143">You might be tempted to create a `PortfolioList` message or something similar and use it across multiple service methods, but you should resist this temptation.</span></span> <span data-ttu-id="6ab38-144">Není možné zjistit, jak se různé metody ve službě budou vyvíjet, takže jejich zprávy budou specifické a čistě oddělené.</span><span class="sxs-lookup"><span data-stu-id="6ab38-144">It's impossible to know how the various methods on a service will evolve, so keep their messages specific and cleanly separated.</span></span>

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

<span data-ttu-id="6ab38-145">Pokud uložíte projekt s těmito změnami, cíl sestavení gRPC se spustí na pozadí a vygeneruje všechny typy zpráv Protobuf a základní třídu, kterou můžete zdědit pro implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="6ab38-145">If you save your project with these changes, the gRPC build target will run in the background and generate all the Protobuf message types and a base class that you can inherit to implement the service.</span></span>

<span data-ttu-id="6ab38-146">Otevřete třídu `Services/GreeterService.cs` a odstraňte ukázkový kód.</span><span class="sxs-lookup"><span data-stu-id="6ab38-146">Open the `Services/GreeterService.cs` class and delete the example code.</span></span> <span data-ttu-id="6ab38-147">Nyní můžete přidat implementaci služby portfolio.</span><span class="sxs-lookup"><span data-stu-id="6ab38-147">Now you can add the Portfolio service implementation.</span></span> <span data-ttu-id="6ab38-148">Vygenerovaná základní třída bude v oboru názvů `Protos` a je vygenerována jako vnořená třída.</span><span class="sxs-lookup"><span data-stu-id="6ab38-148">The generated base class will be in the `Protos` namespace and is generated as a nested class.</span></span> <span data-ttu-id="6ab38-149">gRPC vytvoří statickou třídu se stejným názvem jako služba v souboru `.proto` a základní třídou s příponou `Base` uvnitř této statické třídy, takže úplný identifikátor základního typu je `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-149">gRPC creates a static class with the same name as the service in the `.proto` file and a base class with the suffix `Base` inside that static class, so the full identifier for the base type is `TraderSys.Portfolios.Protos.Portfolios.PortfoliosBase`.</span></span>

```csharp
namespace TraderSys.Portfolios.Services
{
    public class PortfolioService : Protos.Portfolios.PortfoliosBase
    {
    }
}
```

<span data-ttu-id="6ab38-150">Základní třída deklaruje `virtual` metody pro `Get` a `GetAll`, které lze přepsat pro implementaci služby.</span><span class="sxs-lookup"><span data-stu-id="6ab38-150">The base class declares `virtual` methods for `Get` and `GetAll` that can be overridden to implement the service.</span></span> <span data-ttu-id="6ab38-151">Metody jsou `virtual` spíše než `abstract`, takže pokud je neimplementujete, může služba vrátit explicitní stavový kód gRPC `Unimplemented`, podobně jako můžete vyvolat `NotImplementedException` v běžném C# kódu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-151">The methods are `virtual` rather than `abstract` so that if you don't implement them, the service can return an explicit gRPC `Unimplemented` status code, much like you might throw a `NotImplementedException` in regular C# code.</span></span>

<span data-ttu-id="6ab38-152">Signatura všech gRPC unárních metod služby v ASP.NET Core je konzistentní.</span><span class="sxs-lookup"><span data-stu-id="6ab38-152">The signature for all gRPC unary service methods in ASP.NET Core is consistent.</span></span> <span data-ttu-id="6ab38-153">Existují dva parametry: první je typ zprávy deklarovaný v souboru `.proto` a druhý je `ServerCallContext`, který funguje podobně jako `HttpContext` od ASP.NET Core.</span><span class="sxs-lookup"><span data-stu-id="6ab38-153">There are two parameters: the first is the message type declared in the `.proto` file, and the second is a `ServerCallContext` that works similarly to the `HttpContext` from ASP.NET Core.</span></span> <span data-ttu-id="6ab38-154">Ve skutečnosti existuje metoda rozšíření s názvem `GetHttpContext` ve třídě `ServerCallContext`, kterou můžete použít k získání základní `HttpContext`, i když byste ji neměli potřebovat často použít.</span><span class="sxs-lookup"><span data-stu-id="6ab38-154">In fact, there's an extension method called `GetHttpContext` on the `ServerCallContext` class that you can use to get the underlying `HttpContext`, although you shouldn't need to use it often.</span></span> <span data-ttu-id="6ab38-155">Podíváme se na `ServerCallContext` později v této kapitole a také v kapitole, která se zabývá ověřováním.</span><span class="sxs-lookup"><span data-stu-id="6ab38-155">We'll take a look at `ServerCallContext` later in this chapter, and also in the chapter that discusses authentication.</span></span>

<span data-ttu-id="6ab38-156">Návratový typ metody je `Task<T>`, kde `T` je typ zprávy odpovědi.</span><span class="sxs-lookup"><span data-stu-id="6ab38-156">The method's return type is a `Task<T>`, where `T` is the response message type.</span></span> <span data-ttu-id="6ab38-157">Všechny metody služby gRPC jsou asynchronní.</span><span class="sxs-lookup"><span data-stu-id="6ab38-157">All gRPC service methods are asynchronous.</span></span>

## <a name="migrate-the-portfoliodata-library-to-net-core"></a><span data-ttu-id="6ab38-158">Migrace knihovny PortfolioData do .NET Core</span><span class="sxs-lookup"><span data-stu-id="6ab38-158">Migrate the PortfolioData library to .NET Core</span></span>

<span data-ttu-id="6ab38-159">V tomto okamžiku projekt potřebuje úložiště portfolia a modely obsažené v knihovně tříd `TraderSys.PortfolioData` v řešení WCF.</span><span class="sxs-lookup"><span data-stu-id="6ab38-159">At this point, the project needs the Portfolio repository and models contained in the `TraderSys.PortfolioData` class library in the WCF solution.</span></span> <span data-ttu-id="6ab38-160">Nejjednodušší způsob, jak je přenést do více instancí, je vytvořit novou knihovnu tříd pomocí dialogového okna **Nový projekt** aplikace Visual Studio se šablonou knihovny tříd (.NET Standard), nebo z příkazového řádku pomocí .NET Core CLI spustit tyto příkazy z adresáře, který obsahuje soubor `TraderSys.sln`:</span><span class="sxs-lookup"><span data-stu-id="6ab38-160">The easiest way to bring them across is to create a new class library by using either the Visual Studio **New project** dialog box with the Class Library (.NET Standard) template, or from the command line by using the .NET Core CLI, running these commands from the directory that contains the `TraderSys.sln` file:</span></span>

```dotnetcli
dotnet new classlib -o src/TraderSys.PortfolioData
dotnet sln add src/TraderSys.PortfolioData
```

<span data-ttu-id="6ab38-161">Poté, co jste vytvořili knihovnu a přidáte ji do řešení, odstraňte vygenerovaný `Class1.cs` soubor a zkopírujte soubory z knihovny řešení WCF do nové složky knihovny tříd, čímž zachováte strukturu složek:</span><span class="sxs-lookup"><span data-stu-id="6ab38-161">After you've created the library and added it to the solution, delete the generated `Class1.cs` file and copy the files from the WCF solution's library into the new class library's folder, keeping the folder structure:</span></span>

```
Models
  Portfolio.cs
  PortfolioItem.cs
IPortfolioRepository.cs
PortfolioRepository.cs
```

<span data-ttu-id="6ab38-162">Projekty .NET ve stylu sady SDK automaticky zahrnují všechny `.cs` soubory v nebo v jejich vlastním adresáři, takže je nemusíte explicitně přidávat do projektu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-162">SDK-style .NET projects automatically include any `.cs` files in or under their own directory, so you don't need to explicitly add them to the project.</span></span> <span data-ttu-id="6ab38-163">Jediným krokem je odebrání atributů `DataContract` a `DataMember` z tříd `Portfolio` a `PortfolioItem`, aby byly prostými starými C# třídami:</span><span class="sxs-lookup"><span data-stu-id="6ab38-163">The only step remaining is to remove the `DataContract` and `DataMember` attributes from the `Portfolio` and `PortfolioItem` classes so they're plain old C# classes:</span></span>

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

## <a name="use-aspnet-core-dependency-injection"></a><span data-ttu-id="6ab38-164">Použít vkládání závislostí ASP.NET Core</span><span class="sxs-lookup"><span data-stu-id="6ab38-164">Use ASP.NET Core dependency injection</span></span>

<span data-ttu-id="6ab38-165">Nyní můžete přidat odkaz na tuto knihovnu do projektu aplikace gRPC a spotřebovat třídu `PortfolioRepository` pomocí injektáže závislosti v implementaci služby gRPC.</span><span class="sxs-lookup"><span data-stu-id="6ab38-165">Now you can add a reference to this library to the gRPC application project and consume the `PortfolioRepository` class by using dependency injection in the gRPC service implementation.</span></span> <span data-ttu-id="6ab38-166">V aplikaci WCF bylo vkládání závislostí zajištěno kontejnerem Autofac IoC.</span><span class="sxs-lookup"><span data-stu-id="6ab38-166">In the WCF application, dependency injection was provided by the Autofac IoC container.</span></span> <span data-ttu-id="6ab38-167">ASP.NET Core má v příkazu vloženýmiy pro vkládání závislostí.</span><span class="sxs-lookup"><span data-stu-id="6ab38-167">ASP.NET Core has dependency injection baked in.</span></span> <span data-ttu-id="6ab38-168">Úložiště můžete zaregistrovat v metodě `ConfigureServices` `Startup` třídy:</span><span class="sxs-lookup"><span data-stu-id="6ab38-168">You can register the repository in the `ConfigureServices` method in the `Startup` class:</span></span>

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

<span data-ttu-id="6ab38-169">Implementaci `IPortfolioRepository` lze nyní zadat jako parametr konstruktoru ve třídě `PortfolioService`, jak je znázorněno níže:</span><span class="sxs-lookup"><span data-stu-id="6ab38-169">The `IPortfolioRepository` implementation can now be specified as a constructor parameter in the `PortfolioService` class, as follows:</span></span>

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

## <a name="implement-the-grpc-service"></a><span data-ttu-id="6ab38-170">Implementace služby gRPC</span><span class="sxs-lookup"><span data-stu-id="6ab38-170">Implement the gRPC service</span></span>

<span data-ttu-id="6ab38-171">Nyní, když jste deklarovali vaše zprávy a službu v souboru `portfolios.proto`, je nutné implementovat metody služby ve třídě `PortfolioService`, která dědí z třídy `Portfolios.PortfoliosBase` generované v gRPC.</span><span class="sxs-lookup"><span data-stu-id="6ab38-171">Now that you've declared your messages and your service in the `portfolios.proto` file, you have to implement the service methods in the `PortfolioService` class that inherits from the gRPC-generated `Portfolios.PortfoliosBase` class.</span></span> <span data-ttu-id="6ab38-172">Metody jsou deklarovány jako `virtual` v základní třídě.</span><span class="sxs-lookup"><span data-stu-id="6ab38-172">The methods are declared as `virtual` in the base class.</span></span> <span data-ttu-id="6ab38-173">Pokud je nepřepíšete, budou ve výchozím nastavení vráceny stavový kód "neimplementováno" gRPC.</span><span class="sxs-lookup"><span data-stu-id="6ab38-173">If you don't override them, they'll return a gRPC "Not Implemented" status code by default.</span></span>

<span data-ttu-id="6ab38-174">Začněte implementací metody `Get`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-174">Start by implementing the `Get` method.</span></span> <span data-ttu-id="6ab38-175">Výchozí přepsání vypadá jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="6ab38-175">The default override looks like this example:</span></span>

```csharp
public override Task<GetResponse> Get(GetRequest request, ServerCallContext context)
{
    return base.Get(request, context);
}
```

<span data-ttu-id="6ab38-176">Prvním problémem je, že `request.TraderId` je řetězec a služba vyžaduje `Guid`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-176">The first problem is that `request.TraderId` is a string, and the service requires a `Guid`.</span></span> <span data-ttu-id="6ab38-177">I když je očekávaný formát pro řetězec `UUID`, musí kód zabývat se možností, že volající odeslal neplatnou hodnotu a odpovídajícím způsobem reagovat.</span><span class="sxs-lookup"><span data-stu-id="6ab38-177">Even though the expected format for the string is `UUID`, the code has to deal with the possibility that a caller has sent an invalid value and respond appropriately.</span></span> <span data-ttu-id="6ab38-178">Služba může reagovat s chybami tím, že vyvolají `RpcException` a použije standardní stavový kód `InvalidArgument` k vyjádření problému:</span><span class="sxs-lookup"><span data-stu-id="6ab38-178">The service can respond with errors by throwing an `RpcException` and use the standard `InvalidArgument` status code to express the problem:</span></span>

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

<span data-ttu-id="6ab38-179">Po použití správné `Guid` hodnoty pro `traderId`můžete k načtení portfolia použít úložiště a vrátit ho do klienta:</span><span class="sxs-lookup"><span data-stu-id="6ab38-179">After there's a proper `Guid` value for `traderId`, you can use the repository to retrieve the Portfolio and return it to the client:</span></span>

```csharp
    var response = new GetResponse
    {
        Portfolio = await _repository.GetAsync(request.TraderId, request.PortfolioId)
    };
```

### <a name="map-internal-models-to-grpc-messages"></a><span data-ttu-id="6ab38-180">Mapování interních modelů na zprávy gRPC</span><span class="sxs-lookup"><span data-stu-id="6ab38-180">Map internal models to gRPC messages</span></span>

<span data-ttu-id="6ab38-181">Předchozí kód ve skutečnosti nefunguje, protože úložiště vrací svůj vlastní POCO model `Portfolio`, ale gRPC potřebuje vlastní zprávu Protobuf `Portfolio`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-181">The previous code doesn't actually work because the repository is returning its own POCO model `Portfolio`, but gRPC needs its own Protobuf message `Portfolio`.</span></span> <span data-ttu-id="6ab38-182">Stejně jako při mapování typů Entity Framework na typy přenosu dat, nejlepším řešením je poskytnout převod mezi těmito dvěma.</span><span class="sxs-lookup"><span data-stu-id="6ab38-182">As when you map Entity Framework types to data transfer types, the best solution is to provide a conversion between the two.</span></span> <span data-ttu-id="6ab38-183">Dobrým místem pro vložení kódu pro tento převod je v třídě generované Protobuf, která je deklarována jako třída `partial`, aby ji bylo možné rozšířit:</span><span class="sxs-lookup"><span data-stu-id="6ab38-183">A good place to put the code for this conversion is in the Protobuf-generated class, which is declared as a `partial` class so it can be extended:</span></span>

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
> <span data-ttu-id="6ab38-184">Můžete použít knihovnu, jako je například [automapper](https://automapper.org/) , pro zpracování tohoto převodu z interních tříd modelu na Protobuf typy, pokud nakonfigurujete převody typu nižší úrovně jako `string`/`Guid` nebo `decimal`/`double` a mapování seznamu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-184">You could use a library like [AutoMapper](https://automapper.org/) to handle this conversion from internal model classes to Protobuf types, as long as you configure the lower-level type conversions like `string`/`Guid` or `decimal`/`double` and the list mapping.</span></span>

<span data-ttu-id="6ab38-185">Teď, když máte na místě převod kódu, můžete dokončit implementaci `Get` metody:</span><span class="sxs-lookup"><span data-stu-id="6ab38-185">Now that you have the conversion code in place, you can complete the `Get` method implementation:</span></span>

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

<span data-ttu-id="6ab38-186">Implementace metody `GetAll` je podobná.</span><span class="sxs-lookup"><span data-stu-id="6ab38-186">The implementation of the `GetAll` method is similar.</span></span> <span data-ttu-id="6ab38-187">Všimněte si, že pole `repeated` ve zprávách Protobuf jsou generována jako `readonly` vlastností typu `RepeatedField<T>`, takže je nutné do nich přidat položky pomocí metody `AddRange`, jako v tomto příkladu:</span><span class="sxs-lookup"><span data-stu-id="6ab38-187">Note that the `repeated` fields on Protobuf messages are generated as `readonly` properties of type `RepeatedField<T>`, so you have to add items to them by using the `AddRange` method, like in this example:</span></span>

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

<span data-ttu-id="6ab38-188">Po úspěšné migraci služby Request-Reply WCF do gRPC se podívejme na vytvoření klienta z `.proto`ho souboru.</span><span class="sxs-lookup"><span data-stu-id="6ab38-188">Having successfully migrated the WCF request-reply service to gRPC, let's look at creating a client for it from the `.proto` file.</span></span>

## <a name="generate-client-code"></a><span data-ttu-id="6ab38-189">Vygenerovat kód klienta</span><span class="sxs-lookup"><span data-stu-id="6ab38-189">Generate client code</span></span>

<span data-ttu-id="6ab38-190">Vytvořte .NET Standard knihovnu tříd ve stejném řešení, aby obsahovala klienta.</span><span class="sxs-lookup"><span data-stu-id="6ab38-190">Create a .NET Standard class library in the same solution to contain the client.</span></span> <span data-ttu-id="6ab38-191">Toto je primárně příklad vytváření kódu klienta, ale tuto knihovnu můžete zabalit pomocí nástroje NuGet a distribuovat ji do interního úložiště, aby se daly využívat jiné týmy .NET.</span><span class="sxs-lookup"><span data-stu-id="6ab38-191">This is primarily an example of creating client code, but you could package such a library by using NuGet and distribute it on an internal repository for other .NET teams to consume.</span></span> <span data-ttu-id="6ab38-192">Pokračujte a přidejte do řešení novou knihovnu tříd .NET Standard nazvanou `TraderSys.Portfolios.Client` a odstraňte soubor `Class1.cs`.</span><span class="sxs-lookup"><span data-stu-id="6ab38-192">Go ahead and add a new .NET Standard class library called `TraderSys.Portfolios.Client` to the solution and delete the `Class1.cs` file.</span></span>

> [!CAUTION]
> <span data-ttu-id="6ab38-193">Balíček NuGet pro [Grpc .NET. Client](https://www.nuget.org/packages/Grpc.Net.Client) vyžaduje rozhraní .net Core 3,0 (nebo jiný modul runtime kompatibilní s .NET Standard 2,1).</span><span class="sxs-lookup"><span data-stu-id="6ab38-193">The [Grpc.Net.Client](https://www.nuget.org/packages/Grpc.Net.Client) NuGet package requires .NET Core 3.0 (or another .NET Standard 2.1-compliant runtime).</span></span> <span data-ttu-id="6ab38-194">Předchozí verze .NET Framework a .NET Core jsou podporovány balíčkem NuGet [Grpc. Core](https://www.nuget.org/packages/Grpc.Core) .</span><span class="sxs-lookup"><span data-stu-id="6ab38-194">Earlier versions of .NET Framework and .NET Core are supported by the [Grpc.Core](https://www.nuget.org/packages/Grpc.Core) NuGet package.</span></span>

<span data-ttu-id="6ab38-195">V aplikaci Visual Studio 2019 můžete přidat odkazy na gRPC Services způsobem, který je podobný jako při přidávání odkazů na služby do projektů WCF v dřívějších verzích sady Visual Studio.</span><span class="sxs-lookup"><span data-stu-id="6ab38-195">In Visual Studio 2019, you can add references to gRPC services in a way that's similar to how you'd add service references to WCF projects in earlier versions of Visual Studio.</span></span> <span data-ttu-id="6ab38-196">Odkazy na služby a připojené služby se teď spravují v rámci stejného uživatelského rozhraní.</span><span class="sxs-lookup"><span data-stu-id="6ab38-196">Service references and connected services are all managed under the same UI now.</span></span> <span data-ttu-id="6ab38-197">Přístup k uživatelskému rozhraní získáte tak, že kliknete pravým tlačítkem na uzel **závislosti** v `TraderSys.Portfolios.Client` projektu v Průzkumník řešení a vyberete **Přidat připojenou službu**.</span><span class="sxs-lookup"><span data-stu-id="6ab38-197">You can access the UI by right-clicking the **Dependencies** node in the `TraderSys.Portfolios.Client` project in Solution Explorer and selecting **Add Connected Service**.</span></span> <span data-ttu-id="6ab38-198">V zobrazeném okně nástroje vyberte oddíl odkazy na **službu** a pak vyberte **Přidat nový odkaz na službu gRPC**:</span><span class="sxs-lookup"><span data-stu-id="6ab38-198">In the tool window that appears, select the **Service References** section and then select **Add new gRPC service reference**:</span></span>

![Uživatelské rozhraní připojených služeb v aplikaci Visual Studio 2019](media/migrate-request-reply/add-connected-service.png)

<span data-ttu-id="6ab38-200">V projektu `TraderSys.Portfolios` přejděte k souboru `portfolios.proto`, **v části** **Vyberte typ třídy, který se má vygenerovat**, a pak vyberte **OK**:</span><span class="sxs-lookup"><span data-stu-id="6ab38-200">Browse to the `portfolios.proto` file in the `TraderSys.Portfolios` project, leave **Client** under **Select the type of class to be generated**, and then select **OK**:</span></span>

![Dialogové okno Přidat nový odkaz na službu gRPC v aplikaci Visual Studio 2019](media/migrate-request-reply/add-new-grpc-service-reference.png)

> [!TIP]
> <span data-ttu-id="6ab38-202">Všimněte si, že toto dialogové okno také poskytuje pole Adresa URL.</span><span class="sxs-lookup"><span data-stu-id="6ab38-202">Notice that this dialog box also provides a URL field.</span></span> <span data-ttu-id="6ab38-203">Pokud vaše organizace udržuje adresář `.proto`ch souborů, který je přístupný pro web, můžete vytvořit klienty pouze nastavením této adresy URL.</span><span class="sxs-lookup"><span data-stu-id="6ab38-203">If your organization maintains a web-accessible directory of `.proto` files, you can create clients just by setting this URL address.</span></span>

<span data-ttu-id="6ab38-204">Použijete-li funkci **Přidat připojenou službu** sady Visual Studio, soubor `portfolios.proto` se přidá do projektu knihovny tříd jako *propojený soubor* namísto zkopírování, takže změny souboru v projektu služby budou automaticky použity v klientském projektu.</span><span class="sxs-lookup"><span data-stu-id="6ab38-204">When you use the Visual Studio **Add Connected Service** feature, the `portfolios.proto` file is added to the class library project as a *linked file* rather than copied, so changes to the file in the service project will automatically be applied in the client project.</span></span> <span data-ttu-id="6ab38-205">Element `<Protobuf>` v souboru `csproj` vypadá takto:</span><span class="sxs-lookup"><span data-stu-id="6ab38-205">The `<Protobuf>` element in the `csproj` file looks like this:</span></span>

```xml
<Protobuf Include="..\TraderSys.Portfolios\Protos\portfolios.proto" GrpcServices="Client">
  <Link>Protos\portfolios.proto</Link>
</Protobuf>
```

> [!TIP]
> <span data-ttu-id="6ab38-206">Pokud nepoužíváte aplikaci Visual Studio nebo chcete pracovat z příkazového řádku, můžete použít globální nástroj `dotnet-grpc` pro správu odkazů Protobuf v projektu .NET gRPC.</span><span class="sxs-lookup"><span data-stu-id="6ab38-206">If you're not using Visual Studio or prefer to work from the command line, you can use the `dotnet-grpc` global tool to manage Protobuf references in a .NET gRPC project.</span></span> <span data-ttu-id="6ab38-207">Další informace najdete v dokumentaci k [`dotnet-grpc`](/aspnet/core/grpc/dotnet-grpc).</span><span class="sxs-lookup"><span data-stu-id="6ab38-207">For more information, see the [`dotnet-grpc` documentation](/aspnet/core/grpc/dotnet-grpc).</span></span>

### <a name="use-the-portfolios-service-from-a-client-application"></a><span data-ttu-id="6ab38-208">Použití služby portfolio z klientské aplikace</span><span class="sxs-lookup"><span data-stu-id="6ab38-208">Use the Portfolios service from a client application</span></span>

<span data-ttu-id="6ab38-209">Následující kód představuje stručný příklad použití vygenerovaného klienta v konzolové aplikaci.</span><span class="sxs-lookup"><span data-stu-id="6ab38-209">The following code is a brief example of how to use the generated client in a console application.</span></span> <span data-ttu-id="6ab38-210">Podrobnější zkoumání kódu klienta gRPC je na konci této kapitoly.</span><span class="sxs-lookup"><span data-stu-id="6ab38-210">A more detailed exploration of the gRPC client code is at the end of this chapter.</span></span>

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

<span data-ttu-id="6ab38-211">Nyní jste migrovali základní aplikaci WCF do služby ASP.NET Core gRPC a vytvořili jste klienta pro využívání služby z aplikace .NET.</span><span class="sxs-lookup"><span data-stu-id="6ab38-211">You've now migrated a basic WCF application to an ASP.NET Core gRPC service and created a client to consume the service from a .NET application.</span></span> <span data-ttu-id="6ab38-212">V další části najdete další zahrnuté duplexní služby.</span><span class="sxs-lookup"><span data-stu-id="6ab38-212">The next section will cover the more involved duplex services.</span></span>

>[!div class="step-by-step"]
><span data-ttu-id="6ab38-213">[Předchozí](create-project.md)
>[Další](migrate-duplex-services.md)</span><span class="sxs-lookup"><span data-stu-id="6ab38-213">[Previous](create-project.md)
[Next](migrate-duplex-services.md)</span></span>
