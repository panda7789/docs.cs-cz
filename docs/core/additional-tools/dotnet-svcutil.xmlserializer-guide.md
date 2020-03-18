---
title: Použití dotnet-svcutil.xmlserializer
description: Zjistěte, jak `dotnet-svcutil.xmlserializer` můžete použít balíček NuGet k předběžnému generování sestavení serializace pro projekty .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 4811647c294118cb160d25805e7d3ada97f071f9
ms.sourcegitcommit: 7588136e355e10cbc2582f389c90c127363c02a5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2020
ms.locfileid: "75344904"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="61efc-103">Použití dotnet-svcutil.xmlserializer na .NET Core</span><span class="sxs-lookup"><span data-stu-id="61efc-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="61efc-104">Balíček `dotnet-svcutil.xmlserializer` NuGet můžete předem generovat sestavení serializace pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="61efc-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="61efc-105">Předem generuje kód serializace jazyka C# pro typy v klientské aplikaci, které jsou používány wcf service contract a které mohou být serializovány XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="61efc-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="61efc-106">To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.</span><span class="sxs-lookup"><span data-stu-id="61efc-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="61efc-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="61efc-107">Prerequisites</span></span>

* <span data-ttu-id="61efc-108">[Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější</span><span class="sxs-lookup"><span data-stu-id="61efc-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="61efc-109">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="61efc-109">Your favorite code editor</span></span>

<span data-ttu-id="61efc-110">Pomocí příkazu `dotnet --info` můžete zkontrolovat, které verze sady .NET Core SDK a runtime, které jste již nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="61efc-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="61efc-111">Začínáme</span><span class="sxs-lookup"><span data-stu-id="61efc-111">Getting started</span></span>

<span data-ttu-id="61efc-112">Použití `dotnet-svcutil.xmlserializer` v aplikaci konzoly .NET Core:</span><span class="sxs-lookup"><span data-stu-id="61efc-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="61efc-113">Vytvořte službu WCF s názvem MyWCFService pomocí výchozí šablony WCF Service Application v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="61efc-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="61efc-114">Přidejte `[XmlSerializerFormat]` atribut metody služby takto:</span><span class="sxs-lookup"><span data-stu-id="61efc-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="61efc-115">Vytvořte aplikaci konzoly .NET Core jako klientskou aplikaci WCF, která se zaměřuje na verze .NET Core 2.1 nebo novější.</span><span class="sxs-lookup"><span data-stu-id="61efc-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="61efc-116">Můžete například vytvořit aplikaci s názvem MyWCFClient s následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="61efc-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="61efc-117">Chcete-li zajistit, aby váš projekt cílil na `TargetFramework` rozhraní .NET Core 2.1 nebo novější, zkontrolujte element XML v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="61efc-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="61efc-118">Přidejte odkaz `System.ServiceModel.Http` na balíček spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="61efc-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="61efc-119">Přidejte kód klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="61efc-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="61efc-120">Přidejte odkaz `dotnet-svcutil.xmlserializer` na balíček spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="61efc-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="61efc-121">Spuštění příkazu by mělo přidat položku do souboru projektu podobnou této:</span><span class="sxs-lookup"><span data-stu-id="61efc-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="61efc-122">Vytvořte aplikaci `dotnet build`spuštěním aplikace .</span><span class="sxs-lookup"><span data-stu-id="61efc-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="61efc-123">Pokud je vše úspěšné, ve výstupní složce je generováno sestavení s názvem *MyWCFClient.XmlSerializers.dll.*</span><span class="sxs-lookup"><span data-stu-id="61efc-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="61efc-124">Pokud se nástroji nepodařilo generovat sestavení, zobrazí se upozornění ve výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="61efc-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="61efc-125">Spusťte službu WCF například spuštěním `http://localhost:2561/Service1.svc` v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="61efc-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="61efc-126">Potom spusťte klientskou aplikaci a automaticky se načte a použije předem generované serializátory za běhu.</span><span class="sxs-lookup"><span data-stu-id="61efc-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
