---
title: Korelace trvanlivého duplexního přenosu
ms.date: 03/30/2017
ms.assetid: 8eb0e49a-6d3b-4f7e-a054-0d4febee2ffb
ms.openlocfilehash: f2f5fe557f1f8754758d0dd9b4042cacc62cc61f
ms.sourcegitcommit: 9b552addadfb57fab0b9e7852ed4f1f1b8a42f8e
ms.translationtype: MT
ms.contentlocale: cs-CZ
ms.lasthandoff: 04/23/2019
ms.locfileid: "61856596"
---
# <a name="durable-duplex-correlation"></a><span data-ttu-id="d6d04-102">Korelace trvanlivého duplexního přenosu</span><span class="sxs-lookup"><span data-stu-id="d6d04-102">Durable Duplex Correlation</span></span>
<span data-ttu-id="d6d04-103">Korelace trvanlivého duplexního přenosu, označované také jako zpětné volání korelace, je užitečné, když služba pracovního postupu má požadavek na odeslání zpětné volání počáteční volajícímu.</span><span class="sxs-lookup"><span data-stu-id="d6d04-103">Durable duplex correlation, also known as callback correlation, is useful when a workflow service has a requirement to send a callback to the initial caller.</span></span> <span data-ttu-id="d6d04-104">Na rozdíl od WCF duplexní zpětného volání v každém okamžiku v budoucnu se může stát a není vázaný na jeden kanál nebo kanál životnost; Jediným požadavkem je, že volající mít aktivní koncový bod naslouchání pro zpětné volání zprávy.</span><span class="sxs-lookup"><span data-stu-id="d6d04-104">Unlike WCF duplex, the callback can happen at any time in the future and is not tied to the same channel or the channel lifetime; the only requirement is that the caller have an active endpoint listening for the callback message.</span></span> <span data-ttu-id="d6d04-105">To umožňuje dvě služby pracovního postupu pro komunikaci v rámci dlouhotrvající konverzace.</span><span class="sxs-lookup"><span data-stu-id="d6d04-105">This allows two workflow services to communicate in a long-running conversation.</span></span> <span data-ttu-id="d6d04-106">Toto téma obsahuje přehled korelace trvanlivého duplexního přenosu.</span><span class="sxs-lookup"><span data-stu-id="d6d04-106">This topic provides an overview of durable duplex correlation.</span></span>  
  
## <a name="using-durable-duplex-correlation"></a><span data-ttu-id="d6d04-107">Pomocí korelace trvanlivého duplexního přenosu</span><span class="sxs-lookup"><span data-stu-id="d6d04-107">Using Durable Duplex Correlation</span></span>  
 <span data-ttu-id="d6d04-108">Korelace trvanlivého duplexního přenosu, tyto dvě služby vyžaduje použití vazbu povolen kontext, která podporuje obousměrné operace, jako například <xref:System.ServiceModel.NetTcpContextBinding> nebo <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="d6d04-108">To use durable duplex correlation, the two services must use a context-enabled binding that supports two-way operations, such as <xref:System.ServiceModel.NetTcpContextBinding> or <xref:System.ServiceModel.WSHttpContextBinding>.</span></span> <span data-ttu-id="d6d04-109">Volání služby registrů <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> požadované vazby v klientovi <xref:System.ServiceModel.Endpoint>.</span><span class="sxs-lookup"><span data-stu-id="d6d04-109">The calling service registers a <xref:System.ServiceModel.WSHttpContextBinding.ClientCallbackAddress%2A> with the desired binding on their client <xref:System.ServiceModel.Endpoint>.</span></span> <span data-ttu-id="d6d04-110">Přijímající služba obdrží tato data v počáteční volání a pak pomocí něj sama o sobě <xref:System.ServiceModel.Endpoint> v <xref:System.ServiceModel.Activities.Send> aktivitu, která provádí volání zpět do volání služby.</span><span class="sxs-lookup"><span data-stu-id="d6d04-110">The receiving service receives this data in the initial call and then uses it on its own <xref:System.ServiceModel.Endpoint> in the <xref:System.ServiceModel.Activities.Send> activity that makes the call back to the calling service.</span></span> <span data-ttu-id="d6d04-111">V tomto příkladu dvě služby vzájemně komunikují.</span><span class="sxs-lookup"><span data-stu-id="d6d04-111">In this example, two services communicate with each other.</span></span> <span data-ttu-id="d6d04-112">První služba volá metodu na druhý služby a poté počká na odpověď.</span><span class="sxs-lookup"><span data-stu-id="d6d04-112">The first service invokes a method on the second service and then waits for a reply.</span></span> <span data-ttu-id="d6d04-113">Druhá služba ví název metody zpětného volání, ale koncový bod služby, která implementuje tuto metodu není znám v době návrhu.</span><span class="sxs-lookup"><span data-stu-id="d6d04-113">The second service knows the name of the callback method, but the endpoint of the service that implements this method is not known at design time.</span></span>  
  
