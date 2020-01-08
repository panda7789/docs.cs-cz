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
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Použití dotnet-Svcutil. XmlSerializer v .NET Core

Balíček NuGet `dotnet-svcutil.xmlserializer` může předběžně generovat sestavení serializace pro projekty .NET Core. Předběžně generuje C# Serializační kód pro typy v klientské aplikaci, které používá kontrakt služby WCF a který může být serializován objektem XmlSerializer. To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.

## <a name="prerequisites"></a>Požadavky

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější
* Váš oblíbený editor kódu

K ověření, které verze .NET Core SDK a modulu runtime už máte nainstalované, můžete použít příkaz `dotnet --info`.

## <a name="getting-started"></a>Začínáme

Použití `dotnet-svcutil.xmlserializer` v konzolové aplikaci .NET Core:

1. Vytvořte ve .NET Framework službu WCF s názvem ' MyWCFService ' pomocí výchozí šablony ' aplikace služby WCF '. Do metody služby přidejte `[XmlSerializerFormat]` atribut, jako je následující:

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

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    Chcete-li zajistit, aby byl projekt cílen na rozhraní .NET Core 2,1 nebo vyšší, zkontrolujte `TargetFramework` XML element v souboru projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Přidejte odkaz na balíček do `System.ServiceModel.Http` spuštěním následujícího příkazu:

    ```dotnetcli
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

5. Přidejte odkaz na balíček `dotnet-svcutil.xmlserializer` spuštěním následujícího příkazu:
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Spuštění příkazu by mělo do souboru projektu přidat položku podobný tomuto:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Sestavte aplikaci spuštěním `dotnet build`. Pokud je vše úspěšné, sestavení s názvem *MyWCFClient. XmlSerializers. dll* je vygenerováno ve výstupní složce. Pokud nástroji se nepovedlo vygenerovat sestavení, zobrazí se upozornění ve výstupu sestavení.

7. Spusťte službu WCF, například spuštěním `http://localhost:2561/Service1.svc` v prohlížeči. Pak spusťte klientskou aplikaci a automaticky načte a použije předem vygenerované serializace za běhu.
