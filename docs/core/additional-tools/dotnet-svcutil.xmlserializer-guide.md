---
title: Použití dotnet-Svcutil. XmlSerializer
description: Přečtěte si, jak můžete pomocí `dotnet-svcutil.xmlserializer` balíčku NuGet předem vygenerovat sestavení serializace pro projekty .NET Core.
author: huanwu
ms.date: 11/27/2018
ms.openlocfilehash: 14bb2e8a85ec35f08b0a83b9734a64d751074f1b
ms.sourcegitcommit: 33deec3e814238fb18a49b2a7e89278e27888291
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/02/2020
ms.locfileid: "84284322"
---
# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Použití dotnet-Svcutil. XmlSerializer v .NET Core

`dotnet-svcutil.xmlserializer`Balíček NuGet může předem vygenerovat serializaci sestavení pro projekty .NET Core. Předběžně generuje Serializační kód C# pro typy v klientské aplikaci, které používá kontrakt služby WCF a který může být serializován objektem XmlSerializer. To zlepšuje výkon při spuštění serializace XML při serializaci nebo deserializaci objektů těchto typů.

## <a name="prerequisites"></a>Požadavky

* [.NET Core 2,1 SDK](https://dotnet.microsoft.com/download) nebo novější
* Váš oblíbený editor kódu

Pomocí příkazu můžete `dotnet --info` zjistit, které verze .NET Core SDK a modulu runtime už máte nainstalované.

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

    ```dotnetcli
    dotnet new console --name MyWCFClient
    ```

    Chcete-li zajistit, aby byl projekt cílen na rozhraní .NET Core 2,1 nebo vyšší, prozkoumejte `TargetFramework` XML element v souboru projektu:

    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```

3. Pomocí následujícího příkazu přidejte odkaz na balíček `System.ServiceModel.Http` :

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

5. Přidejte odkaz na `dotnet-svcutil.xmlserializer` balíček spuštěním následujícího příkazu:
  
    ```dotnetcli
    dotnet add package dotnet-svcutil.xmlserializer
    ```

    Spuštění příkazu by mělo do souboru projektu přidat položku podobný tomuto:
  
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Sestavte aplikaci spuštěním `dotnet build` . Pokud je vše úspěšné, sestavení s názvem *MyWCFClient. XmlSerializers. dll* je vygenerováno ve výstupní složce. Pokud nástroji se nepovedlo vygenerovat sestavení, zobrazí se upozornění ve výstupu sestavení.

7. Spusťte službu WCF tak, aby například běžela `http://localhost:2561/Service1.svc` v prohlížeči. Pak spusťte klientskou aplikaci a automaticky načte a použije předem vygenerované serializace za běhu.