> [!NOTE]
> <span data-ttu-id="d6d04-114">Trvanlivý duplexní přenos může obsahovat jenom nepoužívá, pokud <xref:System.ServiceModel.Channels.AddressingVersion> koncového bodu má nakonfigurovanou <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span><span class="sxs-lookup"><span data-stu-id="d6d04-114">Durable duplex can only be used when the <xref:System.ServiceModel.Channels.AddressingVersion> of the endpoint is configured with <xref:System.ServiceModel.Channels.AddressingVersion.WSAddressing10%2A>.</span></span> <span data-ttu-id="d6d04-115">Pokud ne, pak <xref:System.InvalidOperationException> je vyvolána výjimka s následující zprávou: "Zpráva obsahuje hlavičku kontextu zpětného volání s odkazem na koncový bod pro [verze AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span><span class="sxs-lookup"><span data-stu-id="d6d04-115">If it is not, then an <xref:System.InvalidOperationException> exception is thrown with the following message: "The message contains a callback context header with an endpoint reference for [AddressingVersion](http://schemas.xmlsoap.org/ws/2004/08/addressing).</span></span> <span data-ttu-id="d6d04-116">Kontext zpětného volání lze přenášet pouze, pokud verze AddressingVersion konfigurována s "Třídy WSAddressing10".</span><span class="sxs-lookup"><span data-stu-id="d6d04-116">Callback context can only be transmitted when the AddressingVersion is configured with 'WSAddressing10'.</span></span>
  
 <span data-ttu-id="d6d04-117">V následujícím příkladu je hostované služby pracovního postupu, který vytvoří zpětné volání <xref:System.ServiceModel.Endpoint> pomocí <xref:System.ServiceModel.WSHttpContextBinding>.</span><span class="sxs-lookup"><span data-stu-id="d6d04-117">In the following example, a workflow service is hosted that creates a callback <xref:System.ServiceModel.Endpoint> using <xref:System.ServiceModel.WSHttpContextBinding>.</span></span>  
  
```csharp  
// Host WF Service 1.  
string baseAddress1 = "http://localhost:8080/Service1";  
WorkflowServiceHost host1 = new WorkflowServiceHost(GetWF1(), new Uri(baseAddress1));  
  
// Add the callback endpoint.  
WSHttpContextBinding Binding1 = new WSHttpContextBinding();  
host1.AddServiceEndpoint("ICallbackItemsReady", Binding1, "ItemsReady");  
  
// Add the service endpoint.  
host1.AddServiceEndpoint("IService1", Binding1, baseAddress1);  
  
// Open the first workflow service.  
host1.Open();  
Console.WriteLine("Service1 waiting at: {0}", baseAddress1);  
```  
  
 <span data-ttu-id="d6d04-118">Pracovní postup, který implementuje tato služba pracovního postupu inicializuje korelaci zpětného volání s jeho <xref:System.ServiceModel.Activities.Send> aktivitu a odkazuje na tento koncový bod zpětného volání z <xref:System.ServiceModel.Activities.Receive> aktivitu, která koreluje s <xref:System.ServiceModel.Activities.Send>.</span><span class="sxs-lookup"><span data-stu-id="d6d04-118">The workflow that implements this workflow service initializes the callback correlation with its <xref:System.ServiceModel.Activities.Send> activity, and references this callback endpoint from the <xref:System.ServiceModel.Activities.Receive> activity that correlates with the <xref:System.ServiceModel.Activities.Send>.</span></span> <span data-ttu-id="d6d04-119">Následující příklad představuje pracovní postup, který je vrácen z `GetWF1` metody.</span><span class="sxs-lookup"><span data-stu-id="d6d04-119">The following example represents the workflow that is returned from the `GetWF1` method.</span></span>  
  
```csharp  
Variable<CorrelationHandle> CallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartOrder = new Receive  
{  
    CanCreateInstance = true,  
    ServiceContractName = "IService1",  
    OperationName = "StartOrder"  
};  
  
Send GetItems = new Send  
{  
    CorrelationInitializers =   
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = CallbackHandle  
        }  
    },  
    ServiceContractName = "IService2",  
    OperationName = "StartItems",  
    Endpoint = new Endpoint  
    {  
        AddressUri = new Uri("http://localhost:8081/Service2"),  
        Binding = new WSHttpContextBinding  
        {  
            ClientCallbackAddress = new Uri("http://localhost:8080/Service1/ItemsReady")                          
        }  
    }  
};  
  
Receive ItemsReady = new Receive  
{  
    ServiceContractName = "ICallbackItemsReady",  
    OperationName = "ItemsReady",  
    CorrelatesWith = CallbackHandle,  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        CallbackHandle  
    },  
    Activities =  
    {  
        StartOrder,  
        new WriteLine  
        {  
            Text = "WF1 - Started"  
        },  
        GetItems,  
        new WriteLine  
        {  
            Text = "WF1 - Request Submitted"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF1 - Items Received"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="d6d04-120">Druhá služba pracovního postupu je hostované pomocí poskytnuté systémem, na základě kontextu vazby.</span><span class="sxs-lookup"><span data-stu-id="d6d04-120">The second workflow service is hosted using a system-provided, context-based binding.</span></span>  
  
```csharp  
// Host WF Service 2.  
string baseAddress2 = "http://localhost:8081/Service2";  
WorkflowServiceHost host2 = new WorkflowServiceHost(GetWF2(), new Uri(baseAddress2));  
  
// Add the service endpoint.  
WSHttpContextBinding Binding2 = new WSHttpContextBinding();  
host2.AddServiceEndpoint("IService2", Binding2, baseAddress2);  
  
// Open the second workflow service.  
host2.Open();  
Console.WriteLine("Service2 waiting at: {0}", baseAddress2);  
```  
  
 <span data-ttu-id="d6d04-121">Pracovní postup, který implementuje tato služba pracovního postupu začíná <xref:System.ServiceModel.Activities.Receive> aktivity.</span><span class="sxs-lookup"><span data-stu-id="d6d04-121">The workflow that implements this workflow service begins with a <xref:System.ServiceModel.Activities.Receive> activity.</span></span> <span data-ttu-id="d6d04-122">To přijímat aktivity inicializuje korelaci zpětného volání pro tuto službu prodlevy pro určité době simulovat dlouhotrvající práci a poté zavolá zpět do první service pomocí kontextu zpětného volání, který byl předán při prvním volání do služby.</span><span class="sxs-lookup"><span data-stu-id="d6d04-122">This receive activity initializes the callback correlation for this service, delays for a period of time to simulate long-running work, and then calls back into the first service using the callback context that was passed in the first call into the service.</span></span> <span data-ttu-id="d6d04-123">Následující příklad představuje pracovní postup, který je vrácen z volání `GetWF2`.</span><span class="sxs-lookup"><span data-stu-id="d6d04-123">The following example represents the workflow that is returned from a call to `GetWF2`.</span></span> <span data-ttu-id="d6d04-124">Všimněte si, že <xref:System.ServiceModel.Activities.Send> adresu zástupný symbol má aktivita `http://www.contoso.com`; skutečná adresa používá za běhu je adresa zadaná zpětného volání.</span><span class="sxs-lookup"><span data-stu-id="d6d04-124">Note that the <xref:System.ServiceModel.Activities.Send> activity has a placeholder address of `http://www.contoso.com`; the actual address used at runtime is the supplied callback address.</span></span>  
  
```csharp  
Variable<CorrelationHandle> ItemsCallbackHandle = new Variable<CorrelationHandle>();  
  
Receive StartItems = new Receive  
{  
    CorrelationInitializers =   
    {  
        new CallbackCorrelationInitializer  
        {  
            CorrelationHandle = ItemsCallbackHandle  
        }  
    },  
    CanCreateInstance = true,  
    ServiceContractName = "IService2",  
    OperationName = "StartItems"  
};  
  
Send ItemsReady = new Send  
{  
    CorrelatesWith = ItemsCallbackHandle,  
    Endpoint = new Endpoint  
    {  
        // The callback address on the binding is used  
        // instead of this placeholder address.  
        AddressUri = new Uri("http://www.contoso.com"),  
  
        Binding = new WSHttpContextBinding()  
    },  
    OperationName = "ItemsReady",  
    ServiceContractName = "ICallbackItemsReady"  
};  
  
Activity wf = new Sequence  
{  
    Variables =  
    {  
        ItemsCallbackHandle  
    },  
    Activities =  
    {  
        StartItems,  
        new WriteLine  
        {  
            Text = "WF2 - Request Received"  
        },  
        new Delay  
        {  
            Duration = TimeSpan.FromMinutes(90)  
        },  
        new WriteLine  
        {  
            Text = "WF2 - Sending items"  
        },  
        ItemsReady,  
        new WriteLine  
        {  
            Text = "WF2 - Items sent"  
        }  
     }  
};  
```  
  
 <span data-ttu-id="d6d04-125">Když `StartOrder` metoda se vyvolá u prvního pracovního postupu, se zobrazí následující výstup, který znázorňuje tok spuštění prostřednictvím dvou pracovních postupů.</span><span class="sxs-lookup"><span data-stu-id="d6d04-125">When the `StartOrder` method is invoked on the first workflow, the following output is displayed, which shows the flow of execution through the two workflows.</span></span>  
  
```Output  
Service1 waiting at: http://localhost:8080/Service1  
Service2 waiting at: http://localhost:8081/Service2  
Press enter to exit.   
WF1 - Started  
WF2 - Request Received  
WF1 - Request Submitted  
WF2 - Sending items  
WF2 - Items sent  
WF1 - Items Received  
```  
  
 <span data-ttu-id="d6d04-126">V tomto příkladu obou pracovních postupů explicitně spravovat pomocí korelace <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span><span class="sxs-lookup"><span data-stu-id="d6d04-126">In this example, both workflows explicitly manage correlation using a <xref:System.ServiceModel.Activities.CallbackCorrelationInitializer>.</span></span> <span data-ttu-id="d6d04-127">Protože pouze jeden korelace v pracovních postupech tyto ukázky, výchozí <xref:System.ServiceModel.Activities.CorrelationHandle> správy by byl dostatečná.</span><span class="sxs-lookup"><span data-stu-id="d6d04-127">Because there was only a single correlation in these sample workflows, the default <xref:System.ServiceModel.Activities.CorrelationHandle> management would have been sufficient.</span></span>
