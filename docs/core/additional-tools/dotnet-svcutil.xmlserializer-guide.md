---
title: Pomocí dotnet svcutil.xmlserializer v rozhraní .NET Core
description: Zjistěte, jak můžete využít `dotnet-svcutil.xmlserializer` balíček NuGet pro předběžně generovat sestavení serializace pro projekty .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 375a5ad5660658431c0d327e55513024823a6eee
ms.sourcegitcommit: 8699383914c24a0df033393f55db3369db728a7b
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/15/2019
ms.locfileid: "65632202"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Pomocí dotnet svcutil.xmlserializer v rozhraní .NET Core

`dotnet-svcutil.xmlserializer` Balíček NuGet můžete předběžně generovat sestavení serializace pro projekty .NET Core. Předem vygeneruje C# Serializační kód pro typy v klientské aplikaci, které jsou používány kontraktu služby WCF a, který lze serializovat pomocí třídy XmlSerializer. To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů z těchto typů.

## <a name="prerequisites"></a>Požadavky

* [Sady SDK .NET core 2.1](https://www.microsoft.com/net/download) nebo novější
* Váš oblíbený editor kódu

Můžete použít příkaz `dotnet --info` ke kontrole, které verze rozhraní .NET Core SDK a modul runtime jste již nainstalovali.

## <a name="getting-started"></a>Začínáme

Chcete-li použít `dotnet-svcutil.xmlserializer` v .NET Core konzolové aplikace:

1. Vytvoření služby WCF s názvem MyWCFService pomocí výchozí šablony aplikace služby WCF v rozhraní .NET Framework. Přidat `[XmlSerializerFormat]` atributu na metodu služby vypadat asi takto:

   ```csharp
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```

2. Vytvořte konzolovou aplikaci .NET Core jako aplikace klienta WCF, který cílí na .NET Core 2.1 nebo novější verze. Například vytvořte aplikaci s názvem 'MyWCFClient' pomocí následujícího příkazu:

    ```console
    dotnet new console --name MyWCFClient
    ```

    K zajištění váš projekt cílí na .NET Core 2.1 nebo novější, zkontrolujte `TargetFramework` – element XML v souboru projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Přidat odkaz na balíček pro `System.ServiceModel.Http` spuštěním následujícího příkazu:

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

5. Přidejte odkaz na `dotnet-svcutil.xmlserializer` balíčku spuštěním následujícího příkazu:
  
    ```console
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Spuštěním příkazu by měl přidejte záznam do souboru projektu, který je podobný tomuto:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Sestavte aplikaci spuštěním `dotnet build`. Pokud všechno proběhne úspěšně, sestavení s názvem *MyWCFClient.XmlSerializers.dll* se generuje ve výstupní složce. Pokud nástroj pro generování sestavení se nezdařilo, zobrazí se vám upozornění ve výstupu sestavení.

7. Spustit službu WCF, například spuštění `http://localhost:2561/Service1.svc` v prohlížeči. Spusťte klientskou aplikaci, a bude automaticky načíst a použít předem generovaného serializátory za běhu.
