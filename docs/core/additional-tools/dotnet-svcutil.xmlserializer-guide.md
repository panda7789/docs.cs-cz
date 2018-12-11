# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a>Pomocí dotnet svcutil.xmlserializer v rozhraní .NET Core

## <a name="prerequisites"></a>Požadavky

Je nutné provést následující pro dotnet svcutil.xmlserializer pracovat. 

* [Sady SDK .NET core 2.1 nebo novější](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [Modulu Runtime s .NET core 2.1 nebo novější](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

Můžete použít příkaz `dotnet --info` ke kontrole, které verze rozhraní .NET Core SDK a modul runtime jste již nainstalovali.

Použití dotnet svcutil.xmlserializer v konzolovou aplikaci .NET Core:

1. Vytvoření služby WCF s názvem MyWCFService pomocí výchozí šablony aplikace služby WCF v rozhraní .NET Framework.  Přidat ```[XmlSerializerFormat]``` atributu na metodu služby takto
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. Vytvořte konzolovou aplikaci .NET Core jako cíle na netcoreapp 2.1, třeba vytvořit aplikaci s názvem 'MyWCFClient' pomocí příkazu, aplikace klienta WCF
    ```
    dotnet new console --name MyWCFClient
    ```
    Zajistěte, aby že csproj, zaměřuje netcoreapp 2.1. To se provádí pomocí následujících elementu XML v souboru .csproj
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. Přidáte odkaz na balíček pro System.ServiceModel.Http spuštěním následujícího příkazu:
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

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
5. Upravte soubor csproj a přidejte odkaz na balíček dotnet svcutil.xmlserializer. Příklad:

    i. Spusťte příkaz: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`

    ii. Přidejte následující řádky v MyWCFClient.csproj,
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. Sestavte aplikaci spuštěním `dotnet build`. Pokud všechno proběhne úspěšně, vygeneruje se ve výstupní složce sestavení s názvem MyWCFClient.XmlSerializers.dll. Upozornění ve výstupu sestavení se zobrazí, pokud nástroj pro generování sestavení se nezdařilo.

7. Spusťte službu WCF, například spuštěním http://localhost:2561/Service1.svc v prohlížeči. Spusťte klientskou aplikaci, a bude automaticky načíst a použít předem generovaného serializátory za běhu.
