---
title: Použití dotnet-Svcutil. XmlSerializer v .NET Core
description: Přečtěte si, jak můžete `dotnet-svcutil.xmlserializer` pomocí balíčku NuGet předem vygenerovat sestavení serializace pro projekty .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: a98f8d30f2e37b722a3bf1f93be8fe9df540a468
ms.sourcegitcommit: 205b9a204742e9c77256d43ac9d94c3f82909808
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 09/10/2019
ms.locfileid: "70848964"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Použití dotnet-Svcutil. XmlSerializer v .NET Core

Balíček `dotnet-svcutil.xmlserializer` NuGet může předem vygenerovat serializaci sestavení pro projekty .NET Core. Předběžně generuje C# Serializační kód pro typy v klientské aplikaci, které používá kontrakt služby WCF a který může být serializován objektem XmlSerializer. To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.

## <a name="prerequisites"></a>Požadavky

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější
* Váš oblíbený editor kódu

Pomocí příkazu `dotnet --info` můžete zjistit, které verze .NET Core SDK a modulu runtime už máte nainstalované.

## <a name="getting-started"></a>Začínáme

Pro použití `dotnet-svcutil.xmlserializer` v konzolové aplikaci .NET Core:

1. Vytvořte ve .NET Framework službu WCF s názvem ' MyWCFService ' pomocí výchozí šablony ' aplikace služby WCF '. Přidejte `[XmlSerializerFormat]` atribut pro metodu služby, například následující:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. Vytvořte konzolovou aplikaci .NET Core jako klientskou aplikaci WCF, která cílí na .NET Core 2,1 nebo novější verze. Například vytvořte aplikaci s názvem ' MyWCFClient ' s následujícím příkazem:

    ```console
    dotnet new console --name MyWCFClient
    ```

    Chcete-li zajistit, aby byl projekt cílen na rozhraní .NET Core 2,1 `TargetFramework` nebo vyšší, prozkoumejte XML element v souboru projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Pomocí následujícího příkazu přidejte odkaz `System.ServiceModel.Http` na balíček:

    ```console
    dotnet add package System.ServiceModel.Http
    ```

4. Přidejte kód klienta WCF:

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

5. Přidejte odkaz na `dotnet-svcutil.xmlserializer` balíček spuštěním následujícího příkazu:
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Spuštění příkazu by mělo do souboru projektu přidat položku podobný tomuto:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Sestavte aplikaci spuštěním `dotnet build`. Pokud je vše úspěšné, sestavení s názvem *MyWCFClient. XmlSerializers. dll* je vygenerováno ve výstupní složce. Pokud nástroji se nepovedlo vygenerovat sestavení, zobrazí se upozornění ve výstupu sestavení.

7. Spusťte službu WCF tak, aby například běžela `http://localhost:2561/Service1.svc` v prohlížeči. Pak spusťte klientskou aplikaci a automaticky načte a použije předem vygenerované serializace za běhu.
