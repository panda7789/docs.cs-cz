---
title: Volání služby typu REST ze služby WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: eaa5d08faa335740124fcf698b22d2d324cd2c54
ms.sourcegitcommit: cdb295dd1db589ce5169ac9ff096f01fd0c2da9d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/09/2020
ms.locfileid: "84576483"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="1c869-102">Volání služby typu REST ze služby WCF</span><span class="sxs-lookup"><span data-stu-id="1c869-102">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="1c869-103">Při volání služby ve stylu REST z běžné (založené na protokolu SOAP) služby WCF kontext operace v metodě služby (která obsahuje informace o příchozím požadavku) přepíše kontext, který by měl být použit odchozím požadavkem.</span><span class="sxs-lookup"><span data-stu-id="1c869-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="1c869-104">To způsobí, že požadavky HTTP GET změní na požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="1c869-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="1c869-105">Chcete-li vynutit, aby služba WCF používala správný kontext pro volání služby ve stylu REST, vytvořte novou <xref:System.ServiceModel.OperationContextScope> a zavolejte službu ve stylu REST v rámci oboru kontextu operace.</span><span class="sxs-lookup"><span data-stu-id="1c869-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="1c869-106">V tomto tématu se dozvíte, jak vytvořit jednoduchou ukázku, která tento postup znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="1c869-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="1c869-107">Definování kontraktu služby ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="1c869-107">Define the REST-style service contract</span></span>

<span data-ttu-id="1c869-108">Definice jednoduchého kontraktu služby ve stylu REST:</span><span class="sxs-lookup"><span data-stu-id="1c869-108">Define a simple  REST-style service contract:</span></span>

```csharp
[ServiceContract]
public interface IRestInterface
{
    [OperationContract, WebGet]
    int Add(int x, int y);

    [OperationContract, WebGet]
    string Echo(string input);
}
```

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="1c869-109">Implementace kontraktu služby ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="1c869-109">Implement the REST-style service contract</span></span>

<span data-ttu-id="1c869-110">Implementace kontraktu služby ve stylu REST:</span><span class="sxs-lookup"><span data-stu-id="1c869-110">Implement the REST-style service contract:</span></span>

```csharp
public class RestService : IRestInterface
{
    public int Add(int x, int y)
    {
        return x + y;
    }

    public string Echo(string input)
    {
        return input;
    }
}
```

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="1c869-111">Definování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="1c869-111">Define the WCF service contract</span></span>

<span data-ttu-id="1c869-112">Definujte kontrakt služby WCF, který bude použit pro volání služby ve stylu REST:</span><span class="sxs-lookup"><span data-stu-id="1c869-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

```csharp
[ServiceContract]
public interface INormalInterface
{
    [OperationContract]
    int CallAdd(int x, int y);

    [OperationContract]
    string CallEcho(string input);
}
```

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="1c869-113">Implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="1c869-113">Implement the WCF service contract</span></span>

<span data-ttu-id="1c869-114">Implementace kontraktu služby WCF:</span><span class="sxs-lookup"><span data-stu-id="1c869-114">Implement the WCF service contract:</span></span>

```csharp
public class NormalService : INormalInterface
{
    static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
    public int CallAdd(int x, int y)
    {
        return client.Add(x, y);
    }

    public string CallEcho(string input)
    {
        return client.Echo(input);
    }
}
```

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="1c869-115">Vytvoření klientského proxy serveru pro službu ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="1c869-115">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="1c869-116">Použití <xref:System.ServiceModel.ClientBase%601> k implementaci klientského proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="1c869-116">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="1c869-117">Pro každou metodu, která je volána, <xref:System.ServiceModel.OperationContextScope> je vytvořena nová a slouží k volání operace.</span><span class="sxs-lookup"><span data-stu-id="1c869-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

```csharp
public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
{
    public MyRestClient(string address)
        : base(new WebHttpBinding(), new EndpointAddress(address))
    {
        this.Endpoint.Behaviors.Add(new WebHttpBehavior());
    }

    public int Add(int x, int y)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Add(x, y);
        }
    }

    public string Echo(string input)
    {
        using (new OperationContextScope(this.InnerChannel))
        {
            return base.Channel.Echo(input);
        }
    }
}
```

