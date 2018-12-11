---
title: Pomocí dotnet svcutil.xmlserializer v rozhraní .NET Core
description: Zjistěte, jak můžete využít `dotnet-svcutil.xmlserializer` balíček NuGet pro předběžně generovat sestavení serializace pro projekty .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: f5ffed47079a3ee122c7784d0c61c4d40461ba26
ms.sourcegitcommit: bdd930b5df20a45c29483d905526a2a3e4d17c5b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/11/2018
ms.locfileid: "53235537"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="91f75-103">Pomocí dotnet svcutil.xmlserializer v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="91f75-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="91f75-104">`dotnet-svcutil.xmlserializer` Balíček NuGet můžete předběžně generovat sestavení serializace pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="91f75-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="91f75-105">Předem vygeneruje C# Serializační kód pro typy v klientské aplikaci, které jsou používány kontraktu služby WCF a, který lze serializovat pomocí třídy XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="91f75-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="91f75-106">To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů z těchto typů.</span><span class="sxs-lookup"><span data-stu-id="91f75-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="91f75-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="91f75-107">Prerequisites</span></span>

* <span data-ttu-id="91f75-108">[Sady SDK .NET core 2.1](https://www.microsoft.com/net/download) nebo novější</span><span class="sxs-lookup"><span data-stu-id="91f75-108">[.NET Core 2.1 SDK](https://www.microsoft.com/net/download) or later</span></span>
* <span data-ttu-id="91f75-109">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="91f75-109">Your favorite code editor</span></span>

<span data-ttu-id="91f75-110">Můžete použít příkaz `dotnet --info` ke kontrole, které verze rozhraní .NET Core SDK a modul runtime jste již nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="91f75-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="91f75-111">Začínáme</span><span class="sxs-lookup"><span data-stu-id="91f75-111">Getting started</span></span>

<span data-ttu-id="91f75-112">Chcete-li použít `dotnet-svcutil.xmlserializer` v .NET Core konzolové aplikace:</span><span class="sxs-lookup"><span data-stu-id="91f75-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="91f75-113">Vytvoření služby WCF s názvem MyWCFService pomocí výchozí šablony aplikace služby WCF v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="91f75-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="91f75-114">Přidat `[XmlSerializerFormat]` atributu na metodu služby vypadat asi takto:</span><span class="sxs-lookup"><span data-stu-id="91f75-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="91f75-115">Vytvořte konzolovou aplikaci .NET Core jako aplikace klienta WCF, který cílí na .NET Core 2.1 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="91f75-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="91f75-116">Například vytvořte aplikaci s názvem 'MyWCFClient' pomocí následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="91f75-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```console
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="91f75-117">K zajištění váš projekt cílí na .NET Core 2.1 nebo novější, zkontrolujte `TargetFramework` – element XML v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="91f75-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="91f75-118">Přidat odkaz na balíček pro `System.ServiceModel.Http` spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="91f75-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```console
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="91f75-119">Přidejte kód klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="91f75-119">Add the WCF Client code:</span></span>

    ```csharp
    using System.ServiceModel;

        class Program
        {
            static void Main(string[] args)
            {
                var myBinding = new BasicHttpBinding();
                var myEndpoint = new EndpointAddress("http://localhost:2561/Service1.svc"); //Fill your service url here
                var myChannelFactory = new ChannelFactory<IService1>(myBinding, myEndpoint);
                IService1 client = myChannelFactory.CreateChannel();
                string s = client.GetData(1);
                ((ICommunicationObject)client).Close();
            }
        }

    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

5. <span data-ttu-id="91f75-120">Přidejte odkaz na `dotnet-svcutil.xmlserializer` balíčku spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="91f75-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="91f75-121">Spuštěním příkazu by měl přidejte záznam do souboru projektu, který je podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="91f75-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="91f75-122">Sestavte aplikaci spuštěním `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="91f75-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="91f75-123">Pokud všechno proběhne úspěšně, sestavení s názvem *MyWCFClient.XmlSerializers.dll* se generuje ve výstupní složce.</span><span class="sxs-lookup"><span data-stu-id="91f75-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="91f75-124">Pokud nástroj pro generování sestavení se nezdařilo, zobrazí se vám upozornění ve výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="91f75-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="91f75-125">Spustit službu WCF, například spuštění `http://localhost:2561/Service1.svc` v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="91f75-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="91f75-126">Spusťte klientskou aplikaci, a bude automaticky načíst a použít předem generovaného serializátory za běhu.</span><span class="sxs-lookup"><span data-stu-id="91f75-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>