---
title: Použití dotnet-Svcutil. XmlSerializer
description: Naučte se, jak můžete použít balíček NuGet `dotnet-svcutil.xmlserializer` k předběžnému vygenerování sestavení serializace pro projekty .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 4811647c294118cb160d25805e7d3ada97f071f9
ms.sourcegitcommit: 30a558d23e3ac5a52071121a52c305c85fe15726
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 12/25/2019
ms.locfileid: "75344904"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="e4817-103">Použití dotnet-Svcutil. XmlSerializer v .NET Core</span><span class="sxs-lookup"><span data-stu-id="e4817-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="e4817-104">Balíček NuGet `dotnet-svcutil.xmlserializer` může předběžně generovat sestavení serializace pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="e4817-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="e4817-105">Předběžně generuje C# Serializační kód pro typy v klientské aplikaci, které používá kontrakt služby WCF a který může být serializován objektem XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="e4817-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="e4817-106">To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.</span><span class="sxs-lookup"><span data-stu-id="e4817-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="e4817-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="e4817-107">Prerequisites</span></span>

* <span data-ttu-id="e4817-108">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější</span><span class="sxs-lookup"><span data-stu-id="e4817-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="e4817-109">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="e4817-109">Your favorite code editor</span></span>

<span data-ttu-id="e4817-110">K ověření, které verze .NET Core SDK a modulu runtime už máte nainstalované, můžete použít příkaz `dotnet --info`.</span><span class="sxs-lookup"><span data-stu-id="e4817-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="e4817-111">Začínáme</span><span class="sxs-lookup"><span data-stu-id="e4817-111">Getting started</span></span>

<span data-ttu-id="e4817-112">Použití `dotnet-svcutil.xmlserializer` v konzolové aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="e4817-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="e4817-113">Vytvořte ve .NET Framework službu WCF s názvem ' MyWCFService ' pomocí výchozí šablony ' aplikace služby WCF '.</span><span class="sxs-lookup"><span data-stu-id="e4817-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="e4817-114">Do metody služby přidejte `[XmlSerializerFormat]` atribut, jako je následující:</span><span class="sxs-lookup"><span data-stu-id="e4817-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="e4817-115">Vytvořte konzolovou aplikaci .NET Core jako klientskou aplikaci WCF, která cílí na .NET Core 2,1 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="e4817-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="e4817-116">Například vytvořte aplikaci s názvem ' MyWCFClient ' s následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="e4817-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="e4817-117">Chcete-li zajistit, aby byl projekt cílen na rozhraní .NET Core 2,1 nebo vyšší, zkontrolujte `TargetFramework` XML element v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="e4817-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="e4817-118">Přidejte odkaz na balíček do `System.ServiceModel.Http` spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="e4817-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="e4817-119">Přidejte kód klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="e4817-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="e4817-120">Přidejte odkaz na balíček `dotnet-svcutil.xmlserializer` spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="e4817-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="e4817-121">Spuštění příkazu by mělo do souboru projektu přidat položku podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="e4817-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="e4817-122">Sestavte aplikaci spuštěním `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="e4817-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="e4817-123">Pokud je vše úspěšné, sestavení s názvem *MyWCFClient. XmlSerializers. dll* je vygenerováno ve výstupní složce.</span><span class="sxs-lookup"><span data-stu-id="e4817-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="e4817-124">Pokud nástroji se nepovedlo vygenerovat sestavení, zobrazí se upozornění ve výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="e4817-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="e4817-125">Spusťte službu WCF, například spuštěním `http://localhost:2561/Service1.svc` v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="e4817-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="e4817-126">Pak spusťte klientskou aplikaci a automaticky načte a použije předem vygenerované serializace za běhu.</span><span class="sxs-lookup"><span data-stu-id="e4817-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
