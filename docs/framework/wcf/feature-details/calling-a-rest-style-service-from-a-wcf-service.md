---
title: Volání služby typu REST ze služby WCF
ms.date: 03/30/2017
ms.assetid: 77df81d8-7f53-4daf-8d2d-bf7996e94d5a
ms.openlocfilehash: 8f520b1f77b9ca41b9fd2b8d51c1b935ab1e0a87
ms.sourcegitcommit: 3d5d33f384eeba41b2dff79d096f47ccc8d8f03d
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 05/04/2018
ms.locfileid: "33488508"
---
# <a name="calling-a-rest-style-service-from-a-wcf-service"></a><span data-ttu-id="76cfe-102">Volání služby typu REST ze služby WCF</span><span class="sxs-lookup"><span data-stu-id="76cfe-102">Calling a REST-style service from a WCF service</span></span>
<span data-ttu-id="76cfe-103">Při volání z regulární služby WCF (založený na protokolu SOAP) služby ve stylu REST, přepíše kontext operaci na metodě služby (která obsahuje informace o příchozího požadavku) kontext, který má být používána odchozího požadavku.</span><span class="sxs-lookup"><span data-stu-id="76cfe-103">When calling a REST-style service from a regular (SOAP-based) WCF service, the operation context on the service method (which contains information about the incoming request) overrides the context which should be used by the outgoing request.</span></span> <span data-ttu-id="76cfe-104">To způsobí, že metody GET protokolu HTTP žádosti o změnu na požadavky HTTP POST.</span><span class="sxs-lookup"><span data-stu-id="76cfe-104">This causes HTTP GET requests to change to HTTP POST requests.</span></span> <span data-ttu-id="76cfe-105">Chcete-li vynutit službu WCF na používání správné kontextu pro volání služby stylu REST, vytvořte novou <xref:System.ServiceModel.OperationContextScope> a volání služby stylu REST z uvnitř oblasti kontextu operace.</span><span class="sxs-lookup"><span data-stu-id="76cfe-105">To force the WCF service to use the right context for calling the REST-style service, create a new <xref:System.ServiceModel.OperationContextScope> and call the REST-style service from inside the operation context scope.</span></span> <span data-ttu-id="76cfe-106">Toto téma popisuje, jak k vytvoření jednoduchý příklad, který tento postup ukazuje.</span><span class="sxs-lookup"><span data-stu-id="76cfe-106">This topic will describe how to create a simple sample that illustrates this technique.</span></span>  
  
## <a name="define-the-rest-style-service-contract"></a><span data-ttu-id="76cfe-107">Definování kontraktu služby ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="76cfe-107">Define the REST-style service contract</span></span>  
 <span data-ttu-id="76cfe-108">Definování kontraktu služby jednoduché stylu REST:</span><span class="sxs-lookup"><span data-stu-id="76cfe-108">Define a simple  REST-style service contract:</span></span>  
  
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
  
## <a name="implement-the-rest-style-service-contract"></a><span data-ttu-id="76cfe-109">Implementace kontraktu služby ve stylu REST</span><span class="sxs-lookup"><span data-stu-id="76cfe-109">Implement the REST-style service contract</span></span>  
 <span data-ttu-id="76cfe-110">Implementace kontraktu služby ve stylu REST:</span><span class="sxs-lookup"><span data-stu-id="76cfe-110">Implement the REST-style service contract:</span></span>  
  
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
  
## <a name="define-the-wcf-service-contract"></a><span data-ttu-id="76cfe-111">Definování kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="76cfe-111">Define the WCF service contract</span></span>  
 <span data-ttu-id="76cfe-112">Definování kontraktu služby WCF, který se použije k volání služby stylu REST:</span><span class="sxs-lookup"><span data-stu-id="76cfe-112">Define a WCF service contract  that will be used to call the REST-style service:</span></span>  
  
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
  
## <a name="implement-the-wcf-service-contract"></a><span data-ttu-id="76cfe-113">Implementace kontraktu služby WCF</span><span class="sxs-lookup"><span data-stu-id="76cfe-113">Implement the WCF service contract</span></span>  
 <span data-ttu-id="76cfe-114">Implementace kontraktu služby WCF:</span><span class="sxs-lookup"><span data-stu-id="76cfe-114">Implement the WCF service contract:</span></span>  
  
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
  
## <a name="create-the-client-proxy-for-the-rest-style-service"></a><span data-ttu-id="76cfe-115">Vytvořit proxy klienta pro službu stylu REST</span><span class="sxs-lookup"><span data-stu-id="76cfe-115">Create the client proxy for the REST-style service</span></span>  
 <span data-ttu-id="76cfe-116">Pomocí <!--zz<xref:System.ServiceModel.ClientBase%60>--> `System.ServiceModel.ClientBase` implementace proxy klienta.</span><span class="sxs-lookup"><span data-stu-id="76cfe-116">Using <!--zz<xref:System.ServiceModel.ClientBase%60>--> `System.ServiceModel.ClientBase` implement the client proxy.</span></span> <span data-ttu-id="76cfe-117">Pro každou metodu s názvem, nový <xref:System.ServiceModel.OperationContextScope> se vytvoří a používá k volání operace.</span><span class="sxs-lookup"><span data-stu-id="76cfe-117">For each method called, a new <xref:System.ServiceModel.OperationContextScope> is created and used to call the operation.</span></span>  
  
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
  
## <a name="host-and-call-the-services"></a><span data-ttu-id="76cfe-118">Hostování a volání služeb</span><span class="sxs-lookup"><span data-stu-id="76cfe-118">Host and call the services</span></span>  
 <span data-ttu-id="76cfe-119">Hostitel obě služby v aplikaci konzoly, přidání potřebné koncových bodů a chování.</span><span class="sxs-lookup"><span data-stu-id="76cfe-119">Host both services in a console app, adding the needed endpoints and behaviors.</span></span> <span data-ttu-id="76cfe-120">A pak zavolají regulární služby WCF:</span><span class="sxs-lookup"><span data-stu-id="76cfe-120">And then call the regular WCF service:</span></span>  
  
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
  
## <a name="complete-code-listing"></a><span data-ttu-id="76cfe-121">Výpis úplného kódu</span><span class="sxs-lookup"><span data-stu-id="76cfe-121">Complete code listing</span></span>  
 <span data-ttu-id="76cfe-122">Níže uvádíme úplný seznam všech ukázka implementované v tomto tématu:</span><span class="sxs-lookup"><span data-stu-id="76cfe-122">The following is a complete listing of the sample implemented in this topic:</span></span>  
  
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
  
## <a name="see-also"></a><span data-ttu-id="76cfe-123">Viz také</span><span class="sxs-lookup"><span data-stu-id="76cfe-123">See Also</span></span>  
 [<span data-ttu-id="76cfe-124">Postupy: Vytvoření základní webové služby HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="76cfe-124">How to: Create a Basic WCF Web HTTP Service</span></span>](../../../../docs/framework/wcf/feature-details/how-to-create-a-basic-wcf-web-http-service.md)  
 [<span data-ttu-id="76cfe-125">Programovací objektový model webových služeb HTTP WCF</span><span class="sxs-lookup"><span data-stu-id="76cfe-125">WCF Web HTTP Programming Object Model</span></span>](../../../../docs/framework/wcf/feature-details/wcf-web-http-programming-object-model.md)
