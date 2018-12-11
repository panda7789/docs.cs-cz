# <a name="using-dotnet-svcutilxmlserializer-on-net-core"></a><span data-ttu-id="ba675-101">Pomocí dotnet svcutil.xmlserializer v rozhraní .NET Core</span><span class="sxs-lookup"><span data-stu-id="ba675-101">Using dotnet-svcutil.xmlserializer on .NET Core</span></span>

## <a name="prerequisites"></a><span data-ttu-id="ba675-102">Požadavky</span><span class="sxs-lookup"><span data-stu-id="ba675-102">Prerequisites</span></span>

<span data-ttu-id="ba675-103">Je nutné provést následující pro dotnet svcutil.xmlserializer pracovat.</span><span class="sxs-lookup"><span data-stu-id="ba675-103">The following is required for dotnet-svcutil.xmlserializer to work.</span></span> 

* [<span data-ttu-id="ba675-104">Sady SDK .NET core 2.1 nebo novější</span><span class="sxs-lookup"><span data-stu-id="ba675-104">.NET Core 2.1 SDK or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/sdk-2.1.300)
* [<span data-ttu-id="ba675-105">Modulu Runtime s .NET core 2.1 nebo novější</span><span class="sxs-lookup"><span data-stu-id="ba675-105">.NET Core Runtime 2.1 or later</span></span>](https://www.microsoft.com/net/download/dotnet-core/runtime-2.1.0)

<span data-ttu-id="ba675-106">Můžete použít příkaz `dotnet --info` ke kontrole, které verze rozhraní .NET Core SDK a modul runtime jste již nainstalovali.</span><span class="sxs-lookup"><span data-stu-id="ba675-106">You can use the command `dotnet --info` to check which versions of .NET Core SDK and runtime you already have installed.</span></span>

<span data-ttu-id="ba675-107">Použití dotnet svcutil.xmlserializer v konzolovou aplikaci .NET Core:</span><span class="sxs-lookup"><span data-stu-id="ba675-107">To use dotnet-svcutil.xmlserializer in a .NET Core console application:</span></span>

1. <span data-ttu-id="ba675-108">Vytvoření služby WCF s názvem MyWCFService pomocí výchozí šablony aplikace služby WCF v rozhraní .NET Framework.</span><span class="sxs-lookup"><span data-stu-id="ba675-108">Create a WCF Service named 'MyWCFService' using the default template 'WCF Service Application' in .NET Framework.</span></span>  <span data-ttu-id="ba675-109">Přidat ```[XmlSerializerFormat]``` atributu na metodu služby takto</span><span class="sxs-lookup"><span data-stu-id="ba675-109">Add ```[XmlSerializerFormat]``` attribute on the service method like the following</span></span>
    ```c#
    [ServiceContract]
    public interface IService1
    {
        [XmlSerializerFormat]
        [OperationContract(Action = "http://tempuri.org/IService1/GetData", ReplyAction = "http://tempuri.org/IService1/GetDataResponse")]
        string GetData(int value);
    }
    ```
2. <span data-ttu-id="ba675-110">Vytvořte konzolovou aplikaci .NET Core jako cíle na netcoreapp 2.1, třeba vytvořit aplikaci s názvem 'MyWCFClient' pomocí příkazu, aplikace klienta WCF</span><span class="sxs-lookup"><span data-stu-id="ba675-110">Create a .NET Core console application as WCF client application that targets at netcoreapp 2.1, e.g. create an app named 'MyWCFClient' with the command,</span></span>
    ```
    dotnet new console --name MyWCFClient
    ```
    <span data-ttu-id="ba675-111">Zajistěte, aby že csproj, zaměřuje netcoreapp 2.1.</span><span class="sxs-lookup"><span data-stu-id="ba675-111">Make sure your csproj targets a netcoreapp 2.1.</span></span> <span data-ttu-id="ba675-112">To se provádí pomocí následujících elementu XML v souboru .csproj</span><span class="sxs-lookup"><span data-stu-id="ba675-112">This is done using the following XML element in your .csproj file</span></span>
    ```xml
    <TargetFramework>netcoreapp2.1</TargetFramework>
    ```
3. <span data-ttu-id="ba675-113">Přidáte odkaz na balíček pro System.ServiceModel.Http spuštěním následujícího příkazu:</span><span class="sxs-lookup"><span data-stu-id="ba675-113">Add a package reference to System.ServiceModel.Http by running the following command:</span></span>
   
   ```dotnet add package System.ServiceModel.Http -v 4.5.0```

4. <span data-ttu-id="ba675-114">Přidejte kód klienta WCF:</span><span class="sxs-lookup"><span data-stu-id="ba675-114">Add the WCF Client code:</span></span>
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
5. <span data-ttu-id="ba675-115">Upravte soubor csproj a přidejte odkaz na balíček dotnet svcutil.xmlserializer.</span><span class="sxs-lookup"><span data-stu-id="ba675-115">Edit the .csproj file and add a reference to the dotnet-svcutil.xmlserializer package.</span></span> <span data-ttu-id="ba675-116">Příklad:</span><span class="sxs-lookup"><span data-stu-id="ba675-116">For example:</span></span>

    <span data-ttu-id="ba675-117">i.</span><span class="sxs-lookup"><span data-stu-id="ba675-117">i.</span></span> <span data-ttu-id="ba675-118">Spusťte příkaz: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span><span class="sxs-lookup"><span data-stu-id="ba675-118">Run command: `dotnet add package dotnet-svcutil.xmlserializer -v 1.0.0`</span></span>

    <span data-ttu-id="ba675-119">ii.</span><span class="sxs-lookup"><span data-stu-id="ba675-119">ii.</span></span> <span data-ttu-id="ba675-120">Přidejte následující řádky v MyWCFClient.csproj,</span><span class="sxs-lookup"><span data-stu-id="ba675-120">Add the following lines in MyWCFClient.csproj,</span></span>
    ```xml
    <ItemGroup>
      <DotNetCliToolReference Include="dotnet-svcutil.xmlserializer" Version="1.0.0" />
    </ItemGroup>
    ```

6. <span data-ttu-id="ba675-121">Sestavte aplikaci spuštěním `dotnet build`.</span><span class="sxs-lookup"><span data-stu-id="ba675-121">Build the application by running `dotnet build`.</span></span> <span data-ttu-id="ba675-122">Pokud všechno proběhne úspěšně, vygeneruje se ve výstupní složce sestavení s názvem MyWCFClient.XmlSerializers.dll.</span><span class="sxs-lookup"><span data-stu-id="ba675-122">If everything succeeds, an assembly named MyWCFClient.XmlSerializers.dll will be generated in the output folder.</span></span> <span data-ttu-id="ba675-123">Upozornění ve výstupu sestavení se zobrazí, pokud nástroj pro generování sestavení se nezdařilo.</span><span class="sxs-lookup"><span data-stu-id="ba675-123">You will see warnings in the build output if the tool failed to generate the assembly.</span></span>

7. <span data-ttu-id="ba675-124">Spusťte službu WCF, například spuštěním http://localhost:2561/Service1.svc v prohlížeči.</span><span class="sxs-lookup"><span data-stu-id="ba675-124">Start the WCF service e.g. by running http://localhost:2561/Service1.svc in the browser.</span></span> <span data-ttu-id="ba675-125">Spusťte klientskou aplikaci, a bude automaticky načíst a použít předem generovaného serializátory za běhu.</span><span class="sxs-lookup"><span data-stu-id="ba675-125">Then start the client application, and it will automatically load and use the pre-generated serializers at runtime.</span></span>
