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
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Použití dotnet-svcutil.xmlserializer na .NET Core

Balíček `dotnet-svcutil.xmlserializer` NuGet můžete předem generovat sestavení serializace pro projekty .NET Core. Předem generuje kód serializace jazyka C# pro typy v klientské aplikaci, které jsou používány wcf service contract a které mohou být serializovány XmlSerializer. To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.

## <a name="prerequisites"></a>Požadavky

* [Sada .NET Core 2.1 SDK](https://dotnet.microsoft.com/download) nebo novější
* Váš oblíbený editor kódu

Pomocí příkazu `dotnet --info` můžete zkontrolovat, které verze sady .NET Core SDK a runtime, které jste již nainstalovali.

## <a name="getting-started"></a>Začínáme

Použití `dotnet-svcutil.xmlserializer` v aplikaci konzoly .NET Core:

1. Vytvořte službu WCF s názvem MyWCFService pomocí výchozí šablony WCF Service Application v rozhraní .NET Framework. Přidejte `[XmlSerializerFormat]` atribut metody služby takto:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. Vytvořte aplikaci konzoly .NET Core jako klientskou aplikaci WCF, která se zaměřuje na verze .NET Core 2.1 nebo novější. Můžete například vytvořit aplikaci s názvem MyWCFClient s následujícím příkazem:

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    Chcete-li zajistit, aby váš projekt cílil na `TargetFramework` rozhraní .NET Core 2.1 nebo novější, zkontrolujte element XML v souboru projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Přidejte odkaz `System.ServiceModel.Http` na balíček spuštěním následujícího příkazu:

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

5. Přidejte odkaz `dotnet-svcutil.xmlserializer` na balíček spuštěním následujícího příkazu:
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Spuštění příkazu by mělo přidat položku do souboru projektu podobnou této:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Vytvořte aplikaci `dotnet build`spuštěním aplikace . Pokud je vše úspěšné, ve výstupní složce je generováno sestavení s názvem *MyWCFClient.XmlSerializers.dll.* Pokud se nástroji nepodařilo generovat sestavení, zobrazí se upozornění ve výstupu sestavení.

7. Spusťte službu WCF například spuštěním `http://localhost:2561/Service1.svc` v prohlížeči. Potom spusťte klientskou aplikaci a automaticky se načte a použije předem generované serializátory za běhu.
