---
title: Volání služby typu REST ze služby WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: c2a3467fb5fe28194dcb8ee7715353f4cb6a1bff
ms.sourcegitcommit: 69bf8b719d4c289eec7b45336d0b933dd7927841
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 03/14/2019
ms.locfileid: "57842928"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="cbbc8-102">Volání služby typu REST ze služby WCF</span><span class="sxs-lookup"><span data-stu-id="cbbc8-102">Calling a REST-style service from a WCF service</span></span>

<span data-ttu-id="cbbc8-103">Při volání služby typu REST – vizuální styl od pravidelných služby WCF (založený na protokolu SOAP), přepíše kontext operace na metodu služby (který obsahuje informace o příchozího požadavku) kontext, který by měly být používány odchozí požadavek.</span><span class="sxs-lookup"><span data-stu-id="cbbc8-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="cbbc8-104">To způsobí, že požadavky HTTP GET, chcete-li změnit na požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="cbbc8-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="cbbc8-105">Chcete-li vynutit služby WCF ve správném kontextu použít pro volání služby REST – vizuální styl, vytvořte nový <xref:System.ServiceModel.OperationContextScope> a volání služby REST – vizuální styl od uvnitř oboru kontextu operace.</span><span class="sxs-lookup"><span data-stu-id="cbbc8-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="cbbc8-106">Toto téma popisuje, jak vytvořit jednoduchý příklad, který znázorňuje tento postup.</span><span class="sxs-lookup"><span data-stu-id="cbbc8-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>

## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="cbbc8-107">Definování kontraktu služby ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="cbbc8-107">Define the REST-style service contract</span></span>

<span data-ttu-id="cbbc8-108">Definování kontraktu služby jednoduchého stylu REST:</span><span class="sxs-lookup"><span data-stu-id="cbbc8-108">Define a simple  REST-style service contract:</span></span>

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

## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="cbbc8-109">Implementace kontraktu služby ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="cbbc8-109">Implement the REST-style service contract</span></span>

<span data-ttu-id="cbbc8-110">Implementace kontraktu služby ve stylu REST:</span><span class="sxs-lookup"><span data-stu-id="cbbc8-110">Implement the REST-style service contract:</span></span>

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

## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="cbbc8-111">Definování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="cbbc8-111">Define the WCF service contract</span></span>

<span data-ttu-id="cbbc8-112">Definování kontraktu služby WCF, který se použije k vyvolání služby REST-style:</span><span class="sxs-lookup"><span data-stu-id="cbbc8-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>

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

## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="cbbc8-113">Implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="cbbc8-113">Implement the WCF service contract</span></span>

<span data-ttu-id="cbbc8-114">Implementace kontraktu služby WCF:</span><span class="sxs-lookup"><span data-stu-id="cbbc8-114">Implement the WCF service contract:</span></span>

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

## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="cbbc8-115">Vytvořit proxy klienta pro službu REST-style.</span><span class="sxs-lookup"><span data-stu-id="cbbc8-115">Create the client proxy for the REST-style service</span></span>

<span data-ttu-id="cbbc8-116">Pomocí <xref:System.ServiceModel.ClientBase%601> implementace proxy serveru klienta.</span><span class="sxs-lookup"><span data-stu-id="cbbc8-116">Using <xref:System.ServiceModel.ClientBase%601> to implement the client proxy.</span></span> <span data-ttu-id="cbbc8-117">Pro každou metodu s názvem, nová <xref:System.ServiceModel.OperationContextScope> se vytvoří a použít k volání operace.</span><span class="sxs-lookup"><span data-stu-id="cbbc8-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>

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

## <a name="host-and-call-the-services"></a><span data-ttu-id="cbbc8-118">Hostování a volání služeb</span><span class="sxs-lookup"><span data-stu-id="cbbc8-118">Host and call the services</span></span>

<span data-ttu-id="cbbc8-119">Hostitelem obou služeb v konzolové aplikaci, přidání koncových bodů potřebné a chování.</span><span class="sxs-lookup"><span data-stu-id="cbbc8-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="cbbc8-120">A pak vyvolejte regulární služby WCF:</span><span class="sxs-lookup"><span data-stu-id="cbbc8-120">And then call the regular WCF service:</span></span>

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

## <a name="complete-code-listing"></a><span data-ttu-id="cbbc8-121">Úplný výpis kódu</span><span class="sxs-lookup"><span data-stu-id="cbbc8-121">Complete code listing</span></span>

<span data-ttu-id="cbbc8-122">Následuje úplný ukázkový implementované v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="cbbc8-122">The following is a complete listing of the sample implemented in this topic:</span></span>

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

## <a name="see-also"></a><span data-ttu-id="cbbc8-123">Viz také:</span><span class="sxs-lookup"><span data-stu-id="cbbc8-123">See also</span></span>

- [<span data-ttu-id="cbbc8-124">Postupy: Vytvoření základní webové HTTP služby WCF</span><span class="sxs-lookup"><span data-stu-id="cbbc8-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)
- [<span data-ttu-id="cbbc8-125">Programovací objektový model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="cbbc8-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
