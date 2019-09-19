---
title: Použití dotnet-Svcutil. XmlSerializer v .NET Core
description: Přečtěte si, jak můžete `dotnet-svcutil.xmlserializer` pomocí balíčku NuGet předem vygenerovat sestavení serializace pro projekty .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: f1eebeb70206ce883a8e4e4bbd5216ae0ba5507c
ms.sourcegitcommit: a4b10e1f2a8bb4e8ff902630855474a0c4f1b37a
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/19/2019
ms.locfileid: "71117268"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="cc4e5-103">Použití dotnet-Svcutil. XmlSerializer v .NET Core</span><span class="sxs-lookup"><span data-stu-id="cc4e5-103">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

<span data-ttu-id="cc4e5-104">Balíček `dotnet-svcutil.xmlserializer` NuGet může předem vygenerovat serializaci sestavení pro projekty .NET Core.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-104">The `dotnet-svcutil.xmlserializer` NuGet package can pre-generate a serialization assembly for .NET Core projects.</span></span> <span data-ttu-id="cc4e5-105">Předběžně generuje C# Serializační kód pro typy v klientské aplikaci, které používá kontrakt služby WCF a který může být serializován objektem XmlSerializer.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-105">It pre-generates C# serialization code for the types in the client application that are used by the WCF Service Contract and that can be serialized by the XmlSerializer.</span></span> <span data-ttu-id="cc4e5-106">To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-106">This improves the startup performance of XML serialization when serializing or deserializing objects of those types.</span></span>

## <a name="prerequisites"></a><span data-ttu-id="cc4e5-107">Požadavky</span><span class="sxs-lookup"><span data-stu-id="cc4e5-107">Prerequisites</span></span>

* <span data-ttu-id="cc4e5-108">[.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější</span><span class="sxs-lookup"><span data-stu-id="cc4e5-108">[.NET Core 2.1 SDK](https://dotnet.microsoft.com/download) or later</span></span>
* <span data-ttu-id="cc4e5-109">Váš oblíbený editor kódu</span><span class="sxs-lookup"><span data-stu-id="cc4e5-109">Your favorite code editor</span></span>

<span data-ttu-id="cc4e5-110">Pomocí příkazu `dotnet --info` můžete zjistit, které verze .NET Core SDK a modulu runtime už máte nainstalované.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-110">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

## <a name="getting-started"></a><span data-ttu-id="cc4e5-111">Začínáme</span><span class="sxs-lookup"><span data-stu-id="cc4e5-111">Getting started</span></span>

<span data-ttu-id="cc4e5-112">Pro použití `dotnet-svcutil.xmlserializer` v konzolové aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="cc4e5-112">To use `dotnet-svcutil.xmlserializer` in a .NET Core console application:</span></span>

1. <span data-ttu-id="cc4e5-113">Vytvořte ve .NET Framework službu WCF s názvem ' MyWCFService ' pomocí výchozí šablony ' aplikace služby WCF '.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-113">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span> <span data-ttu-id="cc4e5-114">Přidejte `[XmlSerializerFormat]` atribut pro metodu služby, například následující:</span><span class="sxs-lookup"><span data-stu-id="cc4e5-114">Add `[XmlSerializerFormat]` attribute on the service method like the following:</span></span>

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. <span data-ttu-id="cc4e5-115">Vytvořte konzolovou aplikaci .NET Core jako klientskou aplikaci WCF, která cílí na .NET Core 2,1 nebo novější verze.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-115">Create a .NET Core console application as WCF client application that targets at .NET Core 2.1 or later versions.</span></span> <span data-ttu-id="cc4e5-116">Například vytvořte aplikaci s názvem ' MyWCFClient ' s následujícím příkazem:</span><span class="sxs-lookup"><span data-stu-id="cc4e5-116">For example, create an app named 'MyWCFClient' with the following command:</span></span>

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    <span data-ttu-id="cc4e5-117">Chcete-li zajistit, aby byl projekt cílen na rozhraní .NET Core 2,1 `TargetFramework` nebo vyšší, prozkoumejte XML element v souboru projektu:</span><span class="sxs-lookup"><span data-stu-id="cc4e5-117">To ensure your project is targeting .NET Core 2.1 or later, inspect the `TargetFramework` XML element in your project file:</span></span>

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. <span data-ttu-id="cc4e5-118">Pomocí následujícího příkazu přidejte odkaz `System.ServiceModel.Http` na balíček:</span><span class="sxs-lookup"><span data-stu-id="cc4e5-118">Add a package reference to `System.ServiceModel.Http` by running the following command:</span></span>

    ```dotnetcli
    dotnet add package System.ServiceModel.Http
    ```

4. <span data-ttu-id="cc4e5-119">Přidejte kód klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="cc4e5-119">Add the WCF Client code:</span></span>

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

5. <span data-ttu-id="cc4e5-120">Přidejte odkaz na `dotnet-svcutil.xmlserializer` balíček spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="cc4e5-120">Add a reference to the `dotnet-svcutil.xmlserializer` package by running the following command:</span></span>
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    <span data-ttu-id="cc4e5-121">Spuštění příkazu by mělo do souboru projektu přidat položku podobný tomuto:</span><span class="sxs-lookup"><span data-stu-id="cc4e5-121">Running the command should add an entry to your project file similar to this:</span></span>
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="cc4e5-122">Sestavte aplikaci spuštěním `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-122">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="cc4e5-123">Pokud je vše úspěšné, sestavení s názvem *MyWCFClient. XmlSerializers. dll* je vygenerováno ve výstupní složce.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-123">If everything succeeds, an assembly named *MyWCFClient.XmlSerializers.dll* is generated in the output folder.</span></span> <span data-ttu-id="cc4e5-124">Pokud nástroji se nepovedlo vygenerovat sestavení, zobrazí se upozornění ve výstupu sestavení.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-124">If the tool failed to generate the assembly, you'll see warnings in the build output.</span></span>

7. <span data-ttu-id="cc4e5-125">Spusťte službu WCF tak, aby například běžela `http://localhost:2561/Service1.svc` v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-125">Start the WCF service by, for example, running `http://localhost:2561/Service1.svc` in the browser.</span></span> <span data-ttu-id="cc4e5-126">Pak spusťte klientskou aplikaci a automaticky načte a použije předem vygenerované serializace za běhu.</span><span class="sxs-lookup"><span data-stu-id="cc4e5-126">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
