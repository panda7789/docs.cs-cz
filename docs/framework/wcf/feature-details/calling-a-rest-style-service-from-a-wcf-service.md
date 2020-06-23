---
title: Volání služby typu REST ze služby WCF
description: Naučte se, jak vytvořit službu WCF pomocí správného kontextu se službou ve stylu REST vytvořením oboru a voláním služby ve stylu REST z tohoto oboru.
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: 15f468923cf55feb85e7aeca1a2cc5e38050d665
ms.sourcegitcommit: 358a28048f36a8dca39a9fe6e6ac1f1913acadd5
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 06/23/2020
ms.locfileid: "85245294"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="b1b9e-103">Volání služby typu REST ze služby WCF</span><span class="sxs-lookup"><span data-stu-id="b1b9e-103">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="b1b9e-104">Při volání služby ve stylu REST z běžné (založené na protokolu SOAP) služby WCF kontext operace v metodě služby (která obsahuje informace o příchozím požadavku) přepíše kontext, který by měl být použit odchozím požadavkem.</span><span class="sxs-lookup"><span data-stu-id="b1b9e-104">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="b1b9e-105">To způsobí, že požadavky HTTP GET změní na požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="b1b9e-105">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="b1b9e-106">Chcete-li vynutit, aby služba WCF používala správný kontext pro volání služby ve stylu REST, vytvořte novou <xref:System.ServiceModel.OperationContextScope> a zavolejte službu ve stylu REST v rámci oboru kontextu operace.</span><span class="sxs-lookup"><span data-stu-id="b1b9e-106">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="b1b9e-107">V tomto tématu se dozvíte, jak vytvořit jednoduchou ukázku, která tento postup znázorňuje.</span><span class="sxs-lookup"><span data-stu-id="b1b9e-107">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="b1b9e-108">Definování kontraktu služby ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="b1b9e-108">Define the REST-style service contract</span></span>

<span data-ttu-id="b1b9e-109">Definice jednoduchého kontraktu služby ve stylu REST:</span><span class="sxs-lookup"><span data-stu-id="b1b9e-109">Define a simple  REST-style service contract:</span></span>

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

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="b1b9e-110">Implementace kontraktu služby ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="b1b9e-110">Implement the REST-style service contract</span></span>

<span data-ttu-id="b1b9e-111">Implementace kontraktu služby ve stylu REST:</span><span class="sxs-lookup"><span data-stu-id="b1b9e-111">Implement the REST-style service contract:</span></span>

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

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="b1b9e-112">Definování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="b1b9e-112">Define the WCF service contract</span></span>

<span data-ttu-id="b1b9e-113">Definujte kontrakt služby WCF, který bude použit pro volání služby ve stylu REST:</span><span class="sxs-lookup"><span data-stu-id="b1b9e-113">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

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

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="b1b9e-114">Implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="b1b9e-114">Implement the WCF service contract</span></span>

<span data-ttu-id="b1b9e-115">Implementace kontraktu služby WCF:</span><span class="sxs-lookup"><span data-stu-id="b1b9e-115">Implement the WCF service contract:</span></span>

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

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="b1b9e-116">Vytvoření klientského proxy serveru pro službu ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="b1b9e-116">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="b1b9e-117">Použití <xref:System.ServiceModel.ClientBase%601> k implementaci klientského proxy serveru.</span><span class="sxs-lookup"><span data-stu-id="b1b9e-117">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="b1b9e-118">Pro každou metodu, která je volána, <xref:System.ServiceModel.OperationContextScope> je vytvořena nová a slouží k volání operace.</span><span class="sxs-lookup"><span data-stu-id="b1b9e-118">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

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

## <a name="host-and-call-the-services"></a><span data-ttu-id="b1b9e-119">Hostování a volání služeb</span><span class="sxs-lookup"><span data-stu-id="b1b9e-119">Host and call the services</span></span>

<span data-ttu-id="b1b9e-120">Hostování obou služeb v konzolové aplikaci přidáním potřebných koncových bodů a chování.</span><span class="sxs-lookup"><span data-stu-id="b1b9e-120">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="b1b9e-121">A pak zavolejte běžnou službu WCF:</span><span class="sxs-lookup"><span data-stu-id="b1b9e-121">And then call the regular WCF service:</span></span>

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

## <a name="complete-code-listing"></a><span data-ttu-id="b1b9e-122">Úplný výpis kódu</span><span class="sxs-lookup"><span data-stu-id="b1b9e-122">Complete code listing</span></span>

<span data-ttu-id="b1b9e-123">Následuje úplný seznam ukázek implementovaných v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="b1b9e-123">The following is a complete listing of the sample implemented in this topic:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="b1b9e-124">Viz také</span><span class="sxs-lookup"><span data-stu-id="b1b9e-124">See also</span></span>

- [<span data-ttu-id="b1b9e-125">Postupy: Vytvoření základní webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="b1b9e-125">How to: Create a Basic WCF Web HTTP Service</span></span>](how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="b1b9e-126">Programovací objektový model WCF Web HTTP</span><span class="sxs-lookup"><span data-stu-id="b1b9e-126">WCF Web HTTP Programming Object Model</span></span>](wcf-web-http-programming-object-model.md)