## <a name="host-and-call-the-services"></a><span data-ttu-id="1c869-118">Hostování a volání služeb</span><span class="sxs-lookup"><span data-stu-id="1c869-118">Host and call the services</span></span>

<span data-ttu-id="1c869-119">Hostování obou služeb v konzolové aplikaci přidáním potřebných koncových bodů a chování.</span><span class="sxs-lookup"><span data-stu-id="1c869-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="1c869-120">A pak zavolejte běžnou službu WCF:</span><span class="sxs-lookup"><span data-stu-id="1c869-120">And then call the regular WCF service:</span></span>

```csharp
public static void Main()
{
    ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
    restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
    restHost.Open();

    ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
    normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
    normalHost.Open();

    Console.WriteLine("Hosts opened");

    ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
    INormalInterface proxy = factory.CreateChannel();

    Console.WriteLine(proxy.CallAdd(123, 456));
    Console.WriteLine(proxy.CallEcho("Hello world"));
}
```

## <a name="complete-code-listing"></a><span data-ttu-id="1c869-121">Úplný výpis kódu</span><span class="sxs-lookup"><span data-stu-id="1c869-121">Complete code listing</span></span>

<span data-ttu-id="1c869-122">Následuje úplný seznam ukázek implementovaných v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="1c869-122">The following is a complete listing of the sample implemented in this topic:</span></span>

```csharp
public class CallingRESTSample
{
    static readonly string RestServiceBaseAddress = "http://" + Environment.MachineName + ":8008/Service";
    static readonly string NormalServiceBaseAddress = "http://" + Environment.MachineName + ":8000/Service";

    [ServiceContract]
    public interface IRestInterface
    {
        [OperationContract, WebGet]
        int Add(int x, int y);
        [OperationContract, WebGet]
        string Echo(string input);
    }

    [ServiceContract]
    public interface INormalInterface
    {
        [OperationContract]
        int CallAdd(int x, int y);
        [OperationContract]
        string CallEcho(string input);
    }

    public class RestService : IRestInterface
    {
        public int Add(int x, int y)
        {
            return x + y;
        }

        public string Echo(string input)
        {
            return input;
        }
    }

    public class MyRestClient : ClientBase<IRestInterface>, IRestInterface
    {
        public MyRestClient(string address)
            : base(new WebHttpBinding(), new EndpointAddress(address))
        {
            this.Endpoint.Behaviors.Add(new WebHttpBehavior());
        }

        public int Add(int x, int y)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Add(x, y);
            }
        }

        public string Echo(string input)
        {
            using (new OperationContextScope(this.InnerChannel))
            {
                return base.Channel.Echo(input);
            }
        }
    }

    public class NormalService : INormalInterface
    {
        static MyRestClient client = new MyRestClient(RestServiceBaseAddress);
        public int CallAdd(int x, int y)
        {
            return client.Add(x, y);
        }

        public string CallEcho(string input)
        {
            return client.Echo(input);
        }
    }

    public static void Main()
    {
        ServiceHost restHost = new ServiceHost(typeof(RestService), new Uri(RestServiceBaseAddress));
        restHost.AddServiceEndpoint(typeof(IRestInterface), new WebHttpBinding(), "").Behaviors.Add(new WebHttpBehavior());
        restHost.Open();

        ServiceHost normalHost = new ServiceHost(typeof(NormalService), new Uri(NormalServiceBaseAddress));
        normalHost.AddServiceEndpoint(typeof(INormalInterface), new BasicHttpBinding(), "");
        normalHost.Open();

        Console.WriteLine("Hosts opened");

        ChannelFactory<INormalInterface> factory = new ChannelFactory<INormalInterface>(new BasicHttpBinding(), new EndpointAddress(NormalServiceBaseAddress));
        INormalInterface proxy = factory.CreateChannel();

        Console.WriteLine(proxy.CallAdd(123, 456));
        Console.WriteLine(proxy.CallEcho("Hello world"));
    }
}
```

## <a name="see-also"></a><span data-ttu-id="1c869-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="1c869-123">See also</span></span>

- [<span data-ttu-id="1c869-124">Postupy: Vytvoření základní webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="1c869-124">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="1c869-125">Programovací objektový model WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="1c869-125">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
